---
layout: project
title: Wireless (Klik aan Klik uit) dimmer
date: 2015-10-20
---
I recently replaced the wall dimmer of my living room lighting with a wireless controlled version.
This is all very nice but the only way to control the dim factor is with a regular switch or remote.

The way to choose the dim factor is as follows:

* Turn on the dimmer
* Turn on the dimmer again the light will now fade from full bright to dim continuously.
* When you are happy with the brightness Turn on the dimmer once more to set the value.

After a bit of digging and wiring up an Arduino with a 433.92Mhz radio I found out that using the KaKu library you can actually send the desired dim value to the dimmer and so a project was born.

I still have 2 Arduino pro mini's lying around from a Sparkfun sale and decided to use those, as they have a solder jumper that can make them very power efficient.

So I started out by using a rotary encoder with an push button to basically mimmic the functionality of the existing dimmer controls. This worked quite well until I tried to used the Atmega's sleep mode. It turns out that the encoder uses to much power (probably due to the way I debounced the encoder).
