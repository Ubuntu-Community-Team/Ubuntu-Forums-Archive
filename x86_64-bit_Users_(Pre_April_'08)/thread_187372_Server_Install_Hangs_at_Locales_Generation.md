---
title: "Server Install Hangs at Locales Generation"
date: 2006-06-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by spamolamah on 2006-06-02
Hi, when I try a server install from the Kubuntu alternate disk, the computer hard locks at generating the locales. I have tried both the US and AU locales and get the same issue. If I watch the status console I can see a kernel panic occur at the configuring of the locales package.

Using the Kubuntu desktop live CD, my computer is fine until I type 'dpkg-reconfigure locales' at which point the system hard locks.

The computer is an 
Nforce4 AMD X2-4400
DFI SLI-D with latest bios (CPU errata fixes make no difference)
1GB ram (tested)
Nvidia Graphics
NForce Network
Nforce SATA controller

Everything is stable in the i386-k7 version and the AMD64 live CD until the locales-gen script is run. 

Thankyou in advance for any help and suggestions.

---

### Post by henriquemaia on 2006-06-04
[quote=spamolamah]Hi, when I try a server install from the Kubuntu alternate disk, the computer hard locks at generating the locales. I have tried both the US and AU locales and get the same issue. If I watch the status console I can see a kernel panic occur at the configuring of the locales package.

Using the Kubuntu desktop live CD, my computer is fine until I type 'dpkg-reconfigure locales' at which point the system hard locks.

The computer is an 
Nforce4 AMD X2-4400
DFI SLI-D with latest bios (CPU errata fixes make no difference)
1GB ram (tested)
Nvidia Graphics
NForce Network
Nforce SATA controller

Everything is stable in the i386-k7 version and the AMD64 live CD until the locales-gen script is run. 

Thankyou in advance for any help and suggestions.[/quote]

I had a problem similar to yours and this was due to a error in the burnt CD. Check the md5sum of the iso and if ok, burn the CD again at lowest speed possible for your recorder (just a hint). Maybe this helps.

---

### Post by spamolamah on 2006-06-06
Hi, thanks for replying! I have checked the md5sum and it is correct. I also burnt ubuntu server, desktop and alternate (and tried a minimal net install) and have exactly the same problem. When I use the desktop live CD everything is stable until I type 'dpkg-reconfigure locales', my system will then kernel panic and hang. I checked /var/log but nothing meaningful could be recovered. I will get a record of the kernel crash message.

There seems to be a related problem in [launchpad.net]("https://launchpad.net/distros/ubuntu/+source/belocs-locales-bin/+bug/25660") that also kernel panicked the machine. I believe my hardware is stable as I do not have crashes in any 32bit software or in Fedora Core5 AMD64.

---

### Post by henriquemaia on 2006-06-07
[quote=spamolamah]Hi, thanks for replying! I have checked the md5sum and it is correct. I also burnt ubuntu server, desktop and alternate (and tried a minimal net install) and have exactly the same problem. When I use the desktop live CD everything is stable until I type 'dpkg-reconfigure locales', my system will then kernel panic and hang. I checked /var/log but nothing meaningful could be recovered. I will get a record of the kernel crash message.

There seems to be a related problem in [launchpad.net]("https://launchpad.net/distros/ubuntu/+source/belocs-locales-bin/+bug/25660") that also kernel panicked the machine. I believe my hardware is stable as I do not have crashes in any 32bit software or in Fedora Core5 AMD64.[/quote] 
That's weird. If it happens consistently, it is a bug. I have tried this just now and I don't have any error.

Just as a side note: why are you running sudo dpkg-reconfigure locales? I ask this, because in Dapper this doesn't allow you to choose the locales to use (odd) in the Debian way. This command just re-generates the previously installed ones. To change your system locales, read more here:

[http://ubuntuforums.org/showpost.php?p=1109034&postcount=1](http://ubuntuforums.org/showpost.php?p=1109034&postcount=1)
[http://ubuntuforums.org/showpost.php?p=1057281&postcount=8]("http://ubuntuforums.org/showpost.php?p=1057281&postcount=8")

Hope this helps you.

---

### Post by spamolamah on 2006-06-08
Hi, thankyou for trying to replicate my problem, at least I know it's an isolated case now. The reason I regenerate the locales in the live CD is to duplicate the error using the text based installer. When I get time I will get a serial port dump of my kernel logs and try and get to the bottom of it. Thanks for your help so far, it's much appreciated!

---

