---
title: "Linksys Wireless not working"
date: 2006-10-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by briander43 on 2006-10-14
I have a Linksys WMP54G4 wireless card installed on a Gateway AMD64, and it appears to be detected as ra0. But when I enable it, provide the info asked for in the interface properties dialog, I still can't connect to the internet even though I can see packets transmitted and received (very little however) in the Network tools dialog. The interface information is also "not available".

What's worse, if I restart the computer, it locks up when detecting network interfaces, and I have to reinstall Dapper.

I've attempted to use ndiswrapper with the windows version of the .inf file for my card, but when I do ndiswrapper -l, it lists the card but states it's invalid.

I've also attempted to download and compile the ralink drivers from the ralink site, but I run into a problem when attempting to compile the kernal (2.6.15-23) (something about "slot" something or other and the compile fails).

I've also attempted to install network manager via the Add/Remove Applications dialog, but it states it's "not available in any software channel."

Could someone please guide me down the right path to get this working?](*,)

Brian

---

### Post by wieman01 on 2006-10-14
> **briander43 said:**
> I've also attempted to download and compile the ralink drivers from the ralink site, but I run into a problem when attempting to compile the kernal (2.6.15-23) (something about "slot" something or other and the compile fails).
Common problem... When you deploy *.INF while all other driver files are not in the same folder (e.g. *.SYS, *.CAB, etc.), it will fail. "ndiswrapper" needs all files and will copy them to another directory.

_**EDIT:**_
You also need to blacklist the native Windows driver for Ralink:
> echo 'blacklist [COLOR="Red"]rt2xxx[/COLOR]' | sudo tee -a /etc/modprobe.d/blacklist
[COLOR="Red"]rt2xxx[/COLOR] stands for the version of your Linux Ralink driver.

---

### Post by briander43 on 2006-10-15
I think I have it partially configured. I'm now able to see my card in the Network Tools dialog (the mac address is showing - progress!).  But I'm still unable to see my router - when I ping it, it fails. Am I still not configured properly? What else do I need to do to make this work?

---

### Post by basementgeek on 2006-10-15
I've had similar issues with my linksys wirelss pci card ](*,) .  Sure hope you have better luck than me!  Then I'll steal shamelessly :)

---

### Post by wieman01 on 2006-10-15
Ok, please run these commands & post the output if possible (copy the text on to USB device and paste it):
> sudo gedit /etc/network/interfaces
> ifconfig
> iwconfig
> iwlist scan
> sudo /etc/init.d/networking restart
> route
That'll tell us what's going on with your network. "ndiswrapper" is definitely the right way to go.

---

