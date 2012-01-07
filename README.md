
The LasaurShield is a custom PCB for the [Lasersaur project](http://lasersaur.com). It's an [Arduino](http://arduino.cc/) [shield](http://arduino.cc/en/Main/ArduinoShields) that connects laser, stepper, stepper driver, stepper power, limit switches, door sensor, water chiller sensor, emergency stop sensor, and Arduino. Starting with v11.10 the core safety functions are also hardwired on the board.

The LasaurShield is designed around the SparkFun Eagle Library, their design and CAM job rules. Check out the [SparkFun Tutorial](http://www.sparkfun.com/tutorials/108) if you are new to this. If you are interesting doing your own production run check out [this tutorial](http://www.sparkfun.com/tutorials/109).


The following Eagle library and design files are being used:

- cam/sparkfun-gerb274x.cam
- dru/LasaurShield.dru
- lbr/[SparkFun.lbr]
- lbr/con-phoenix-254.lbr (comes with Eagle)
- lbr/con-phoenix-508.lbr (comes with Eagle)
- lbr/con-weidmueller-sl35.lbr (comes with Eagle)


**DISCLAIMER:** Please be aware that operating a DIY laser cutter can be dangerous and requires full awareness of the risks involved. You build the machine and you will have to make sure it is safe. The instructions of the Lasersaur project and related software come without any warranty or guarantees whatsoever. All information is provided as-is and without claims to mechanical or electrical fitness, safety, or usefulness. You are fully responsible for doing your own evaluations and making sure your system does not burn, blind, or electrocute people.

Some Notes about Using Eagle
=============================

Eagle is quite powerful but also awkward to use. It's easy to forget how to command the UI.

When designing the schematic
------------------------------
- import parts libraries, Library->Use
- some parts like the NAND gates require you to press the "Invoke" button and place power and ground. Don't ask me why.
- Once the schematic is done, run the electrical checks Tools->Erc

When laying out the board
--------------------------
- load design rules, Tools->Drc  (dru/LasaurShield.dru)
- place components, move/rotate to optimize the ratsnest
- color layers as needed, View->Display/hide layers
  - 121 _tsilk  ... is top silkscreen
  - 122 _bsilk  ... is bottom silkscreen
- run autoroute, 
  - The power of the autorouter is that it can be used incrementally. Some wires can be drawn manually and the autorouter can finish the rest. 
  - Another great approach is to draw some wires roughly (e.g. on one side of the board) then autoroute, rip the manual wires and autoroute again. This way the autorouter follows the general idea but draws the wires nicely.
- if the autorouter should use different trace widths this can be accomplished by defining net classes with different widths, Edit->Net classes
  - air wires of the ratsnest (it actually applies to the entire signal) can then be assigned to the various net classes

When creating the CAM Job (gerber files)
-----------------------------------------
- run final design rule check, Tools->Drc
- Open the CAM Processor, File->Cam Processor
- Open the CAM rule file, File->Open->Job   (cam/sparkfun-gerb274x.cam)
- Press "Process Job"
- At this point Eagle creates a bunch of files in the same directory as the board file. 
  - Top Copper (GTL)
  - Top Soldermask (GTS)
  - Top Silkscreen (GTO)
  - Bottom Copper (GBL)
  - Bottom Soldermask (GBS)
  - Bottom Silkscreen (GBO)
  - Drill File (TXT)
  - Drill Summary (dri)
- before sending these to a manufacturing house check them with [Viewplot](http://www.viewplot.com/) or by uploading a zip to [circuitpeople.com](http://circuitpeople.com/).



Parts List for v11.11 Upgrade
==============================

2   resistor 10 KOhm    271-10K-RC    (making it a total of 7x)
1   e-stop button 24mm    642-A01ES
1   e-stop SPST block    642-A0150B
2   NAND Gates IC    863-MC74AC20NG
1   DIN rail 1m    651-5602100
1   relay 277VAC@25A for DIN rail    528-725BXXSC3ML-24D
8   terminal block for DIN rail    651-3004362
1   terminal block side cover    651-3003020
5   terminal block bridge    651-0201155
1   power supply 24V for DIN rail    845-PS-6024    (replacement)
1   power entry connector, C-20   562-744W-00/04 
1   power entry connector, C-14   161-R30148-E


Test for v11.11
===============

- chiller hard logic ... ok
- limit switches hard logic ... ok

- limit switch input
- chiller input
- overwrite
- rel input


git push -u origin master


