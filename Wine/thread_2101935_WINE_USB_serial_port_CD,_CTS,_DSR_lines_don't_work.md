---
title: "WINE USB serial port CD, CTS, DSR lines don't work"
date: 2013-01-05
forum: Wine
---

### Post by rattskjelke on 2013-01-05
I dual boot Xubuntu 12.10 64 bit and Windows 7 Home 64 bit and I'm trying to get a USB serial port to work properly with a 2-way radio VoIP program under WINE.

It uses a serial port's RTS or DTR lines to key the radio and the CD, CTS or DSR lines for the COS input.

Xubuntu recognizes the USB serial port. I linked ttyUSB0 to the ~/.wine/dosdevices folder and set the permissions so it will work with WINE. The port sends and receives data and the RTS and DTR lines work but the CD, CTS and DSR lines don't work.

I can't tell if the problem is with WINE or Xubuntu. The same hardware works properly on the same PC when running Windows 7. I don't have another PC to try it on.

Anybody know how I can fix this?

---

### Post by rattskjelke on 2013-06-01
I tried this again using Xubuntu 13.04 AMD 64-bit and LinuxMint 15 MATE 64-bit with the exact same results.

---

### Post by kojo on 2013-06-24
When I ran a DSTAR Satoshi hotspot on linux I used a virtualbox ( [http://www.virtualbox.org](http://www.virtualbox.org) ) to host an XP environment.  You can even export your current Windows partition image file and boot it up in a virtual system.  I found this worked very well.  You might be pushing it trying to use WINE for this application.  Are you trying to build a DSTAR system?  Echolink?

You might find more help at the following yahoo groups:
pcrepeatercontroller
gmsk_dv_node

---

### Post by rattskjelke on 2013-07-05
I just want to run my EchoLink node on Linux. It is one of the things I need to do to be able to dump Windows completely but I can't because there are no Linux applications for stuff like EchoLink and two-way radio/scanner programming.

I tried VirturalBox before to multi boot other linux distros but I have a low end laptop that is too slow and doesn't have enough memory to run VirtualBox well. I also had problems trying to get other applications to run properly under WINE.

It sucks when Windows just works and Linux doesn't.

---

### Post by rattskjelke on 2014-04-18
This problem was fixed in WINE version 1.7.

---

