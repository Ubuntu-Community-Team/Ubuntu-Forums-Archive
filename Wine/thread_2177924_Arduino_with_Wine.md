---
title: "Arduino with Wine"
date: 2013-10-01
forum: Wine
---

### Post by chris130 on 2013-10-01
Hi all,

I'm still pretty new to Ubuntu (and linux) and I've been having trouble getting my ArduinoUno board to be 'seen' by the arduino software (which I'm running with Wine).  I'm running Ubuntu 12.04.3.

The arduino board shows up in Ubuntu as /dev/ttyACM0.  I've seem multiple forum post all over the web saying that all you have to do is create a symbolic link.  I've tried multiple ways of doing this to no avail. 

For those who are wondering why I don't install the linux version of arduino - I have a plotting program that only runs in Windows (I'm also using Wine for this) that also needs to be able to access the serial port of the Arduino.  Both software programs run fine, it's just that neither of them can actually connect with the board.

Any help would be greatly appreciated!

Chris

---

### Post by tgalati4 on 2013-10-01
I can't imagine any kind of plot that *gnuplot* can not handle.  Sure it has a learning curve, but it beats running WINE for something as simple as a plot.

It's possible that it is a permissions problem with the device.  Try changing the permission with *chmod* (755 or 777) to see if WINE can use it.  Please post the symbolic links that you have tried already.

---

### Post by chris130 on 2013-10-01
What I'm using, or trying to use is MakerPlot so that I can customize the visual interface and real-time monitor sensor values both in numerical and graphical form.  

I tried changing permissions by using chmod, but I don't know how to access the windows files to do it since it is in ~/home/.wine/dosdevices/c:/Program Files/Arduino/arduino.exe.  I can get to the c: folder, but can't figure out how to go further and use chmod on arduino.exe.  Although there is also a arduino.exe at /.wine/drive_c/Program Files/Arduino/arduino.exe.  From forum posts it looks like the one in the dos devices is correct, but I can be sure.  I ended up looking at the properties 

The links I have tried are:

*ln -s /dev/ttyACM0 ~/.wine/dosdevices/com1*  (I've also tried com2 and com3)
*ln -s /dev/ttyACM0 ~/.wine/dosdevices/c:/com1* (also tried com2 and com3)
*ln -s /dev/ttyACM0 ~/.wine/drive_c/com1 * (also 2 and 3)

---

### Post by tgalati4 on 2013-10-01
Change the permissions of the device files

```
sudo chmod 777 /dev/ttyACM0
```

I've only used an arduino in linux, so I can't really help further.

---

### Post by chris130 on 2013-10-01
Thank you!  That actually worked!  Now the arduino software is running and reading properly however the plotting software, MakerPlot is not.  My arduino is now com3 in Wine and I can connect to com3 just fine in MakerPlot (com3 is the only one it says isn't being used by another program). When I hit connect and try to start plotting in real time, the arduino seems to be connected, but MakerPlot is not actually plotting anything.  I don't get any error messages, but it isn't plotting anything.

I know my Arduino code is fine because it works correctly in the arduino software.

---

### Post by tgalati4 on 2013-10-01
My guess is that anything running under WINE does not have complete user privileges to access devices such as the serial port.  It's also possible that WINE does not allow two programs to access the same com port at the same time.  Does MakerPlot work without running the arduino software?

Another work around:  Run the linux version of the Arduino programmer, then only use MakerPlot under WINE.  This way you can monitor the Arduino's communications using the Arduino programmer in linux and use MakerPlot in WINE to view the results.  I would still find a replacement for MakerPlot.

Is there not a linux visual interface for the arduino that you could use?

A simple google search on *linux visual interface arduino* brings up a lot of hits including:

[http://www.instructables.com/id/Control-your-arduino-from-your-PC-with-the-Qt-Gui/](http://www.instructables.com/id/Control-your-arduino-from-your-PC-with-the-Qt-Gui/)

---

### Post by chris130 on 2013-10-01
MakerPlot still doesn't work even when the arduino software isn't running.  The main reason I want to use MakerPlot is that I had it working fine while I had Windows (meaning I have already purchased the MakerPlot software) and it was incredibly easy to work with and code for.  With the amount of time I've put into troubleshooting this maybe it is time that I give up and look for a linux visual interface as you suggested.   Thanks for your help.

---

### Post by tgalati4 on 2013-10-02
Ask the developers for a linux version of MakerPlot.  If it was written in Qt, then it might not be that difficult to port to linux.

---

