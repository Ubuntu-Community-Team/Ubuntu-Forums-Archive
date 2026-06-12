---
title: "64bit drivers"
date: 2007-08-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by will71110 on 2007-08-15
I just installed Ubuntu 7.04 64bit for an AMD64 cpu.  Does this mean that I can only installe 64bit drives and that the 32bit drivers will not work?

---

### Post by Kilz on 2007-08-15
> **will71110 said:**
> I just installed Ubuntu 7.04 64bit for an AMD64 cpu.  Does this mean that I can only installe 64bit drives and that the 32bit drivers will not work?

As far as I understand that is correct, Exactly what drivers are you looking to find?

---

### Post by will71110 on 2007-08-15
Well I have a ferrari 4000 and my blueooth, WIFI and card reader does not work.  Maybe more but I havent tested it all.

EDIT:

Also I have a Plextor PX-TV402U I'd like to install.

---

### Post by John.Michael.Kane on 2007-08-15
> **will71110 said:**
> Well I have a ferrari 4000 and my blueooth, WIFI and card reader does not work. 
You will have to find out who the makers are of your blue-tooth/Wifi/cardreader, and if the kernel has found them.

You can check to find out if your blue-tooth is found by running the command below in the terminal
```
hcitool dev
```

You can check to find out if your Wifi is found by running the command below in the terminal
```
lspci -v | less
```

You can check to find out if your cardreader is found by running the command below in the terminal
```
lspci
```

Further reading:
Explains what wifi cards are supported, and gives the command to find out.
[WirelessCardsSupported]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported?highlight=%28wifi%29")

Explains how to get your wifi working.
[WiFiHowTo]("https://help.ubuntu.com/community/WifiDocs/WiFiHowTo?highlight=%28wifi%29")

For blue tooth.
["blue tooth"]("https://help.ubuntu.com/community/?action=fullsearch&context=180&value=blue+tooth&titlesearch=Titles")

> **will71110 said:**
> Also I have a Plextor PX-TV402U I'd like to install.
Heres a guide for that device.
[WIS Go7007 Linux driver]("http://nikosapi.org/nikosapi.org/wiki/index.php?title=WIS_Go7007_Linux_driver")

Hope this helps.

---

### Post by will71110 on 2007-08-16
Ok here is what I found out using those stepts...

The WIFI is found but I cant turn it on.  my Laptop has one of those buttons that you push to turn it on.  It lights up amber when is is on.  Does nothing when I push it.

Bluetooth does not show up when I use the command above but it showes up in my hardware infomation in GUI.  Also just like the WIFI,  it has a button to turn it off and on.

Cardreader does show up but does nothing then I insert a card.

The WiS go7007 drivers dont say if they do or dont support 64bit.

I'll do some further reading on the links you sent me too.

LOL below.  Dont know how that's possible???

> **SD-Plissken said:**
> 
Explains how to get your wife working.
[WiFiHowTo]("https://help.ubuntu.com/community/WifiDocs/WiFiHowTo?highlight=%28wifi%29")
.

---

### Post by will71110 on 2007-08-16
Well it looks like I have the WIFI drivers but I cant get the amber light to turn on?  Could it be working even though that is off?  Is there a way to scan for an SSID to test?  There isnt a way in GUI unless I'm missing something. 

EDIT: (Looks like I might have to run Ndiswrapper but cant since I have lost internet at home)

---

