---
layout: post
title:  "Raspberry PI as Arduino network programmer"
date:   2014-05-22 23:04:11
categories: arduino Raspberry Pi programmer
---

This guide will show you how to program an Arduino connected to your Raspberry PI from  the Arduino IDE on your local computer.
Linux and OS X for now

###On your Raspberry PI

First install avrdude

    apt-get install avrdude

Install avrdude-rpi using the installation tips from https://github.com/deanmao/avrdude-rpi they boil down to this:

{% highlight bash %}
wget https://raw.githubusercontent.com/deanmao/avrdude-rpi/master/autoreset
wget https://raw.githubusercontent.com/deanmao/avrdude-rpi/master/avrdude-autoreset
sudo cp autoreset /usr/bin
sudo cp avrdude-autoreset /usr/bin
sudo mv /usr/bin/avrdude /usr/bin/avrdude-original
sudo ln -s /usr/bin/avrdude-autoreset /usr/bin/avrdude
{% endhighlight %}

Next open the file /usr/bin/autoreset and change the reset pin to the pin you connected the Arduino reset to.
The GPIO pin number corresponds to the number of the pin of the header.

    vim /usr/bin/autoreset

###On your computer

Download and install Arduino IDE
go to the folder containing avrdude
On OS X this most likely is /Applications/Arduino.app/Contents/Resources/Java/hardware/tools/avr/bin

    cd /Applications/Arduino.app/Contents/Resources/Java/hardware/tools/avr/bin
    mv avrdude avrdude-original
	wget https://gist.githubusercontent.com/erikkallen/11153072/raw/3e1cdfdef6aee12b9f0f47b50bc33849612f2a0d/avrdude
	chmod +x avrdude
