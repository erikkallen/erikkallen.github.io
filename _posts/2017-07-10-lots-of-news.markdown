---
title: Lots of news
date: 2017-07-10 22:42:00 Z
categories:
- 3d printing
- company
tags:
- 3d printer
- evabits
image: images/pi-dsi-lcd.jpg
---

Where do I start, it has been a while so naturally I finally have a lot to say :D. So first of; my Mendel90 finally got his well deserved paint job, and some needed wiring cleanup. Also while I was doing that I slapped in some new electronics (well new for me as it's the old but well tested RAMPS 1.4 Arduino combination).

![Mendel90 Paintjob](images/mendel90_paintjob.jpg)

Since we are still on the subject of electronics and one of my colleagues pointed me to [Pcbway](http://www.pcbway.com) (a cheap fab house) which sells you 10 prints for 5 bucks I decided to attempt to make my own PCB. So I fired up [KiCad](http://kicad-pcb.org) and started designing a PCB that fits snugly into the tiny space reserved for a connector board on my Mendel90 hotend carriage. 10 days later I was a proud owner of my very own PCB and by some miracle I even fits the housing, unfortunately I read the ramps schematics wrong and I had to bodge wire the entire thing, but hey what would you expect from a software dude making a pcb :P. Anyhow the rev1 is up on my [Github](https://github.com/erikkallen/mendel90_connector_pcb) for anyone who happens to have the same Mendel90 as me :D or ambitions to have the same one (which ever is more likely).

![Mendel90 Hotend PCB](images/mendel90_hotend_pcb.png)

Continuing with colleagues... I started my own company together with two of my former colleagues, it's called EVAbits and we do....surprise surprise engineering :D so if you need some of that done head over to our [website](http://evabits.com).

![EVAbits](http://evabits.com/images/evabits.png)

Lastly I received a LCD display from my other job from an old discontinued product which I hooked up to a Raspberry Pi and IT WORKED! I had to use almost all GPIO pins though so I have to figure something out for connecting other peripherals. Ooh yea the reason I did this was for my car multimedia setup which I am building (very slowly but you know... some day it will be done). The LCD also had a touchscreen controller which I had to replace by an Arduino because I could not get it to work on my Raspberry Pi, anyway more details on the LCD in a different post.

![Pi LCD Hookup](images/pi-dsi-lcd.jpg)

So thats it for now, thanks for reading...if you made it this far that is :D
