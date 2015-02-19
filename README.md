ReflashBlinkM
==============

How to update the firmware in a BlinkM

![](http://farm5.static.flickr.com/4154/5189904937_5b8e9ea93a_o.png)

## Introduction

All BlinkM-family devices have the ability to have their firmware upgraded. This means you can install your own firmware on the devices (using them as an ATtiny development board), or trying out alternative firmwares like [CyzRgb](http://code.google.com/p/codalyze/wiki/CyzRgb).

Previously you needed an AVR ISP programmer like the [AVRISPmkII](http://www.atmel.com/dyn/products/tools_card.asp?tool_id=3808) or the [USBtinyISP](http://www.adafruit.com/index.php?main_page=product_info&cPath=16&products_id=46).  Thanks to the [ArduinoISP](http://arduino.cc/en/Tutorial/ArduinoISP) sketch that ships with Arduino, if you have already have an Arduino, you can easily reflash your BlinkM with new firmware.

The ReflashBlinkM application is a tool for Mac OS X and Windows that uses ArduinoISP to help you reflash BlinkMs to their default firmware.  ReflashBlinkM is written in [Processing](http://processing.org/).

##  Steps to using ReflashBlinkM
  * Download ReflashBlinkM app for your OS
  * Load ArduinoISP onto an Arduino
  * Wire up the BlinkM to Arduino 
  * Plug Arduino + BlinkM into USB of your computer
  * Launch ReflashBlinkM
  * Pick the firmware you want and the serial port the Arduino is on
  * Press the "Reflash" button!


##  Detailed Step-by-step 

### 1. Download ReflashBlinkM app

Go to the [ReflashBlinkM repo](https://github.com/todbot/ReflashBlinkM) and download ReflashBlinkM for your platform.  Pick the one for your OS, and unzip it.  Or compile your own.

###  2. Load ArduinoISP onto an Arduino 

The ArduinoISP sketch comes with Arduino.  Select it and program the Arduino with it.
![](http://farm2.static.flickr.com/1002/5189961979_09e33bf1bd_z.jpg)

### 3. Wire up BlinkM to Arduino 

The BlinkM has to be wired up in a different manner than the way it normally is.  The AVRISP protocol to reflash needs 6-wires.

NOTE: In order to make good electrical connection, you may need to press down on the BlinkM/MinM or otherwise ensure the connections or good during the reflashing process.  Otherwise the reflashing will fail.  (But don't worry, you can just try again)

Wiring Diagrams:

![http://www.flickr.com/photos/todbot/5189406314/](http://farm5.static.flickr.com/4112/5189406314_f79bab3814.jpg)
![http://www.flickr.com/photos/todbot/5189406458/](http://farm5.static.flickr.com/4151/5189406458_01cc5c19f7.jpg)

Suggested Physical layout:

![http://www.flickr.com/photos/todbot/5189389248/](http://farm5.static.flickr.com/4151/5189389248_a93bcc9e5b.jpg)
![http://www.flickr.com/photos/todbot/5189388534/](http://farm5.static.flickr.com/4152/5189388534_82448716a9.jpg)

### 4. Plug Arduino + BlinkM into USB of your computer

Once everything is wired up, plug the Arduino into the USB jack of your computer.

## 5. Launch ReflashBlinkM

Double-click on the unzipped application you obtained from Step 1 and you should get the application window at the top of this page.  Windows users: if there is a message about no "javaw.exe".  Then you need to install Java.  Visit http://java.com/ for the quick download.

## 6. Pick the firmware you want and the serial port the Arduino is on 
Now you can pick which firmware you want to use.  Note that due to differences in the chips used in different types of BlinkMs, not all firmwares will work.  If you choose the wrong one, ReflashBlinkM will be able to tell when it attempts to reflash.  No harm will come to your BlinkM if the wrong firmware is chosen.

![http://www.flickr.com/photos/todbot/5190503328/](http://farm5.static.flickr.com/4154/5190503328_57d3e88c67_o.png)

### 7. Press the "Reflash" button! 
At this point ReflashBlinkM will attempt to use your Arduino with ArduinoISP sketch as a programmer to reprogram the BlinkM.

If everything is connected correctly, you'll see a progression of messages telling you what it's doing, finished with a "Reflashing Done!" message.

If there is a problem, ReflashBlinkM will attempt to figure out what the problem is and give you a message suggesting a solution.

Some error messages that can be encountered:
  * "Can't open serial device, try another" -- The serial port chosen apparently doesn't have an Arduino with ArduinoISP on it.
  * "Programmer not responding. ArduinoISP loaded?" -- An Arduino was detected but ArduinoISP doesn't seem to be loaded onto it.
  * "Prorammer not responding. Check connections" -- An Arduino with ArduinoISP is found, but the wiring to BlinkM is faulty or intermittent
  * "Verification error, bad wiring?" -- Programming worked for a while, but verify failed, usually indicating a loose connection
  * "No chip detected. Check connections" -- Another type of bad wiring error.

##  Video of Reflashing
Because the blue LED of BlinkMs is hooked up to one of the programming lines, it makes for a good visual indication that reflashing is working.  Below is a video of a BlinkM MinM being reflashed.

http://www.youtube.com/watch?v=PMBtjAPBdwI

<iframe width="420" height="315" src="https://www.youtube.com/embed/PMBtjAPBdwI" frameborder="0" allowfullscreen></iframe>
