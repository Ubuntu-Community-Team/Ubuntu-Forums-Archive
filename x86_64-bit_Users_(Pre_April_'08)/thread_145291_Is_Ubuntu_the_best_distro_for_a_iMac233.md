---
title: "Is Ubuntu the best distro for a iMac233?"
date: 2006-03-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by PsychoSync on 2006-03-16
There is a lot of linux distributions for PPC, i'm tired of running MacOS 9, its slow and i don't think OSX would be any better on a 233 Mac! What my question really is, is: What's the best linux distribution for a iMac 233 with 64 megs of RAM? 

Other question: If Ubuntu or any other PPC distro can run on G5, is it also optimized for an old Mac, i don't know how express this well... For me, it's like running Windows XP on Pentium 233.

---

### Post by ssam on 2006-03-16
if you want a graphic user interface you will need some more RAM, atleast 128 for a lightweight window manager, but more like 256 for gnome. this should not cost very much. (it may also make mac os run faster)

i'd say ubuntu would be a very good choice, i have used yellowdog (a fedora derivitive) in the past but found ubuntu much better. ubuntu has very upto date software (especially if you can wait until dapper drake is released (most likely preview on april 20, and final on june 1)). recently linux has become much more userfriendly and gained lots of optimisation work, so there is a big difference between upto date and year old software.

processor optimisation tend to only make a few percent deifference, far less than using lightweight programs, updrading RAM, and developers making programs faster. ubuntu is not particularly optimised for G4s or G5s appart from there being an optional G5 optimised kernel and some optimised for altivec media players.

---

### Post by 3rdalbum on 2006-03-17
Ubuntu will be slower than OS 9, but that's because Ubuntu has to have all the modern features that are missing from OS 9. Also, Linux allocates system resources more "fairly" than OS 9, so some programs will feel slower.

You'll need at least 128 megs of RAM, and even then it'll be about as slow as OS X... slower at startup and shutdown. If you're going to use Ubuntu seriously, you'd need to max out your machine to 256 megs and put a bigger hard disk in it.

---

### Post by PsychoSync on 2006-03-17
Well i ordered a 128m ram and in 4 days i'm gonna have the maximum a rev-B iMac can have : 192m. And i have a Maxtor 40g 7200rpm that is sleeping in the closet so putting that in should help too... One question though... Would it be faster with Ubuntu 4.10 (Warty) than 5.10 (Breazy) considering that Warty is 2 years older sop it might be easyer to run?

---

### Post by jdp on 2006-03-17
Runnign old Linux releases is not like running old Mac OS.  Old Linux releases tend to be old.  New releases contain bug fixes and better hardware support.  Typically, you'd run an old Mac OS because it still supports old hardware without too much bloat.  Under Linux you can configure everything you want to the point that any bloat you don't want is gone.

So, no, running Warty isn't a great idea.  Esp. since it will be dropped from the update support cycle before long.

Breezy does have a few issues, esp. on iMacs, but once you get around them, it's pretty good.  It's almost always recommended to keep up with a stable Linux distro, because they tend to always get better, and they are free.  Mac OS X only gets one of those points going for it. ;)

---

### Post by spaceballl on 2006-03-18
You only ordered 128mb more? Old ram is so cheap you probably should have bought a 256mb stick. Well actually, I'd reccommend buying a 256mb stick of ram and getting rid of your old 64mb so you have a total of 384mb.

Getting back to the functionality, I'd say ubuntu is a good choice. It's very easy to set up. However, once you get the basic system set up. You'll find the UI rather slow with that processor so you can use a more lightweight environment like XFCE, maybe even something faster/lighter. Just use the Dapper Flight 5 CD to install and once its set up, come back and let us know how performance is and we'll help you get a better window manager installed.

-Kevin

---

### Post by arctic on 2006-03-18
Just one note: OSX will not run on a 233 Mhz iMac, according to Apple. Minimum requirements: G4 Processors and 256 MB Ram

