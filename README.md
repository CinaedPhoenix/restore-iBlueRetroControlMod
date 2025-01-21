# restore-iBlueRetroControlMod

## How to maybe fix your iBlueControlMod...

Did you ignore/overlook the warning not to flash the official BlueRetro firmware to your new iBlueControlMod...?
...is the blue light on port 3 lighting up and is the gamecube no longer powering on? 
...Then you are like me... 



## End-User License Agreement (EULA) and Disclaimer

By using this guide to reflash your iBlueControlMod, you acknowledge and agree to the following terms:

No Warranty:
This guide is provided "as is," without any warranty of any kind, express or implied. Reflashing a micro controller carries inherent risks, and there is no guarantee that following this guide will resolve your issue.

Assumption of Risk:
You assume all responsibility and risk for using this guide. The process described may result in permanent damage to your hardware, void warranties, or render your PCB inoperable.

Limitation of Liability:
Under no circumstances shall the author of this guide be held liable for any direct, indirect, incidental, special, or consequential damages arising from the use of this guide or the inability to use it, including but not limited to hardware damage, loss of data, or loss of functionality.

Use at Your Own Discretion:
By proceeding with the reflashing process, you agree that you are performing these actions voluntarily and at your own discretion.

If you do not agree to these terms, do not proceed with the reflashing process. 
Always consult with a professional if you are unsure about any step in the process.


## Disclaimer.

If you are able to have the board RMA'ed you should do this before attempting the repair. (IMHO)


## Hardware needed:

* iBlueControlMod PCB, rev 1.1, MCU is a ESP32-WROOM-32
![Image of my iBlueControlMod PCB, rev 1.1, MCU is a ESP32-WROOM-32](/img/PCB-v1.1.jpg) 

* A USB-UART device to connect to the MCU directly, mine is a HW-193 version.
![Image of my USB-UART, HW-193](/img/USB-UART.jpg) 

* Wires and a soldering iron.


## Step 0

Step 0 is untested, but my hunch says it might work... 

if you are really lucky and can still connect to the module via bluetooth (via "THE SOFTWARE or via blueretro.io) you can grab "\firmware\ESP32-D0WDQ6 (revision 1)_factory_0x10000_0x100000b.bin" and upload this instead.


## Step 1

Remove the CR1220 Battery from your iBlueControlMod.

Then connect the USB-UART to the MicroController in the following way:

![Image of the wiring I used](/img/wiring.png) 

Doublecheck for any bridged connection before proceeding.

Connect the USB-UART to your PC.


## Step 2

Open a chrome-based browser and go to: https://tyeth.github.io/read-partitions-esptool-js/

On the webpage:
Set Baudrate to 460800 (I had more success with the connection this way)
Press "Connect"
Choose the COM port corresponding to your USB-UART
Press "Connect"

![Image of USB port selection](/img/comport.png)

Set Partition Table Offset to 8000
Press "Read Partition Table"

![Image of Read Partition Table](/img/readparttable.png) 

Warning...! If you do not see a partition table like this:

![Image of Partition Table](/img/parttable.png) 
...Your problem might not be solvable by my solution...

I recommend that you backup all partitions at this point, press all the save buttons highlighted here:

![Image of save buttons](/img/savefiles.png) 

Also save an image of your current partition table for future use.


## Step 3

Press the "Choose File" button and locate the file you saved from the partition "factory".

![Image of choose file button](/img/choosefile.png) 

In the "Flash Address" input box, input the address of the partition "ota_0",
in my example, it's was address "0x110000".
And press the "Program" button.

![Image of Flash address dialog](/img/flashaddress.png) 

Sadly, this is where my screenshots ended and I don't want to redo it...
But you should be done with the programming at this point.

Wait untill the flash is done, then disconnect:

![Image of disconnect button](/img/disconnect.png)

then unplug the USB-UART from your PC.

## Step 4

Desodder the wires from the MicroController.

Reinsert the CR1220 battery into the iBlueControlMod board.

Reinstall the iBlueControlMod into your gamecube.



...I sincerly hope this has resolved the your issue...

