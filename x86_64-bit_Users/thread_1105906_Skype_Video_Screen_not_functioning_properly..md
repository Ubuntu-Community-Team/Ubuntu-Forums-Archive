---
title: "Skype Video Screen not functioning properly."
date: 2009-03-25
forum: x86 64-bit Users
---

### Post by suomalainen on 2009-03-25
Synopsis:

At issue is the Skype Video Screen. Currently it is unable to display live video streams. In two specidic instances, Skype is unable to stream live video feeds via webcam when:

1) In a live call and the "Start My Video" option has been selected
2) Under the "Video Devices" option a live video stream "TEST" cannot be successfully performed.

A work around has been discovered. However, it isn't a pratical method to follow. The Skype program itself should operate and perform flawlessly as intended.

It is hoped that through the epertise and knowledge of those here that the Skype Video Screen can be restored to its proper functionality.


Please consider the following:


Software/Hardware being used:
Linux-Ubuntu 8.04 LTS 64 bit
Skype version 2.0.0.72
Logitech QuickCam Chat   QC Chat 961462-0403
HP AMD model a500n Additional info available at:
[http://h10025.www1.hp.com/ewfrf/wc/product?product=405440&lc=en&cc=us&dlc=en&submit.y=0&submit.x=0&lang=en&cc=us](http://h10025.www1.hp.com/ewfrf/wc/product?product=405440&lc=en&cc=us&dlc=en&submit.y=0&submit.x=0&lang=en&cc=us)


Scenario 1

1. Applications ---> Internet ---> Skype
2. Right click on Skype icon in tool bar and choose: Options ---> Video Devices (See picture# 1)
3. Click on the "TEST" button over the black screen (See picture# 2")

IMPORTANT NOTE # 1:
At this point the "TEST" button disappears and the Skype test video screen remains black with no "live" video feed that can be seen.

IMPORTANT NOTE # 2:
If a Skype contact is online a call can be placed to that contact. However, When "Start My Video" is chosen a live video feed does not appear in the lower left hand corner of the Skype video screen. However, a live Skype video feed is being transmitted "live" from Skype to the Contacts computer although that live video feed isn't being properly displayed. THIS FEATURE NEEDS TO WORK SO THAT THE CALLER CAN POSITION THE WEBCAM CORRECTLY DURING A CALL.

4. Right click on Skype icon in tool bar and choose: Quit


Scenario 2

1. Applications ---> Internet ---> Skype
2. Applications ---> Sound & Video ---> TVtime Television Viewer
3. Set TVtime Television Viewer volume to zero (0).

ABOUT TVtime Television Viewer:
tvtime is a high quality television application for use with video capture cards on Linux systems. tvtime processes the input from a capture card and displays it on a computer monitor or projector. See: [http://tvtime.sourceforge.net/](http://tvtime.sourceforge.net/)

4. Go to Skype
5. Look for an online contact and make a call to that contact
6. Select "Start My Video"
7. A "live" Skype video feed appears on both the Contacts computer and the computer of the person originating the call. 

IMPORTANT NOTE # 3:
Within the Skype video screen appears both the contacts live video feed and the smaller video of the caller in the bottom left hand corner.

8. End the call with the contact
9. Right click on Skype icon in tool bar and choose: Options ---> Video Devices (See picture# 1)
10. Click on the "TEST" button over the black screen (See picture# 2")
11. Live "TEST" video stream appears (See picture# 3)


Scenario 3

1. Applications ---> Accesories ---> Terminal
2. Enter the following: gstreamer-properties
3. Terminal reports the following, see below, as the Multimedia Systems Selector program opens:

desk@desk-desktop:~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
desk@desk-desktop:~$

4. Pictures 4 & 5 show the settings of the Multimedia Systems Selector program.


Scenario 4

1. Applications ---> Accesories ---> Terminal
2. Enter the following: lsusb
3. Terminal reports the following:

desk@desk-desktop:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 046d:08af Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000
desk@desk-desktop:~$

---

