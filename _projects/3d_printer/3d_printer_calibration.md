---
layout: project_sub
title: 3D Printer calibration
date: 2016-7-13 22:00
updated: 2016-7-22 22:00
description: How to calibrate my printer.
thumbnail: /images/3d_printing.png
sub_page: true
---
## [3D Printer](3d_printer.html) &raquo; calibration

What I do to calibrate is:

* Issue M851 command it will tell you the current Z offset, remember this value
* Now run the G28 command followed by G29 the printer will now do the bed leveling
* Then move the head to the center G1 X100 Y100 F2000
* Move the head to what the printer thinks is Z0 with the command G1 Z0
* Now measure the distance (or eyeball and increment the procedure with smaller steps)
* Next adjust the Z offset by taking the remembered Z value - the value you measured so in you case is Z offset was 0 then now Z should be -3.3 by issuing the command M851 Z-3.3
* Then repeat the steps 1 till 4 until you are happy with the result and finally save the offset with M500


[Back](3d_printer.html)
