# TKL keyboard "from scratch"

Being bored during the covid lockdown, I tried to learn a bit about electronics how my mechanical keyboard works. To practice, I wanted to build my own PCB, and why not try to build a usable keyboard.

## Disclamer : language mastery

I'm from France, I learn english mainly thanks to pop culture (TV shows/movies/videogames and lurking on reddit), so let me know if some sentences are gibberish or if I'm not clear enough.

## Table of Contents

* [Learning sources](#learning-sources)
* [Software/equipment/services used](#software-equipment-services-used)
* [Schematics](#schematics)
* [PCB](#pcb-design)
* [Soldering](#soldering)
* [Flashing Firmware](#flashing-firmware)
* [Troubles oh troubles](#troubles-oh-troubles)

## Learning sources

I learned how matrices works thanks to [r/MechanicalKeyboards/](https://www.reddit.com/r/MechanicalKeyboards/), and soon found [ruiqimao's awesome guide](https://github.com/ruiqimao/keyboard-pcb-guide). As you will see, the schematics I made are very similar to his.

## Software/equipment/services used

For schematics and pcb design, I used [Kicad](https://kicad-pcb.org/).
For pcb manufacturing, I went to [JLCPCB](https://jlcpcb.com/).
For components, I went to [Digikey](https://www.digikey.com/) and [RS components](https://www.rs-online.com/)
For soldering tools and materials, I bought from divers Amazon sellers :
* [Soldering tools](https://www.amazon.fr/gp/product/B07PLTB46N/ref=ppx_yo_dt_b_asin_title_o06_s01?ie=UTF8&psc=1)
* [Flux](https://www.amazon.fr/gp/product/B002OB4CIE/ref=ppx_yo_dt_b_asin_title_o05_s00)
* [Solder](https://www.amazon.fr/gp/product/B07PDFF5NZ/ref=ppx_yo_dt_b_asin_title_o06_s01)
For plate and case design, I used [Blender](https://www.blender.org/),
For plate and case printing, I used my [Ender3](https://www.ender3.fr/) 3D printer.
for switches and stabilizers, I bought from [kbdfans](https://kbdfans.com/)

## Schematics

Inspired by [u/Ryvaeus](https://www.reddit.com/r/MechanicalKeyboards/comments/4qdu9o/help_ive_planned_my_matrix_and_teensy_pinout_for/), I went for a 12*9 matrice :

![Schematic](/kicad_project/schematics.png)

I did a first try with micro USB, but had a lot of problems soldering correctly, so I made a USB B + holes (so i can have an option to solder a non removable cable) 2nd version.

## PCB Design

It was the first PCB I designed, I'm pretty proud but I guess there might be a problem as you will see right bellow. 
![PCB](/kicad_project/pcb.png)

## Soldering

I have not soldered diodes for now because of the issues you will learn about in the next chapter.

![USB cable soldering](/soldering/usb-cable.jpg)
![PCB](/soldering/micro-comp.jpg)


## Flashing Firmware

I plugged it into my desktop, pressed the RESET button, and flashed it with QMK Toolbox (there was no error). But then nothing, so I unplugged and replugged it, to have windows tel me "USB descriptor failed".

![Screenshot Error 1](/troubles/USB_not_reconized.png)
![Screenshot Error 2](/troubles/USB_descriptor_failed.png)

## Troubles oh troubles

I tried to re-install my USB controllers driver, I tried to flash a few more time, even changing from QMK toolbox to QMK flasher, but I could not make it work.

Then I tried to plug it on my laptop (XPS13, with USB C adaptator), and it was recognised as the keyboard it is destined to be !

![XPS success](/troubles/xps_try.png)

Thinking the USB Male port could be the problem, I replaced the cable by one I know works perfectly. It was unproductive, and strangely it does not work anymore on my laptop (same errors as in my desktop) I tried again to re-install my USB controllers driver on both machines, nothing.

I tried to discharge capacitors before plugging it in, and it seems to connect and disconnect maybe 5 times before showing me the "USB descriptor failed" error.

I just tried to get into DFU mode by using the RESET button, and it does not even work..

You can find all the sources (except the v1 schematics, I cannot find it, I think I threw it) in the repo.