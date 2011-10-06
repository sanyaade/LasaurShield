
The LasaurShield is a custom PCB for the [Lasersaur project](http://lasersaur.com). It's an [Arduino](http://arduino.cc/) [shield](http://arduino.cc/en/Main/ArduinoShields) that connects laser, stepper, stepper driver, stepper power, limit switches, door sensor, water chiller sensor, emergency stop sensor, and Arduino. Starting with v11.10 the core safety function are also hardwired on the board for more reliable operation.

The LasaurShield is designed around the SparkFun Eagle Library, their design and CAM job rules. Check out the [SparkFun Tutorial](http://www.sparkfun.com/tutorials/108) if you are new to this. If you are interesting doing your own production run check out [this tutorial](http://www.sparkfun.com/tutorials/109).


The following Eagle library and design files are being used:

- cam/sparkfun-gerb274x.cam
- dru/SparkFun.dru
- lbr/[SparkFun.lbr]
- lbr/con-phoenix-254.lbr (comes with Eagle)
- lbr/con-phoenix-508.lbr (comes with Eagle)
- lbr/con-weidmueller-sl35.lbr (comes with Eagle)


**DISCLAIMER:** Please be aware that operating a DIY laser cutter can be dangerous and requires full awareness of the risks involved. You build the machine and you will have to make sure it is safe. The instructions of the Lasersaur project and related software come without any warranty or guarantees whatsoever. All information is provided as-is and without claims to mechanical or electrical fitness, safety, or usefulness. You are fully responsible for doing your own evaluations and making sure your system does not burn, blind, or electrocute people.