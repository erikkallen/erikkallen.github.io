---
layout: project
title: 3D Printer
date: 2016-7-13 22:00
updated: 2016-7-22 22:00
description: Making 3d objects a reality.
thumbnail: /images/3d_printing.png
---

* TOC
{:toc}

## My Printer's specs

![My Printer](printer_picture.jpg){: .project-image-medium}

|||
|------------------|-----------|
| **Brand**        | TronXY    |
| **Type**         | Prusa i3  |
| **Extruder**     | MK8       |
| **Heated bed**   | yes       |
| **Firmware**     | [Marlin](https://github.com/erikkallen/Marlin_tronxy)    |
| **HAL Sensor**   | PL-08N    |


## Filaments

##### [Real&reg;](http://real-filament.com) Filament [PET-G](http://real-filament.com/pages/product-details?id=2) Translucent blue

* Print on Kapton tape, with heated bed at **80 &deg;C**
* Extruder temp: **235 &deg;C**
* Speed: **60 mm/s&sup2;**

##### Manufacturer supplied PLA black

* Print on Kapton tape, with heated bed at **60 &deg;C**
* Extruder temp: **195 &deg;C**
* Speed: **60 mm/s&sup2;**

##### Manufacturer supplied ABS black

* Print on Kapton tape, with heated bed at **105 &deg;C**
* Extruder temp: **220 &deg;C**
* Speed: **60 mm/s&sup2;**

##### Purement antibacterial PLA white

* Haven't tried this yet will update as soon as I can
* Print on Kapton tape, with heated bed at **? &deg;C**
* Extruder temp: **? &deg;C**
* Speed: **? mm/s&sup2;**

## Upgrades

#### Heated bed

* I put a piece of cardboard under the heated bed which significantly improved the warmup time.

#### X Carriage

* I printed a replacement X-Idler with tensioning screw from MazaaFIN [X-Idler Thing](http://www.thingiverse.com/thing:1103976)

![Corner piece](x_idler.jpg){: .project-image-medium}


#### Y Carriage

* I printed a replacement Y-Idler with tensioning screws from bunjatec [Y-Idler Thing](http://www.thingiverse.com/thing:1298757)

![Corner piece](y_idler.jpg){: .project-image-medium}

#### MK8 Fan air redirect for PETG

* I made an Air redirector because the extruder fan was blowing air on my print and the PETG filament does not like that.


## Printed objects

Most of my designs can be found on [Thingyverse](http://www.thingiverse.com/erikkallen/designs)
I use Autodesk Fusion 360 for designing

#### Some printed objects:

[![Corner piece](corner_piece.jpg){: .project-image-medium}](http://www.thingiverse.com/thing:38277)
[![X-Motor bracket](prusa_x_motor_bracket.jpg){: .project-image-medium}](http://www.thingiverse.com/thing:1103976)
[![Prusa i3 rework X-Carriage](prusa_rework_x_carriage.jpg){: .project-image-medium}](http://www.thingiverse.com/thing:119616)
![Front door number](front_door_number.jpg){: .project-image-medium}

## Settings

### My Slic3r config
<style type="text/css">
  .gist-file
  .gist-data {max-height: 500px;}
</style>
{% gist erikkallen/1b010b535f7ad495977217d6f1963baa %}
