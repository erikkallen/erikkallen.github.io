---
title: More is better! Mendel90
date: 2016-11-18 18:50:00 Z
categories:
- 3d printing
tags:
- 3d printer
image: images/y-carriage.jpg
---

Every self respecting 3D printing guy has to have built his own 3d printer. By buying a kit from china I felt like that was cheating.
So after looking at some printer designs I decided to go with the Medel90 by Nophead. Since it is fully customizable and can be built with simple tools and someMDF board.

So I went to the hardware store to get a piece of MDF 12mm thick and a bunch of screws, some smooth rod, threaded rod, nuts and bolts. Once at home I fired up my 3d printer to print the needed parts starting with the frame blocks. To cut and drill the plates I printed the design on multiple A4 using Adobe Acrobat reader in poster mode.

![Drill hole design](images/drill_holes.jpg){: .project-image-medium .rounded}
![Frame setup](images/setting_up_the_frame.jpg){: .project-image-medium .rounded}

Next I started on the axis, again I needed printed parts and I cut the rods to length and started mounting the Y-axis.
Slowly I started to realize I needed motors to make this thing do anything at all and luckily our primary source of cheap stuff did not let me down.
I bought 5 [nema 17 stepper motors](https://nl.aliexpress.com/item/5PCS-59Ncm-84oz-in-Nema-17-Stepper-Motor-2A-4-wire-1m-Cable-for-DIY-3D/32589488227.html?spm=2114.13010608.0.0.AlLwHr&detailNewVersion=&categoryId=100007155) from a German warehouse with a torque of 6 kgcm for only &euro;56,- and the best thing was they arrived that same week!

![axis_build](images/axis_build.jpg){: .project-image-medium .rounded}
![Y carriage](images/y-carriage.jpg){: .project-image-medium .rounded}

![stepper_motors](images/stepper_motors.jpg){: .project-image-medium .rounded}
![mounted carriage](images/mounted_carriage.jpg){: .project-image-medium  .rounded}

The next problem I faced was that I did not have any enstops that fitted the design, I did however have some optical endstops laying around so I used 1 of those.
Be careful when connecting them though my melzy board for some reason supplies 12V to the endstop V+ pins and I fried one endstop by hooking it up to that. So after a bit of pcb trace cutting and a bodge wire 5V was where it is supposed to be and..... I decided to only use 1 optical endstop :D because I found some tactile witches on an old mouse which where a bit smaller but by printing [an adapter](http://www.thingiverse.com/thing:1879103) they fit on the original design like a glove.
![endstop_adapter](images/endstop_adapter.jpg){: .project-image-medium .rounded}

After adding some wires I could finally test if the thing moves at all and what do you know it works and even homes!
So thats is my progress up to now, I still have some work to do with the hotend and cleaning up the wiring but I hope to post a first print soon!
