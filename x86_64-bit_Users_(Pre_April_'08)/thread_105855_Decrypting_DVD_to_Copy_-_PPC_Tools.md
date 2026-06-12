---
title: "Decrypting DVD to Copy - PPC Tools?"
date: 2005-12-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by MonolithTMA on 2005-12-19
Good morning all.

I have a few DVDs that are out of print, and I would like to make backup copies of them, but they are encrypted. I see lots of tools that require WINE and DVD Shrink for Windows. Are there any methods that will work on a PPC install of Ubuntu? Thanks! :)

---

### Post by pvz on 2005-12-19
[QUOTE=MonolithTMA] Are there any methods that will work on a PPC install of Ubuntu? Thanks! :)[/QUOTE]
If you have the multiverse repositories enabled in your /etc/apt/sources.list, you can do
```
sudo apt-get install dvdrip subtitleripper
```
and it will install the necessary packages for you. Launch with dvdrip from a terminal.

---

### Post by MonolithTMA on 2005-12-19
[QUOTE=pvz]If you have the multiverse repositories enabled in your /etc/apt/sources.list, you can do
```
sudo apt-get install dvdrip subtitleripper
```
and it will install the necessary packages for you. Launch with dvdrip from a terminal.[/QUOTE]

Terrific! I'll try it when I get home!

Thanks! :D

---

### Post by dietrying on 2005-12-19
installation of dvdrip works on ppc but it's not usable: when i start it, i get a window where it says that the librarie wich dvdrip depends on are not installed: transcode and so on. But i installed all of this packages. I didn't ind out where to configure that, so if someone finds out, please tell me.
greetings -

David

---

### Post by MonolithTMA on 2005-12-19
That sounds familiar. I may have tried that one already. I will check it out once I get home and post my results.

---

### Post by pvz on 2005-12-19
Try switching NPTL on/off in Preferences/Miscellaneous options. I'm using a self-compiled 0.97.3-1 beta version, and after some googling for the answer this fixed the dependency problem for me. Not sure if this works for the ubuntu package too, give it a try.

---

### Post by MonolithTMA on 2005-12-19
Ok...NPTL is off so I don't get that funky every-single-dependancy-is-missing error.

Dependancy check in dvdripper gets me:
[IMG]http://merelyadequate.net/images/forumpics/Screenshot_dvd_rip_Dependency_check.png[/IMG]

I've installed unrar, but dvdripper doesn't seem to want that.

When I try to install vcdimager I get:
[IMG]http://merelyadequate.net/images/forumpics/vcdimager_dependancies.png[/IMG]

My repositories are as such:
```
#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu breezy universe
deb-src http://archive.ubuntu.com/ubuntu breezy universe

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu breezy multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy multiverse

deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse 
```

I'll keep playing and see if I can figure this out.

Any more ideas would be much appreciated.

---

### Post by barryp on 2005-12-19
[QUOTE=MonolithTMA]Good morning all.

I have a few DVDs that are out of print, and I would like to make backup copies of them, but they are encrypted. I see lots of tools that require WINE and DVD Shrink for Windows. Are there any methods that will work on a PPC install of Ubuntu? Thanks! :)[/QUOTE]

Try dvdbackup. I was familiar with it because there is a GUI version for Mac OS X. It's command line only under Linux but has help/documentation to help you out if you are intimidated by that, as I was. It does work on my Mac, G4 dual processor, running Dapper (also used it on Breezy), Haven't found a utility for compressing to single layer disc under Linux, though.

---

### Post by dietrying on 2005-12-19
> Try switching NPTL on/off in Preferences/Miscellaneous options. I'm using a self-compiled 0.97.3-1 beta version, and after some googling for the answer this fixed the dependency problem for me. Not sure if this works for the ubuntu package too, give it a try.


wow, this worked for me....thank you @ pvz!

greetings, david

---

### Post by Jason-X on 2005-12-20
[QUOTE=barryp]Try dvdbackup. I was familiar with it because there is a GUI version for Mac OS X. It's command line only under Linux but has help/documentation to help you out if you are intimidated by that, as I was. It does work on my Mac, G4 dual processor, running Dapper (also used it on Breezy), Haven't found a utility for compressing to single layer disc under Linux, though.[/QUOTE]

I'm in the same boat. DVDbackup works well for making an exact copy of the DVD and decripting it. Unfortunatly I have no way of shrinking for single layer discs.

I have a question. I assumed DVDrip can only convert the DVD to an .avi, .mpeg etc.  Not make a backup with VIDEO_TS etc. If you only want to encode the DVD to .avi, .mpeg etc, then I use "Acidrip" which works really well. I have got some nice quality rips using this application. Also there is no dependecy problems like with DVDrip.

Just thought I mention this.:)

---

### Post by tjm on 2005-12-21
I tried the approach using dvdbackup and acidrip. Seems to work fine with Breezy Badger on a superdrived Mac-Mini.

But 'libdvdread3 cannot be found'... 'check /usr/share/doc/libdvdread3/README.Debian'

Found the solution in the README.Debian file... Executing the script mentioned there worked!

---

### Post by tariqf on 2006-04-29
how about k9copy. Works much like dvdshrink on windoze. GOt it working nice on my mac mini

---

### Post by GrammatonCleric on 2006-05-14
There's also DVD95 (or DVD 9 to DVD 5).

[http://freshmeat.net/projects/dvd95/](http://freshmeat.net/projects/dvd95/)

---

