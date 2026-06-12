---
title: "Garmin 301 forerunner"
date: 2007-07-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by ivt on 2007-07-10
Hi 

I have a Garmin 301 forerunner, I will describe the searching and process I have undergone to date

grmnusb.inf and .sys installed under ndiswrapper

I have the following output from ndiswrapper -l
[I]
grmnusb : driver installed
        device (091E:0003) present (alternate driver: garmin_gps)[/I]
[I]
gpsbabel -i garmin_txt -f /dev/ttyUSB0 -o kml,lines=0 -F /home/iainvt/one.kml[/I]

hangs or produces a .kml with the 3 standard worlwide Garmin headoffice locations

I have tried the options described here 
[I]
[http://ubuntuforums.org/showthread.php?t=457115&highlight=garmin_gps](http://ubuntuforums.org/showthread.php?t=457115&highlight=garmin_gps)[/I]

however this results in 

[I][ERROR] XSERIAL: Cannot open serial port '/dev/ttyUSB0': 6#D&#65533;No such file or directory
[ERROR] Cannot open serial port '/dev/ttyUSB0'
GARMIN:Can't init /dev/ttyUSB0[/I]

So I deleted these out, so to date I have a Garmin 301 forerunner that is recognised and driver working but no way of getting the .kml data for google earth

any thoughts?

---

