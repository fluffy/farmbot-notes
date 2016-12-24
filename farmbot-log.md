
# Fluffy and Rory Adventures in FarmBot

My young friend, who also has the awesome name of Rory, and I have decided to try and build a farmbot. We find it very cool what you are building and the way you are trying to make it all open source. If it is OK with folks, we thought we would post on this thread bits about our progress, challenges, what we are attempting to solve those, and random ideas for cool improvements. The goal being to share info that would be useful to others and at the same time get help from the community. Huge thanks to my friend Rick who got me going on this.


# Ordering Parts - Day 0 

Let me just start by saying I can't wait till I can jut go to the farmbot.io online store click "send me the whole thing" and be done. Most the parts I got from the sites suggested in the documentation.

We got the Plates from using the DXF file from 1.0 and had them cut by JP Metals in Calgary for approximately $200 US out of 3/16 aluminum. (not the 5mm in design). One thing we noticed is that seems to be missing the end bracket to mount the motors for the x axis. I think we will use the drawings from 1.0 to try and make one using a hacksaw and drill press. May try to cut with CNC router at some point.

The 1.1 drawings have a nice bent mental version of the Z motor mount but I think we will try and 3d print the one from the 1.0 drawings instead. 

I have no idea if the stepper motors and encoders we got will work but we ordered the stepper motor from inventables part number 25253-01 (https://www.inventables.com/technologies/stepper-motor-nema-17) and an AMT102-V encoder from digikey (http://www.digikey.ca/product-detail/en/cui-inc/AMT102-V/102-1307-ND/827015). How the encoder mounts on the motor is still an "miracle happens here step" but we might try to glue the encoder on to the motor. Any advice appreciated.  The motor is a SM42HT47-1684B from smart automation (http://www.smartautomation.com.cn/ProductShow.asp?ArticleID=498). In looking for steppers, I found googling for 42HT47 useful as well as the page at (http://reprap.org/wiki/NEMA_17_Stepper_motor)

To run the PI camera over an HDMI cable, I got the "Pi Camera HDMI Cable Extension" from Petit Studio (https://www.tindie.com/products/freto/pi-camera-hdmi-cable-extension/ ). Perhaps a USB camera would be a better idea. Will see what happens.

The RAMPS shield seemed to be out of stock most places but (http://www.sainsmart.com/) had them. All the stuff from sainsmart arrived quickly in nice case. I had not ordered from them before but I will use them again.


# Building Tracks - Day 1

We set up the tracks to be about 1m by 1m space because it -20C outside right now and we plan to learn how to build this farmbot by making a mini-farmbot inside this winter then rebuilding it to a full size one outside in the spring. Questions that came up:

* How exact does the width of the track need to be from one end to the other?

And tip for next time, if the y gantry bar is 1m long, then that needs to match the distance from the *outside* of track on one side to the *outside* of track on other side.

![tracks](images/_DSC0314.jpg)

# Building Wheels and Mounts for Gantry - Day 2

Anyone have good input on easies way to get the location of the wheels adjusted?

![wheels](images/_DSC0320.jpg)


# Building Gantry - Day 3 

Used lots of clamps and squares to try and get everything lined up square.

![gantry](images/_DSC0336.jpg)


# Building X Axis Drive Train - Day 4

Because we love instant gratification and, well, we want to see it move, we are going to try and get the X axis all connected up to web site and moving before building y and z.

The DXF files we used to get the cut plates did not include the correct corner brackets. We used what we did get on one side.

![motor1](images/_DSC0340.jpg)

On the other side  we used a drill press and hacksaw to make one

![motor2](images/_DSC0339.jpg)

If I was doing this again, I would consider order the end plate that vikhyat had designed at http://forum.farmbot.org/t/gantry-corner-bracket-drawing/1082 


## Setting up the Controller

Totally failed to get this to work until I attached a serial console to the Raspberry PI  to see what is going on. Would be nice to have all the log data show up on the web site but even with that, probably need a serial console to deal with errors getting on WIFI and such.

## Arduino firmware

Ran into bug (https://github.com/FarmBot/farmbot-arduino-firmware/issues/42) so can't get the X asis moving. Will have to decide how to attack this problem. Looking at the code, I think I might try a patch that any time the pins for the X1 motor are set, the corresponding pins for the X2 motor are also set.


# Build Cross Slide - Day 5

## Arduino Firmware Hacking

Wrote a little PR to fix the Arduino software so now it drives both X motors. Remember to wire one of the motors to go backwards. This can be done by flipping the connector upside down where the motor plugs into the RAMPS shield. 

## 3D Printing

Downloaded universal tool mount base from OnShape as STL. Loaded in CURA. Flipped upside down. Printed in PLA with high speed setting and no supports. Print time 2 hours with 41 grams of PLA on a Lulzbot mini.

## Build Cross Slide

I wonder if anything should be changed to reduce backlash on z axis screw?

![motor2](images/_DSC0351.jpg)


# Build Z Axis - Day 6

Was going to print motor mount out of nylon which would be much stronger but did a test run with PLA. The PLA version seems very strong (I can stand on it) so think I might just use that. I did not use any supports when I printed it and that left some weirdness in the hole for the wires. Should redo that hole so that it has a 45 degree ramp when printed and does not need to be printed with supports.

![motor2](images/_DSC0329.jpg)

Wishing the wire I got to connect up the motors was smaller and more flexible. Think I would use a cable with 8 wires each stranded 22 gage.


