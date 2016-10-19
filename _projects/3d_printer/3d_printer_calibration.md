---
title: 3D Printer calibration
date: 2016-07-13 22:00:00 Z
layout: project_sub
updated: 2016-7-22 22:00
description: How to calibrate my printer.
thumbnail: "/images/3d_printing.png"
sub_page: true
---

## [3D Printer](3d_printer.html) &raquo; calibration

What I do to calibrate is:

1. First prep your printbed, this can be done with blue painters tape or kapton tape (some people say gluestick works as well but it did not work for me)

2. Connect your printer to a computer through the usb cable

3. Install and start Printrun http://koti.kapsi.fi/~kliment/printrun/ or any other gcode sender like Repetier-host

4. Find the terminal in printrun (right part of the screen)

5. Now type the command **G28** (your printer should now home all its axis)

6. Move the printer head to the center of the bed by typing **G1X100Y100F6000**

7. Now use the controls to move the nozzle onto the bed so that a piece of paper can fit between the nozzle and the printbed (you should be able to move the paper but it should touch the nozzle)

8. If your printhead does not go lower because it hit Z0 you can issue the command **G92Z10** to tell the printer it's position is 10mm, be carefull now though because you can crash the head into the bed!!! So slowly step down with 0.1 increments until you touch the paper.

9. now look at your display it should say your current Z value if you used G92 subtract 10 from the value so 9.5 becomes -0.5

10. enter the command **M851** the printer should reply with a Z value

11. take the Z value from the printer and add the value you calculated in step 9. so if the Z offset was -1.6 and your calculated value was -0.5 then is should become -2.1

12. Set this value to the printer with the command **M851Z-2.1** use your own value for -2.1 of course

13. Save the values by sending the command **M500**

14. Now redo the homing and bed leveling **G28** and **G29** and recheck the offset in the center  **G1X100Y100F6000** and move slowly to Z0 using the controls again.

15. If this is correct you should be set for printing.

16. Download the 20mm test cube and open up slic3r click add and select the test cube.stl

17. Most default settings should be fine but pay attention to certain things:

- Temperature of the bed (60 for PLA and 105 for ABS)
- Extruder temperature (195 for PLA and 220 for ABS)
- Nozzle diameter I think default with tronxy is 0.4
- Infill 0%
- Enable skirt

Also make sure the Z offset in slicer is set to 0
And edit the start gcode section to:

**G1 Z5 F5000 ; lift nozzle
G28 ; home all axes
G29 ; auto level**

18. Export the gcode

19. Switch back to Printrun and load the gcode file

20. Now press print and the magic should commence



[Back](3d_printer.html)
