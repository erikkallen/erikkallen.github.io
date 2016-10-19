---
title: Home Automation with Home-assistant.io
date: 2016-04-28 00:00:00 Z
layout: project
description: With this project I want to make my house more awesome.
thumbnail: "/images/home_automation.png"
---

I finally decided to start using my Rasberry Pi for more than streaming my movie collection.
So after a quick search on the internet I found an awesome project called [Home assistant](http://home-assistant.io).

So I fired up a fresh install of raspbian (Jessie Lite) and installed python3 and home assistant.

After a few simple configuration edits the system was up and running and I could start to add components.
Since I was working on my lights using an arduino I thought it would be worth while to try hooking the 433MHz transmitter directly to my raspberry Pi. Having found the [Wiring Pi library](http://wiringpi.com/) this turned out to be a no brainer.

All I had to do was add some code to connect to my mosquitto server (also running on my Pi) and make sure it reacted to a ON and OFF command sent in a chosen topic

The source for my mqtt Klik Aan Klik Uit home-assistant plugin can be found [here](https://github.com/erikkallen/mqtt_lights)