---

### Post by PsychoSync on 2006-03-18
to spaceball: I don't think the iMac 233 can have more than 192m RAM... 

and, eventually i will try Dapper like you said but right now, i really don't have the time...work... 

OSX can run on a iMac 233 with some hacks i believe...

---

### Post by spangemonkee on 2006-03-18
[QUOTE=PsychoSync]to spaceball: I don't think the iMac 233 can have more than 192m RAM... 

and, eventually i will try Dapper like you said but right now, i really don't have the time...work... 

OSX can run on a iMac 233 with some hacks i believe...[/QUOTE]

I have ubuntu on my iMac 350 with 384mb of RAM and it runs fine. I just hate the lack of decent Flash support.

OSX 10.3.x is officially supported on the iMac 233 and [XPostFacto]("http://eshop.macsales.com/OSXCenter/XPostFacto/") can help you get OSX 10.4.x installed on that machine. 

You will need to make sure you have the latest and greatest firmware installed under OS9 *before* you try an upgrade. Especially to Jaguar.

The max mem is 384 (1x256, 1x128).

[More info on the iMac 233.]("http://www.lowendmac.com/imacs/imac-b.shtml")

---

### Post by grazie on 2006-03-19
I doubt any Linux distro will impove on OS9 for performance, but you will get a lot more funtionality and security.

I don't think you've got that many options for mature PPC Linux distros. I'd say Ubuntu, Gentoo or Yellow Dog. The standard Ubuntu install is going to be slow on your machine. You could do a server install followed by a window manager of choice. XFCE seems popular on Ubuntu and has an easy install path. Fluxbox or similar will give your more speed, but the installation is not so well documented. A lot of people are put off by Gentoo by having to install everthing from source, but it's very well documented. So long as you don't try to build big applications like KDE, Gnome or OpenOffice (which would be silly on your machine), it wouldn't take too long either. Many of the big applications are available pre-built anyway. However, Gentoo isn't for anyone who isn't interested in 'messing around' with the OS. Can't comment on Yellow Dog, as it didn't appeal to me.

---

### Post by theturner on 2006-03-19
I'm running Dapper on a PowerBook G3 250 MHz. It isn't as snappy as Mac OS 8, but it's very usable. The system has 256 MB  RAM, and I think that is the key here, but 192 MB might as well be enough.
As people before me already mentioned, running old releases isn't a good idea, and Dapper (6.06) has improved a lot on Breezy regarding responsiveness and memory usage, so just use Flight 5, it's already very stable.
Note that resizing HFS+ partitions to make space for Linux can be a little tricky, but if it isn't a journaled filesystem (I think only OS X does journaling), you can do it from the Ubuntu Installer.

---

### Post by Lanrond on 2006-03-20
[QUOTE=arctic]Just one note: OSX will not run on a 233 Mhz iMac, according to Apple. Minimum requirements: G4 Processors and 256 MB Ram[/QUOTE]

Not completely true.
OSX runs on G3 processors quite easely (even if not so quickly), provided at least 512 Mb of RAM (1G is better) and a firewire interface; I think they are the ones released from 1999 onward...

---

### Post by jdp on 2006-03-20
We should point out the sub-version of OS X is what matters to if it will install with orr without FW ports.  Up to OS X 10.2.8, most factory G3+ Macs have official support.  The Kanga G3 PowerBook (3500) isn' supported for OS X.   10.3 needed factory USB Macs to install, so the Beige G3 is not officially supported, nor is the G3 Series (WallStreet).  10.4 requires factory FireWire, so trayload iMacs and the Lombard are now out of official support.  Everything with a factory FireWire port should be fully suppored under 10.4.

Just make sure you still check for the updated firmware in iMacs **before** any OS X install is even attempted.  If you attempt to booot an OS X disc on a non-updated iMac, you maybe SOL without knowing the proper recovery methods.  Update to at least 9.1 on the HDD, dot he FW update, then do the OS X install.

---

