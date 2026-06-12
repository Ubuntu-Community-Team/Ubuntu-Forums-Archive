---
title: "Serial Ports, specialty software, and WINE"
date: 2018-11-23
forum: Wine
---

### Post by timfinley on 2018-11-23
So I'm trying use this piece of software called SiController for the Circuit Werkes Sicon-8 device. I would like to install it on Linux as it is a far more robust and reliable system than Windows. The problem I'm having is with the serial port. 

(Side note, I had to use winetricks to install vb6run in order to get the software to install.)

At first, I was unable to connect to the serial port at all. After some research, I've added my user to the dialout group. I still couldn't see the serial port using the R-232 jack, but the device comes with a serial -> USB converter on board. So I decided to use the USB connection. 

I was able to connect the software to the USB type connector using 

```
dmesg | grep tty
```
```
wine regedit
```
Set the port in HKEY_LOCAL_MACHINE\Software\Wine\Ports by creating a new string and setting its name to COM1 and the value to /dev/ttyUSB0 - Then I ran
```
wineserver -k
```

Now the program loads, but has trouble connecting to the device. In fact, that's where it freezes. So I figured it probably has something to do with baud rate. I set the baud rate to 38400:
```
stty -F /dev/ttyUSB0 38400
```
since this is the default baud rate on the the software. 

I have also attempted to install the proprietary USB to Serial drivers that the device uses. They're called ftdi, and it replaces ftdi_sio and usbserial. Problem is is when I follow the instructions and disable the drivers, I can no longer find the USB Serial device to create a registry setting in Wine:
```
sudo rmmod ftdio_sio
```
```
sudo rmmod usbserial
```

So I figure that's probably not going to work. Uninstall the drivers and I'm back at square one. The program freezes as it's trying to connect. 

Any further information can be provided if needed. Could really use some help solving this issue. I'm pretty green when it comes to serial and parallel ports. So I'm hoping I could find some help here.

---

### Post by timfinley on 2018-11-26
*UPDATE*

I was able to get the serial port to work, at least somewhat. I discovered that the serial port must be enabled in the bios. My machine has two COM ports and a Parallel port in the BIOS. However, there is only one physical COM port and one physical parallel port (unless I'm missing something). I enabled one and tried to connect via serial port. The software is still unable to connect to it. It threw an error saying that I had to ensure that the baud rate is correct as well as have it set to 8-n-1 (8 bits, no parity bit, 1 stop bit). After some searching, I found that I can configure the port in this way by issuing ```
stty -F /dev/ttyS0 38400 cs8 -cstopb -parenb
```. Still no dice. At least the software isn't freezing still. I then tried going back to BIOS, disabling the first COM port, and enabling the second COM port. I ran the ```
stty
``` code again, but still no dice. 
[
Any advice would be very useful. Thank you.

---

### Post by rattskjelke on 2018-11-26
What version of WINE are you using? I had serial port problems a long time ago.
Before v 1.8 some of the non-data lines (CTS, RTS, etc.) did not work.
In v 2.8 they changed how serial and parallel ports work.
In case you have not already found it see [https://wiki.winehq.org/index.php?title=Wine_User%27s_Guide&oldid=2519#Serial_and_Parallel_Ports](https://wiki.winehq.org/index.php?title=Wine_User%27s_Guide&oldid=2519#Serial_and_Parallel_Ports). I had to make a registry key to make a USB serial port work. I don't know if that applies in your case.

---

### Post by timfinley on 2018-12-16
Yeah, I had seen that post already. I'm really not sure why it's not working, but I've decided to abandon the project.

---

### Post by timfinley on 2018-12-20
I was still curious about this, so I called the manufacturer of the device. Turns out their developers were trying to do the same thing some 10 years ago and ran into the same wall. I spoke with the owner of the company and he mentioned that it had something to do with the layer between the app running in linux via wine and the com port. Be it serial or USB to serial, it's because of the naming scheme, i.e. ttySx versus the windows naming scheme COMx. 

He said that they too had given up on the project all those years ago and was really foggy with the details. If anyone has any ideas, I'd be stoked. 

The software is written in Visual Basic 6, and is a 32-bit program. That might help with any Linux/Wine gurus....

---

### Post by dacha on 2019-03-29
Still interested in getting your application to work? I have considerable Wine development experience and am interesting in helping.

Firstly try running your application from a terminal with serial port debugging enabled:

```
WINEDEBUG=+comm wine app.exe | tee /tmp/log.txt
```
(from the right directory, replacing app.exe with your application's name)

which might reveal some problems. If not, attach that file (/tmp/log.txt) here so I can have a look and let you know what else to try.

Wine's serial port code is mostly in [https://github.com/wine-mirror/wine/blob/master/dlls/ntdll/serial.c](https://github.com/wine-mirror/wine/blob/master/dlls/ntdll/serial.c)

---

