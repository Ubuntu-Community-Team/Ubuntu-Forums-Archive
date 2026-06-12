---
title: "epson scanner:  error during device I/O"
date: 2007-03-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by unsanity on 2007-03-17
Finally got Ubunto 6.10 64bit to work on my brand new HP Pavillion Media Center AMD 64 4600 and everything seems to work except my Epson Perfection 2450 scanner which is plugged into a usb2 port.
The epson printer that I have plugged into another usb2 port is fine.
Xsane searches and gives me a choice between a noname dev/video0 and a Epson 9700 at libusb:002:006.
I select the Epson and after a while I get the message: xsane failed to start scanner error during device I/O.
The scanner works fine in windows and on my old computer with Ubunto 6.06 LTS (but only on usb 1).
I've tried to read:confused:  the Sane and USB site but I am a newbie at this linux game and have got myself thoroughly confused, I have downloaded libsane-extras to no avail, same error message.
Any help would be appreciated.

---

### Post by kleeman on 2007-03-17
You may need iscan. See this page:

[http://www.epson.com/cgi-bin/Store/support/supDetail.jsp?BV_UseBVCookie=yes&infoType=News&oid=25021&prodoid=35836301&noteoid=38581](http://www.epson.com/cgi-bin/Store/support/supDetail.jsp?BV_UseBVCookie=yes&infoType=News&oid=25021&prodoid=35836301&noteoid=38581)

---

### Post by unsanity on 2007-03-18
Thanks for the tip,
I've been on this road before when I was in the same fix with PCLinuxOS only now I notice that Sane has to be a tarball install as well. 
I'll give it a try as soon as I figure out how to install tarballs again.

---

### Post by unsanity on 2007-03-19
I tried to install sane and iscan with tarballs and rpm but the scanner still won't work.
I'm going to get a firewire cable tomorrow and try that. I suspect it's more to do with usb2 controllers and scanners than anything else because all my other usb2 devices work fine.

---

### Post by unsanity on 2007-03-20
OK. I got a firewire and now I can scan in "sudo xsane" mode. At least that's a step forward, I've been banging my head for 3 days now.
I'll figure out the rest later.
Still got to get my wifi card activated.

---

### Post by kolslorr on 2007-03-25
sudo chmod a+rw /proc/bus/usb/*/*

I ran this command at terminal, and it works fine now. :)

---

### Post by Haegin on 2007-06-10
On any version of Ubuntu later than 6.06 you need to look into the udev file for sane to make sure that permission to use your scanner is given to the scanner group when your system detects it.

---

