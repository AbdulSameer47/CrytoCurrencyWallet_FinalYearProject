# Highly Secure Cryptocurrency Wallet

## INTRODUCTION
The digital currency and payment system cryptocurrency has become more popular in recent years. ​
The value of one Bitcoin was $0 when it was first introduced in 2009 and today it is approximately $52,586.​
The number of Bitcoin users and investors increased dramatically. ​
Unlike other payment systems, Bitcoin is not controlled by a central authority. Instead, it is operated by a decentralized authority, the Bitcoin network. ​

## PROBLEM STATEMENT
Due to the increase in the popularity of bitcoins in recent years, this popularity has also led attackers to find different methods the retrieve the victims private key(by attacks like MITM, adding key logger to victim's system, etc.) which is stored online and is always at the risk of being stolen, to provide an enhanced method of security we propose using a Hardware wallet to store the private keys since it is an offline device the chances for attack are greatly reduced. ​

## Solution
We propose the use of a hardware wallet for the authentication of every payment, this will provide a security from the hackers because the private key would be on an offline device built using raspberry pi zero. Which allows the users private key to be separately stored in a hardware device and which is not vulnerable to online malware attacks. ​
Hence providing security and ensuring a reliable transaction​

## SYSTEM DESIGN
![alt text](https://github.com/AbdulSameer47/CrytoCurrencyWallet_FinalYearProject/blob/main/SystemDesign.png
)

##  Hardware Requirements
* Raspberry Pi Zero W
* Micro USB Cable
* Micro SD Card 8GB
* OLED Display
* Buttons
* Jumper wires
* Heat sink
## Software Requirements
* Pitrezor SD Card images
* Trezor Bridge
* Wallet.trezor.io (Website)
* Bonjour Services
* BalenaEtcher

# Step-By-Step instructions(DIY)

1. download Etcher from here: https://etcher.io/. This software is used to write the program image to 
the SD card.
2. Download the latest pitrezor SD card image by clicking here.
3. Start etcher. You will need to connect the SD card to your computer to flash the pitrezor image file.
4. After the card is flashed, put it in the SD card slot in the pi.
5. Connect the USB cable in the USB port near the center of the pi as shown above, not the one near the 
corner. 
6. Connect the USB cable to your computer or a USB power supply. You 
should see the pi boot sequence in the monitor and after 4-5 seconds the trezor logo 
should appear.
7. Now disconnect the USB cable, HDMI adapter and cable and remove SD card.
8. Solder the 2 buttons to the pi. The red button (called "no") is connected to the pins 30 
and 32. The green button (called "yes") is connected to the pins 34 and 36. 
9. Put back the SD card in the pi and reconnect the HDMI and USB cable back to your 
computer.
10. Open a browser on your computer and navigate to https://wallet.trezor.io
11. You will be requested to install the trezor bridge if you never did it before. Select your 
operating system to download the correct bridge software and perform installation.
12. If the bridge is already installed, you should see a message that invites you to connect 
your trezor. Connect the USB cable of your pi.
13. The browser application should detect the device and invite you to perform the trezor 
setup.
14. During the setup you will need the buttons to go from one seed word to another.
15. If all is working correctly you can disconnect everything to solder the OLED display. 
The I2C OLED display need 4 wires to solder and the SPI OLED uses 7 wires. 
16. Connect the SD card back to your computer and refer to the configuration section below 
to correctly configure your OLED model and orientation. There are only 2 possible
orientations so you can try both and see which one is better for you.
17. Reconnect everything and retry your device. Now you should see the output on the 
OLED.
18. If that work, put everything in a box and your good to go!

## Configuration
If you connect the SD card in your computer you should see a file named "pitrezor.config" in 
the first partition (boot partition). You can open this file with your favorite text editor. You will 
be able to change the configuration variables which are:
TREZOR_OLED_SCALE: This controls the scale factor of the display to apply when using 
the HDMI output. A scale factor of 1 means the default size of 128x64 pixel. A scale factor of 
2 will stretch the image to 256x128 and so on.
TREZOR_OLED_TYPE: Specify the type of OLED connected to the pi zero. The file 
enumerates the different value and their meaning. Select the one that match your OLED 
display.
TREZOR_OLED_FLIP: Set to 0 or 1 to control the image vertically (normal or inverted) This 
is useful depending how you assemble the OLED in an enclosure.
TREZOR_GPIO_YES and TREZOR_GPIO_NO: Specify the GPIO number to use for the 
yes/no button. 
When you change a value, keep the line formatting as-is with the export statement. Just change 
the number after the equal sign. If you change something else, this could prevent the pi trezor 
application to start correctly.
For the Adafruit bonnet, you must change the values to these:
export TREZOR_OLED_TYPE=1 <br />
export TREZOR_OLED_FLIP=1<br />
export TREZOR_GPIO_YES=6<br />
export TREZOR_GPIO_NO=5<br />
Code for I2C OLED DISPLAY<br />
pitrezor.config<br />
#Scale factor of display when using HDMI (1 to 16 inclusively)<br />
export TREZOR_OLED_SCALE=2<br />
#Type of oled to use<br />
#NO OLED = 029<br />
#OLED_ADAFRUIT_I2C_128x64 = 1<br />
#OLED_SEEED_I2C_128x64 = 2<br />
#OLED_SH1106_I2C_128x64 = 3<br />
#OLED_ADAFRUIT_SPI_128x64 = 4<br />
#OLED_SH1106_SPI_128x64 = 5<br />
export TREZOR_OLED_TYPE=3<br />
#Flip the display vertically. Set to 0 or 1 <br />
export TREZOR_OLED_FLIP=1<br />
#Set gpio number to use for the yes/no buttons<br />
export TREZOR_GPIO_YES=16<br />
export TREZOR_GPIO_NO= 12


