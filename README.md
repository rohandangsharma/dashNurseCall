**How to Setup Amazon Dash buttons to work with IFTTT using .iso file**


What you will need:
* Raspberry Pi 3 Model B
* Micro USB to AC to power Raspberry Pi
* Micro SD Card (16GB+) with adapter
* Monitor/TV, Mouse, Keyboard for Setup
* HDMI cord
* A program to burn .iso files to SD Cards
* 1 or more Amazon Dash Buttons


Instructions:
1. Format SD card to FAT or FAT32 format
2. Burn .iso file to the Micro SD card. The .iso image can be downloaded here:
Amazon Dash .iso Image (https://drive.google.com/open?id=0B68EGwJQB1HqY1Y2VUw0UmZfZ1E)
A good burning program for Mac OS is Etcher: https://etcher.io. Don’t worry if the validation fails. For Windows, use Win32 Disk Imager (https://sourceforge.net/projects/win32diskimager/).
3. Insert Micro SD card into Raspberry Pi.
4. Connect Mouse and Keyboard to USB ports in Raspberry Pi and connect to Monitor with HDMI cord
5. Give Raspberry Pi power with Micro USB cable
6. Connect to local wireless network by clicking wifi icon in top right corner of screen.
7. Download the Amazon App on Android or iOS. Then, set up your dash button on the same wifi network as the Raspberry Pi. An instructional video can be found here:
Dash Button Set Up Video (https://drive.google.com/open?id=0B68EGwJQB1HqU1lIdmZyS2FFOFk)
8. Open terminal
9. Type the following:
cd dasher
script/find_button
	

10. Now press the button on your dash button. When this is done a device either titled “unknown manufacturer” or “Amazon Technologies Inc” will appear. Copy the Mac address of this device. The Mac address will by a set of numbers and letters formatted like this: XX:XX:XX:XX
11. Once you have the Mac address, press “control” and “C”
12. Now type the following:
sudo nano config/config.json
	

13.  Each of the sections in the file is a dash button. Change the “address” to the Mac address you just found.
14. Now use IFTTT (https://ifttt.com/) to make an applet that takes in a Webhook and outputs a text message, email, or another way of notifying that a button was pressed. Remember or write down what you name your “trigger”
15. Then change the “url” part of the config.json file to reference your new applet. Format the url like this:
   1. In IFTT to go “search” and search for “webhook”. Once in webhook, click “settings”. There should be a url. Copy everything after the “https://maker.ifttt.com/use/”. This is called the maker key
   2. Go to the config.json file and replace the url with: “https://maker.ifttt.com/trigger/youreventname/with/key/yourmakerkey”
   3. Now replace the “youreventname” with what you named your trigger
   4. Then replace “yourmakerkey” with the maker key found in part a.


16. Press “control” and “x” to exit when done. Type “Y” when prompted and then “enter”. This should return you to the terminal.
17. Click you dash button and check if it did what you intended! You no longer need the monitor, keyboard or mouse if it works.
