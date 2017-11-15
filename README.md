# Raspberry Pi Zero W Installation

## Summary

In this project I am detailing an installation of a 
Python-ready web server on a Raspberry Pi Zero W.
The system is built from bare metal to fully functinoal.

## Requirements
  Each bulleted item lists the generic requirement with 
  details of my specific hardware listed below the 
  bulletpoint.
### Hardware
* Raspberry Pi Zero W
* microSD card  
  16GB SanDisk Ultra PLUS microSDHC UHS-1 Card
* power cable  
  USB <-> microUSB
* power source  
  battery

### Software
* Raspbian  
  Stretch (2017-09-07-raspbian-stretch-lite)
  Linux raspberrypi 4.9.41+ #1023 Tue Aug 8 15:47:12 BST 2017 armv6l GNU/Linux

## Configuration
### SD Card Setup
1. Download the Raspbian OS image and write it to the SD Card
  on a host system. On linux the image can be written with a 
  command similar to:
  ```sudo dd status=progress bs=4M if=<image file> of=<SD Card device>```

1. Mount the small "boot" partition located on the newly 
   prepared SD Card. Don't confuse this with the "/boot" 
   directory in the larger main Linux partition on this card.

1. Create an "ssh" file in the mounted Raspbian boot 
   partition with
   ```touch ssh```  
   Note: The mounted partition should be the working directory.

1. Create a "wpa_supplicant.conf" file in the same 
   directory containing (substituting your ssid/key pair):
   ```
   ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
   update_config=1
   country=US

   network={
	ssid="Your network SSID"
	psk="Your WPA/WPA2 security key"
	key_mgmt=WPA-PSK
   }
   ```
1. Unmount and remove SD Card from host computer.

### RasPi First Boot

1. Insert microSD card into RasPi slot

1. Connect RasPi to power source with cable.
  Observe activity on LED near power connector.

1. Upon booting RasPi can be found on LAN from host computer with
  ```ping -c2 rapsberrypi```

1. SSH into RasPi with
   ```ssh raspberrypi```
   user/password: pi/raspberry

1. Change default root password following prompts from
  ```passwd```

1. Update system software with
   ```sudo apt-get update; sudo apt-get upgrade```

1. Use ```sudo raspi-config``` to configure hostname and 
  other relevant options.

### Configure Python

### Install/Configure Flask

### Install/Configure Nginx

### Install/Configure UWSGI
