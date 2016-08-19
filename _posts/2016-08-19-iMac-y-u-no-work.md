---
layout: post
title:  "iMac why u no work?"
date:   2016-08-19 22:11:11
categories: iMac late 2012 emc BGA reballing
---

My iMac.... I am still a bit sad thinking about it, but never give up thats what I say.
After a bit of googling I found a service manual of my iMac, which stated that the LED's on the logic board should give you an idea of whats going on. Since none of my LED's lit up the guide stated that there might be something wrong with the power supply (that would make sense right?), so I give my Chinese friend Ali a quick look and 60 Euro's and 1 week later I have a replacement power supply.

First thing to do hook the thing up en plug everything in and... still no freeking LED that lights up. Bummer, it wasn't the power supply.

Moving on I came across [Lois Rossmann](https://www.youtube.com/user/rossmanngroup) on youtube when searching on how to repair my iMac and this dude rocks. He has this video where he [replaces the SMC chip an a macbook logic board](https://www.youtube.com/watch?v=D_Eiar3MPck). Since my failure obviously had something to do with power failing and Lois clearly states that it is bullshit to replace the SMC and almost never works I decided to give it a shot :D

I hit Ali up once more and 20 Euro and 3 weeks later I receive a piece of cut logic board with a SMC and a solder stencil.

![SMC and Stencil](/images/smc_and_stencil.jpg){: .project-image-medium}

Next is off with the old, reball the BGA (took me 4 tries but hey I had never done it before) and on with the new (or second hand in this case).

![Reballed SMC](/images/reballed.jpg){: .project-image-medium}

isn't she pretty!

So after resoldering (the BGA moved into place) and screwing the whole iMac together again (except the screen) I finally had a working LED!
So I press the on button aaaaaaand.........nothing DAMN IT!

Back to the drawing board I guess, My next plan of action will be buying the schematics and checking voltages I guess.

TO BE CONTINUED...

Oh by the way check out my new [printer upgrades](/projects/3d_printer/3d_printer_upgrades.html) while you are on this site.
