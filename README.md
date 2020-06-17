# m1k-firmware

[![Build Status](https://travis-ci.com/zaunkoenig-firmware/m1k-firmware.svg?branch=master)](https://travis-ci.com/zaunkoenig-firmware/m1k-firmware)

This is the open-source firmware for the [Zaunkoenig M1K](https://zaunkoenig.co/). What follows are the instructions for installing this firmware on the M1K in Linux and Windows.

## Installing the firmware files on the M1K in Linux
When you already have the firmware files (because someone sent them to you for example) you can jump directly to step 4. Else you have to download the firmware files from GitHub first:
1. Download and unzip the M1K firmware at https://github.com/zaunkoenig-firmware/m1k-firmware by clicking on the green «clone/download» button at the right top corner of the files list.
2. Open up a terminal and execute the following three commands:  
`sudo apt-get update -qq`  
`sudo apt-get install -qq gcc-avr binutils-avr avr-libc`  
`make`
3. After make has been executed the two firmware files have appeared in C:\Users\Patrick\Downloads\m1k-firmware-master\m1k-firmware-master. The .hex file is called twobtn.hex and the .eep file is called twobtn.eep.
4. Install DFU programmer by executing the following two commands in a terminal:  
`sudo apt-get update -y`  
`sudo apt-get install -y dfu-programmer`
5. Copy the two firmware files you want to install into the DFU Programmer folder. The first firmware file is called twobtn.hex and the second one is called twobtn.eep.
6. Now you have to put the M1K into the «firmware update mode». There are two ways to do that. The first way is to short-circuit the two golden pins to the right side of the left switch: you know you succeeded when the mouse cursor freezes. However, for this method you have to open your mouse. The other way is possible without having to open up your M1K:  
Plug in the M1K while holding down both mouse buttons. After five seconds the cursor will move clockwise in a square to indicate that Angle Snapping and LOD have been changed to default values. This time though, do not let go of your mouse buttons yet. Keep them pressed down for five more seconds until your mouse cursor has frozen.
7. Now run the following four commands (each command will take a few seconds to finish):  
`sudo dfu-programmer atmega32u2 erase --force`  
`sudo dfu-programmer atmega32u2 flash continuous-button-polling-edwin.hex`  
`sudo dfu-programmer atmega32u2 flash-eeprom twobtn-v0.1.eep --force`  
`sudo dfu-programmer atmega32u2 start`
8. After you executed the start command your mouse should be up and running with the new firmware.

## Installing the Zaunkoenig M1K firmware in Windows
When you already have the firmware files (because someone sent them to you for example) you can jump directly to step 10. Else you have to download the firmware files from GitHub first:
1. Download and unzip the M1K firmware at https://github.com/zaunkoenig-firmware/m1k-firmware by clicking on the green «clone/download» button at the right top corner of the files list.
2. Open «Microsoft Store» from your Windows Start Menu.
3. Type «WSL» into the search bar.
4. Click on «Ubuntu», then on «Download».
5. Click on «Start» once the download is complete.
6. A terminal opens displaying the installation process. All you have to do is choose a username and a password and wait for the installation to finish (takes only a few minutes).
7. In the same terminal from step 6. you now have to open up the Windows folder into which the M1K firmware was downloaded. In my case: C:\Users\Patrick\Downloads\m1k-firmware-master\m1k-firmware-master. By inputting the following command into your terminal the above download folder will be opened: `cd /mnt/c/Users/Patrick/Downloads/m1k-firmware-master/m1k-firmware-master`
8. Execute the following three commands:  
`sudo apt-get update -qq`  
`sudo apt-get install -qq gcc-avr binutils-avr avr-libc`  
`make`
9. After make has been executed the two firmware files have appeared in C:\Users\Patrick\Downloads\m1k-firmware-master\m1k-firmware-master. The .hex file is called twobtn.hex and the .eep file is called twobtn.eep.
10. [Download the command-line programmer for Atmel USB microcontrollers called «Atmel USB DFU Programmer».](https://sourceforge.net/projects/dfu-programmer/)
11. After you installed DFU Programmer open up the folder «dfu-prog-usb-1.2.2» and right click on atmel_usb_dfu.inf and click on «install».
12. Copy the two firmware files you want to install into the DFU Programmer folder. The first firmware file is called twobtn.hex and the second one is called twobtn.eep.
13. Now you have to put the M1K into the «firmware update mode». There are two ways to do that. The first way is to short-circuit the two golden pins to the right side of the left switch: you know you succeeded when the mouse cursor freezes. However, for this method you have to open your mouse. The other way is possible without having to open up your M1K:  
Plug in the M1K while holding down both mouse buttons. After five seconds the cursor will move clockwise in a square to indicate that Angle Snapping and LOD have been changed to default values. This time though, do not let go of your mouse buttons yet. Keep them pressed down for five more seconds until your mouse cursor has frozen.
14. Start the Windows Command Prompt and execute the following: `cd c:\program files (x86)\dfu-programmer-win-0.7.2`
15. Now you have to run these four commands (each command will take a few seconds to finish):  
`dfu-programmer atmega32u2 erase --force`  
`dfu-programmer atmega32u2 flash twobtn.hex`  
`dfu-programmer atmega32u2 flash-eeprom twobtn.eep --force`  
`dfu-programmer atmega32u2 start`
16. After you executed the start command your mouse should be up and running with the new firmware.
