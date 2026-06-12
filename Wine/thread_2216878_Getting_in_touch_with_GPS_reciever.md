---
title: "Getting in touch with GPS reciever"
date: 2014-04-14
forum: Wine
---

### Post by Ulf_Hegelund on 2014-04-14
I have installed the SeaClear navigation software under Wine. It runs fine and is great for planning routes. However I cannot get it to see my GPS reciever, Navibe GM720. Do I load a windows driver under Wine, or is there any other way to use a Windows driver? Is there any Linux software that I could use?

---

### Post by ian-weisser on 2014-04-14
> **Ulf_Hegelund said:**
> Do I load a windows driver under Wine, or is there any other way to use a Windows driver?

No and no. Windows drivers only work Windows with hardware. Your interface is handled by Linux - the Windows drivers don't speak Linux.

Sorry, I'm not familar with that model or it's requirements.
There are many GPS applications in Software Center that are free to try.
Please test a few - if one works, please post so other owners of the same hardware can benefit.
Does the manufacturer have any Linux recommendations?

---

### Post by Ulf_Hegelund on 2014-04-15
Navibes webpage seems to be down. I have downloaded the windows drivers from a third party, just to save what can be saved. I will take a look on what is availlable in the software center and repost if i find anything useable. thanks for the feedback.

---

### Post by Ulf_Hegelund on 2014-04-15
Just made a dedicated search for this device and came up with this hit: [http://home.zyrianes.net/blog/Articles/158/](http://home.zyrianes.net/blog/Articles/158/) 

Looks interestng. I will try it out when i come home again. Then, actually I am planning to have the setup on my old HP netbook and install Puppylinux on it. Hope it will work under Puppy as well, it being a tad leaner than Ubuntu.

---

### Post by Ulf_Hegelund on 2014-04-17
Tme for a progress report. 

I installed the gpsd and the gpsd-clients packages on my Puppy box. After some running gpsd /dev/ttyUSB0 and starting Seaclear under wine Seaclear no longe complained about "Unable to open device on port0". But did not display any data recieved. 

Played around with the console client sirfmon only to discover that it no linger seem to be part of the gpsd package. Fired up xgps, still no display of data recieved. 

Played around some more. Disconnected reciever restarted gpsd with the -b option, yes, i studied the manpage, reconnected, fired up xgps and......... (fanfare) Data and an accurate position. :-)

Back to SeaClear, still no position. Playing around with the commsettings does not seem to help. I read somewhere that the reciever had a habit of defaulting to a speed of 9600 bps instead of the speccified 4800 bps. but none of these settings do me any good. 

Right now i am way beyond my comfort zone, but I will try and summarize what i have. dgps is up and running, communicating with the reciever, and happily distributing position data across the system. dgps have three ways of sharing data, the socket interfae, shared memory and the Dbus interface. SeaClear have one way of communicating, over a serial interface. It have been lead to believ it have a serial device on port0 to work with, but does not seem to be able to do anything with it. Between the two is Wine, and I have absolutely no clue as to what might go wrong here. 

Right now I have three ideas. 
1. play around with the commsettings in SeaClear after sigging up the socumentation or the reciever. I dont have much faith in this.
2. SeaClear expect an NMEA packet and gpsd distributes an raw binary stream from the Sirfchip. Then again, for that theory to work the windows driver for the device must do that translation because the setup works fine on a windows box. If this is the problem, can I set gpsd to send NMEA packet?
3. It is all the fault of Wine. Here i have absolutely no cle as what to do next :-(

Oh, by the way. Yes I know I am talking Puppy in an Ubuntu forum. But in an attemt not to be offensive, Puppy is Ubuntu based. And, whatever I might learn is probably of interest to more than myself and may attract som interest an inspire converts in the SeaClear Yahoo group.

---

