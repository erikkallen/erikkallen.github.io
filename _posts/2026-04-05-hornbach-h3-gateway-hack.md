---
title: Hacking the SMART HOME by Hornbach Gateway
date: 2026-04-05 00:00:00 Z
categories:
- home automation
- hardware hacking
tags:
- linux
- uart
- allwinner
- home assistant
---

So I got my hands on a **SMART HOME by Hornbach** gateway (model WSR 1706 V1.0) — the little smart home hub Hornbach sells in their stores to control Z-Wave and Zigbee devices. Now I have nothing against Hornbach, but their cloud-dependent locked-down firmware is not really my thing, so naturally the first thought was: can I put Home Assistant on this? Turns out yes, probably, though it is still a work in progress :D.

The first thing I did was crack it open, and immediately spotted an Allwinner H3 SoC — the same quad-core ARM Cortex-A7 chip found in the Orange Pi and NanoPi NEO boards. At that point I knew this was going to be fun.

**UART: what is all this garbage?**

Any self respecting hardware hacker starts with UART, so I soldered up to the debug pads and was immediately greeted by a stream of what looked like complete nonsense:

{% highlight bash %}
#^UVlt%&+,-0123@BCDE[`bcfmpqy}-
{% endhighlight %}

My first thought was baud rate mismatch, but switching baud rates did not help. After some digging I found the real cause: the Allwinner H3 BROM and SPL output at **1.5 Mbaud** during the very early boot stage, before handing off to U-Boot which switches down to 115200. Most cheap USB-UART adapters simply cannot do 1.5M, so that early stage always looks like garbage. The fix is to just wait a few seconds — the clean 115200 output shows up once U-Boot takes over. If you want to actually decode that early output you need an FT232H or CP2102N (not the plain CP2102), but honestly waiting is fine.

One important gotcha: the H3 UART is 3.3V logic. A 5V adapter on the TX line can cause corruption or worse. For just listening it is usually tolerated, but for two-way communication you really want a proper 3.3V adapter — something I learned I need to order before I can go much further :D.

**Trying the network**

While waiting for the UART output to stabilise I also poked at the network side. The device shows up running OpenWrt, which was a nice surprise — but Hornbach has locked it down pretty hard. No LuCI, SSH is not on port 22, and nmap finds absolutely zero open ports. The device only talks outbound to Hornbach's cloud. So that is a dead end and UART is where the action is going to be.

**What is actually inside**

The board uses eMMC soldered directly — no SD card slot populated, which rules out the easy approach of just booting from an SD card. The Z-Wave and Zigbee radios are there, plus a USB-A host port and Ethernet, which is pretty much the standard H3 reference design feature set. Hornbach is a DIY chain, not a hardware company, so this is almost certainly built by an ODM around a NanoPi NEO or Orange Pi-style reference board.

The most interesting discovery came from looking at the PCB carefully: there is an **unpopulated button footprint** — the pads are right there but no button is soldered. This is almost certainly the FEL button. Allwinner puts a FEL recovery mode into the H3 BROM that cannot be disabled by vendors, and ODMs routinely just leave the button unpopulated on production hardware to stop end users from using it. Joke is on them :D.

**FEL mode to the rescue**

FEL is a low-level USB boot protocol burned into the Allwinner silicon. When active, the device shows up over USB as vendor `1f3a`, product `efe8`. You trigger it by holding the FEL button (or in our case, shorting those two pads) while powering on. One important detail: use a USB-A to USB-A cable with the **5V pin taped off** on at least one end — the device has its own power supply and you do not want to backfeed 5V through the USB port.

{% highlight bash %}
# Check the device appeared in FEL mode
lsusb | grep 1f3a

# Confirm with sunxi-tools
sudo sunxi-fel version
{% endhighlight %}

On Arch Linux, sunxi-tools is in the AUR:

{% highlight bash %}
yay -S sunxi-tools

# Udev rule so you don't need sudo every time
echo 'SUBSYSTEM=="usb", ATTR{idVendor}=="1f3a", ATTR{idProduct}=="efe8", MODE="0666"' \
  | sudo tee /etc/udev/rules.d/99-sunxi.rules
sudo udevadm control --reload-rules
{% endhighlight %}

**Flashing Home Assistant OS**

Once in FEL mode the plan is straightforward. First load a compatible U-Boot (NanoPi NEO or Orange Pi builds are good starting points) into RAM via FEL:

{% highlight bash %}
sunxi-fel uboot u-boot-sunxi-with-spl.bin
{% endhighlight %}

Then from within U-Boot or a minimal initramfs, write the Home Assistant OS image straight to the eMMC:

{% highlight bash %}
dd if=haos.img of=/dev/mmcblk0 bs=1M
{% endhighlight %}

Power cycle and it should boot straight into HAOS.

**Where things stand**

I have got the theory solid and the UART output decoded, but I have not yet physically shorted the FEL pads and confirmed it works — partly because my reliable 3.3V UART adapter is still in the post. Once it arrives I can do a proper two-way UART session, confirm U-Boot details, pick the right U-Boot build, and actually pull the trigger on the eMMC flash. Will post an update when that happens!
