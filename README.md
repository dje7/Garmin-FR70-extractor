Garmin-FR70-extractor
=====================

Garmin FR70 extractor on Linux (Mint XFCE)
I'm not sure if this is accurate or not. This is my first experience
with linux and this is close to my first experience with any type of 
computer programming. I am trying to get a USB 2.0 ANT stick for my
Garmin FR70 watch to work with Linux. I have read the items in TIGGE's
Garmin-Forerunner-610-Extractor repository.



Requirements
==============================================================================

- PyUSB 1.0 (seems to be a bug which makes it segfaults on version before
  Alpha 2). It is recommended to use pip to install PyUSB:
  
  pip install pyusb

- Install udev rules (recommended). This is only needed if you want to avoid
  running the program as root. Install with:

  sudo cp resources/ant-usbstick2.rules /etc/udev/rules.d

Supported devices
==============================================================================

Any compliant ANT-FS device should in theory work. Users of these device have
been able to download data of their watches:

 - Garmin FR70

It's possible that other manufactures using ANT+/ANT-FS, such as Suunto and
Timex might work, but have *never* been tested as far as I know. Please let
me know if you have any success with devices that are not listed here.

Usage
==============================================================================

Usage: python garmin.py

This program extracts all activity FIT files from a device and writes them
to a folder (see file locations below). The first time it runs it attempts
to sync with the watch. This produces an authfile which is written to the
same folder. On startup this program will try to read that file to avoid
having to re-sync.

File locations
==============================================================================

Simple answer (probably correct for most people):

 - Your files are placed in ~/.config/garmin-extractor/

Correct answer:

 - FIT files and authfiles are stored in an the location specified by the XDG
   Base Directory specification. It uses the $XDG_CONFIG_HOME with
   $HOME/.config as backup. In this directory a garmin-extractor folder is
   created in which a folder for each device is created. Both the .FIT files
   and authfile are stored in this device-specific folder.

