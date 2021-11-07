# Púca Build Guide

## Contents

- Required Parts
- Getting Started
- OLED
- ProMicro
- Reset Switch
- Testing before continuing
- Diode
- OLED
- Hotswap Sockets


## Required Parts

Below are a list of all parts for building a Púca Pad. Optional items are listed separately.

### Required
| Name            | Quantity     |
|-----------------|--------------|
| PCB             | 1            |
| Diodes          | 23           |
| Reset Switch    | 1            |
| Pro Micro  / Elite-C     | 1          |
| Rotary Encoder  | 1            |
| Plate Botton    | 1            |
| Plate Top       | 1            |
| Acrylic Guard   | 1            |
| Standoffs and screws    | ......            |

### Optional
| Name            | Quantity     |
|-----------------|--------------|
| OLED Module     | 1            |
| WS2821B LED's   | 8            | 


## A video guide can be found here: 
[![](images/pucaVid.PNG)](https://www.youtube.com/watch?v=pTuVGP6S-aw&t=377s)


## Getting Started
Assuming you have all of the required parts listed above, you can start the process of building your Púca. 

The PCB for v1.3 is not reversible, which means that it must be used in its correct orientation. The correct layout can be seen below, but is essentially the side with the diodes and the Púca logo on the right. The microctroller also needs to be in the correct orientation, with the components facing down in the case of the supplied ProMicro or optional Elite-C/Bit-C.

<Insert image of Púca PCB orientation>

## Testing your Controller

Begin by plugging your ProMicro into your PC / laptop with an appropriate cable. If you haven't already, download the Púca firmware file. Then open QMK Toolbox, select the Púca Firmware file from the dropdown menu and short the reset and ground pads. This should auto-detect in QMK Toolbox, and allow you to click 'flash'. Some output will be displayed on screen, and you will be prompted once complete.

## OLED

If you intend on using the supplied OLED display with your Púca, then you will need to bridge four pads. These pads are located under the pro-micro, so it is recommended to bridge these first. Apply solder to one side of the pad and then drag across to the other, the finished product should look as follows:

![briged oled](images/bridgedOLED.PNG)

Close-up example of briged pads from CRKBD:

![](images/bridgedOLED2.PNG)
  
  
## Pro Micro / Elite-C
  
We will begin by soldering the microcontroller. We perform this now to ensure that the PCB and controller are functioning correctly, which will also help narrow the cause of any issues that could potentially occur here: most commonly due to incorrect soldering.
  
First, we will solder the ProMicro in place. This can be made hotswap using either millmax sockets or a ProMicro hotswap socket kit and either pins or diode legs. For this guide, we will assume that you have the Púca base kit, and will use parts available from there. Place the pins into the PCB as seen below:

<Insert image of pins placed into PCB>
  
We will then solder these in place. It is recommended to use a small piece of masking tape to hole the pins in place during this process to ensure it is kept flat.
  
![](images/pinTape.PNG)
  
Next, place your pro-micro / elite-c **face down**. The orientation here is extremely important for two reasons; Firstly, this provides a lower profile which allow the OLED and acrylic guard to be placed closer to the PCB. Secondly, it just won't work due to the pad placement. Make sure the orientation is correct, with the components facing downward, and the back of the pro-micro PCB visible. It should look like the image below:
  
<Insert image of correct mcu placement>

Then apply solder to each of the pins poking through the pro-micro. Ensure the solder provides a clean and solid connection, as seen below:
  
<Insert image of properly soldered ProMicro>
  
Desoldering a ProMicro is not an experience I would recommend.
  
![solder meme](images/solder.jpg)
  
  
## Reset Switch
  
Next, we will solder the reset switch in place so that we can flash firmware to the board. The orientation is not important here, as long as it is placed with the button to the top of the board and soldered from beneath. See image below:
  
![](images/resetSwitch.PNG)

  
## Testing before continuing

It is highly recommend to stop at this point and test that everything is working correctly. Desoldering components is not as easy as installing them, and troubleshooting at this stage is far easier than if all components have been installed.
  
If the above steps complete without issue, then everything is working correctly so far. We will test each stage throughout the build process to identify issues as early as possible.
  
  
## Diodes

Now we will start with the diodes. These will be on display on the right side of the PCB. The orientation here is important as a diode will only allow current to pass in one direction, placing it in the opposite direction will stop the current from passing from the switch to the ProMicro, and will result in the associated key not working. The PCB has a line on the north edge of the diode which represents the cathode end, this should match the line on the diode. The correct orientation can be seen below:
  
![](images/diodeOrientation.PNG)
  
You can do these individually if you wish, or row-by-row. For the purpose of this guide they will be done row-by-row. Joiners from the original GB will also be supplied with a diode bender to optionally use.
  
Place the leg of the anode end of the diode into the PCB, and bend 90 degrees to it will sit centrally. An example of this can be seen below:

<Insert image of diode with single bend>
  
Now, take note of roughly how far it is before the next bend, remove the diode and bend by hand. Place back into the PCB, and if done correctly, should sit flush against the PCB. An optional step you can take is to tape the diodes into place so they do not move position. If doing this optional step make sure to use kapton tape as it has a much higher heat tolerance than traditional tape, and will not melt under normal conditions:

![](images/diodeTape.PNG)
  
The diode legs on the back of the PCB can be bent to hold the diode in place, seen below:
  
<Insert image of bent diode legs on back of PCB>

Repeat this process for each of the 23 required diodes, ensuring that there is a strong connection and the orientation is correct. Use a pair of flush cutters afterwards to trim the excess diode legs. The finished diodes should look as follows:
  
![](images/diodesSoldered.PNG)
  
If you plan on using the OLED display skip ahead to the section: OLED (Optional). If not, we will test the diodes now. 

Carefully plug the ProMicro in and either open Vial or your key tester of choice. Vial will be used for remapping the keys with a GUI later on. Using a pair of tweezers, touch each of the pads on the bottom of the PCB. This will simulate a key press, and if the diode's have been soldered correctly should register on screen for you. If a key does not register here follow the steps in the Troubleshooting section at the end.


## OLED (Optional)

This is an optional item, however if you are intending on using the OLED it can be attached now. Place the OLED into position over the ProMicro and solder the four legs into position. If your diode has legs presoldered be aware that this will block your ProMicro, so will need to be removed if you plan on changing the controller. Optionally you can use diode legs instead of the supplied legs which can be bent out of the way in case the ProMicro needs to be changed in future.

![](images/oledPCB.PNG)
  
We will then test to make sure the OLED is working correctly. Simply plug the Púca in and the OLED should automatically power on, displaying the Púca ghost and layer information. If you did not test the diodes in the previous step, then we will do this now.

![](images/OLEDTesting.PNG)
  
Carefully plug the ProMicro in and either open Vial or your key tester of choice. Vial will be used for remapping the keys with a GUI later on. Using a pair of tweezers, touch each of the pads on the bottom of the PCB. This will simulate a key press, and if the diode's have been soldered correctly should register on screen for you. If a key does not register here follow the steps in the Troubleshooting section at the end.
  

## Hotswap Sockets

Púca uses kailh sockets to provide the hotswap feature, and are required for this build. These are to be soldered to the bottom of the PCB, the opposite side of where the ProMicro and diodes are currently sitting. To solder the sockets in place first put a small amount of solder on one of the pads as seen in the example below:

![](images/kailhPreSolder.PNG)

The purpose of this is that we will reflow this connection to hold the socket in place. Next, place the hot-swap socket into the PCB and make sure it is firmly pressed against the PCB, it is important to make sure these are as flat as possible so the switch pins can fit in correctly. Next, reheat the solder that was placed on the pad whilst pressing the hotswap socket against the board with tweezers (this can also be done by hand, but be very careful not to burn yourself). This will cause the solder to flow again, and create a connection with the socket.

Whilst completing this step keep in mind the layout that you wish to achieve and solder sockets appropriately.
Add a small amount of more solder onto the other end of the socket pressing against the pad to ensure a proper connection. Repeat this step for the other side so that both ends of the socket now have proper connections, example of how this should look below:

![](images/socketsSoldered.PNG)
  
## Underglow LED's (Optional)

This is an optional step and is only required if you wish to have underglow lighting on your Púca. To do this, simply solder the eight SMD LED's into their pads, taking note of the orientation of the LED. One of the corners of the LED has a triangle / is tabbed, and should be in the **opposite** corner to where you see the number one, see image below:
  
![SMD LED Orientation](images/ledOrientation.PNG)

Again, note the orientation and see that the tabbed corner opposite to the number one. All eight of the LED's are linked in sequence, so if one of them is soldered incorrectly, everything after will also fail to work. 
  
Solder one corner of the pad and place the LED into position, again making sure to use the correct orientation. Reflow the solder while lightly pressing the LED with a pair of tweezers so that it sits flush with the PCB. Continue to solder the other three pins to the pad.

   
## Rotary Encoder

Place the rotary encoder into place. It will only fit in one orientation: the side with two pins facing to the north, and the side with three pins facing to the south. Proceed t osolder these pins and the two clips on either side. See image below:
  
![](images/rotEncoder.PNG)
  
  
## Finishing up
 
  
## Troubleshooting

### Key presses not registering
  
This can be down to one of three common causes.
1) Diode is in the wrong orientation
2) ProMicro does not have a strong soldered connection to the PCB
3) Switch legs are not sitting in the hotswap socket correctly 
