---
title: "Live Hoary on iMac G3 ?"
date: 2006-03-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by slink on 2006-03-30
Hello 

I just burnt the Hoary Live CD ( [http://us.releases.ubuntu.com/releases/5.04/ubuntu-5.04-live-powerpc.iso](http://us.releases.ubuntu.com/releases/5.04/ubuntu-5.04-live-powerpc.iso) ) and tried to boot (pressing "C") but nothing happened. It runs on G3 macs but I am not sure if it can on an iMac G3. 

Does anyone know if PowerPC live CD 5.04 can boot on an iMac G3 ?

Thanks

---

### Post by daWabbit on 2006-03-30
I have seen it running on an early iMac, both live and installed. There is a 4 key combination one needs to hold down in order to boot from the CDROM. I am not sure I recall correctly, but I think it is control+special key+shift+delete. Are you doing this?

---

### Post by 3rdalbum on 2006-03-30
Holding down the C key should work. Does the drive sound like it's struggling to read the disc? If so, you should try burning to more expensive media, or ordering through ShipIt.

If the disc reads fine in the Mac Finder, and there's just one file on it, then you've burnt the disc incorrectly. Use the Disc Image function of Toast to burn the ISO to CD.

---

### Post by slink on 2006-03-31
Well, I tried SHIFT+OPT+CMD+DEL. The boot sequence lasted about 5 minutes but OSX loaded at the end. What more can I try?

- I'll try holding OPT to see if it gives me any options menu

- I'll burn again the CD, at 1x on Windows ( burning on mac creates DesktopDB and DesktopDF files, they could be the problem )

---

### Post by slink on 2006-03-31
I'll try all this on Dapper Live CD

---

### Post by jdp on 2006-04-01
If it's a first gen iMac, it may have trouble booting from burned discs.  There's threads galore here about that.  Also, first gen (trayload) iMacs don't have the Option key boot menu (Startup Manager) only slot-load and later do.  It's most likely the issue with burned media.  I've booted several tray-load iMacs with official pressed ShipIt CDs of 5.04 or 5.10.

---

### Post by Is'lan on 2006-04-01
When I was trying to install Gentoo on my OldWorld G3, I had to use BootX to bootstrap into a Linux environment.  Still I have yet to successfully install it, though.. ](*,)

---

### Post by jdp on 2006-04-02
The Beige G3 and the WallStreet were the end of the OldWorld line.  Anything in multicolor (ie, B&W G3, iMac, iBook) and the Lombard on up are NewWorld.  More distinct is: anything with a factory USB port is NewWorld.  Everything else is OldWorld.

BootX is still needed for almost any OldWorld machine unless you want to play around with some of the other mostly unsupported bootloaders.  EMILE still has development and may eventually work on PPC.  Most others seem to be abandoned, even BootX.

---

### Post by slink on 2006-04-04
I burned again the Live Cd, this time on a better quality media, at minimum speed (8x) on Windows. I don't know if it was because the better media or the fact that Windows does not include visible DesktopDB and DesktopDF files, but it ran well, could log to Ubuntu and I was very pleased. 


I assume that any iMac is New Word, an so I don't need BootX. 


I also assume that only C-key is needed to boot wit CDROM. 


Thanks for the hints!

---

### Post by 3rdalbum on 2006-04-04
Glad to hear that it's working for you now. I think the problem was that you were incorrectly burning the ISO file on the Mac. (If you burn it correctly, the Mac won't add Desktop files to the CD).

---

### Post by slink on 2006-04-04
I agree with you, 3rdalbum, and I'm very pleased with my first cup of Ubuntu. 

Now I'm going to try a few days and if everything goes well I'll install Dapper on my iMac. In the meantime I'll learn about partitioning, yaboot, install process...

---

