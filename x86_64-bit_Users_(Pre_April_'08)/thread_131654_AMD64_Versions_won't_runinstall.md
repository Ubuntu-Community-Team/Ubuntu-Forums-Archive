---
title: "AMD64 Versions won't run/install"
date: 2006-02-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by rdav@usa.com on 2006-02-16
When I attempt to either run or install Version 5.10, the program proceeds through detecting hardware and scanning the cd-rom and is loading installer components, when it halts with an error message:  "There was a problem reading data from the CD=ROM.  Please make  sure it is in the drive, etc."

I can retry but I continue to get the error message and have to abort.

I get the identical problem with both the live and the install versions of the CD, which I created from the iso images I downloaded.

I have used several different machines to cownload the iso images and different cd-rom drives to burn the cds.  I have also downloaded the iso images from different mirrors.

It appears that there is a missing or defective installer component in the current AMD64 iso image.

The AMD64 machine I am using runs several other versions of Linux including Knoppix in both the install and run cd packages, so it doesn't appear to be an obvious hardware problem.

I have successfully installed and updated Ubuntu 5.10 on an Intel PC but can't get the AMD64 version to run or install.

What should I do?

tia,  Robert
       Mill Valley, California

---

### Post by StuartCarter on 2006-02-16
I had the same problem.

Do a server install, then use apt-get to install ubuntu-desktop and synaptics.

Should do you.

---

### Post by rdav@usa.com on 2006-02-16
How do you do a server install?   Is it one of the Ubuntu installer main menu choices?

---

### Post by rdav@usa.com on 2006-02-16
Here is some additional info that was displayed when I ran the CD-ROM Integrity test:

"The /pool/main/l/linux-source-2.6.12/nic-modules-2.6.12-9-amd64-generic-di_2.6.12-9.23_amd64.udeb file failed the MD5 checksum verification"

This may help to determine what is wrong with the iso images.

- Robert

---

### Post by StuartCarter on 2006-02-16
[QUOTE=rdav@usa.com]How do you do a server install?   Is it one of the Ubuntu installer main menu choices?[/QUOTE]


At the boot: prompt, type server. If you get a scambled display (especially if you have a high res screen), you may want to try server vga=771

---

### Post by marcthepunk on 2006-02-17
i'm also experiencing a similar problem with a ubuntu installation on a amd64 machine.
the installation step reaches as far as 'installing additional components' and it bombs out at the jfsutils.deb
i tried the server install but that didn't change anything.
i redownloaded the iso from different mirrors and reburned at different speeds, nothing changed.
i'm a newbie at this linux and have been dying to try it out.
anyone has a solution?

---

### Post by rdav@usa.com on 2006-02-17
Sorry, but it didn't work for me.

I had exactly the same result as before.  It looks to me like the iso images are trashed for AMD64.

Is anyone working on fixing this problem?

Robert
Mill Valley, California

---

### Post by Daggett on 2006-02-17
Burn an AMD64 Kubuntu DVD and install from that.  It worked fine for me.  If you really want to use GNOME then install GNOME afterward.

---

### Post by Daggett on 2006-02-17
One more bit of advice.  If you have a dual-core AMD64 processor, do NOT use the SMP version of the kernel.  It crashes like crazy.  If you know what you're doing, compile your own SMP version of the kernel from the latest sources.  It doesn't support everything Ubuntu/Kubuntu uses, but it works fine for my needs and it doesn't crash.

---

### Post by StuartCarter on 2006-02-17
[QUOTE=rdav@usa.com]Sorry, but it didn't work for me.

I had exactly the same result as before.  It looks to me like the iso images are trashed for AMD64.

Is anyone working on fixing this problem?

Robert
Mill Valley, California[/QUOTE]


Unfortunately I have to agree :(

---

### Post by rdav@usa.com on 2006-02-17
I'll try burning the AMD64 Kubuntu CD first, as the DVD is 3.5 gigabytes.

If that doesn't work, I try downloading the 3.5 gb DVD.

This sure is becoming a pain...

---

### Post by StuartCarter on 2006-02-18
[QUOTE=rdav@usa.com]I'll try burning the AMD64 Kubuntu CD first, as the DVD is 3.5 gigabytes.

If that doesn't work, I try downloading the 3.5 gb DVD.

This sure is becoming a pain...[/QUOTE]

So, I get back in after being out for an hour to find the Ubuntu64 laptop has crashed and will no longer boot :(

Now downloading the DVD ISO :(

---

### Post by marcthepunk on 2006-02-18
well i tried the suggestion... came up null.  i even downloaded and tried the i386 iso, nothing.  i however, came up with a different 'bomb out' component when installing additional components E2FSPOGS.UDEB???

any more suggestions would be appreciated, thanks.

---

### Post by Daggett on 2006-02-18
Like I said, the Kubuntu 5.10 AMD64 DVD installed fine for me.   I'm running it right now.  I can't speak for the Ubuntu installation because I didn't install from Ubuntu. But if it's a matter of the Ubuntu iso being mucked-up, then Kubuntu uses the identical software base, so just go with that.  Just install GNOME afterward if you really want to use GNOME.  (I think that's a bit masochistic, personally, but each to his own).  

If you want to run an AMD64 version of Firefox 1.5.0.1, I compiled one and posted a link to the tar.bz2 file in this forum.  I don't know if it's possible to make Java or any plugins work if you go that way.  There's an AMD64 version of Java, but no plugin .so with it. 

I also repeat: Do NOT use the Ubuntu/Kubuntu/Debian 2.6.12-10-k8-smp kernel on a dual-core AMD64 machine.  It crashes.  I compiled my own 2.6.15.4 k8 smp version and it works great.

---

### Post by StuartCarter on 2006-02-18
[QUOTE=marcthepunk]well i tried the suggestion... came up null.  i even downloaded and tried the i386 iso, nothing.  i however, came up with a different 'bomb out' component when installing additional components E2FSPOGS.UDEB???

any more suggestions would be appreciated, thanks.[/QUOTE]


I would suggest using the DVD image - it has worked pretty much flawlessly for me. Including properly setting up my laptop screen properly :-D

---

### Post by yarzer on 2006-02-19
[QUOTE=StuartCarter]I would suggest using the DVD image - it has worked pretty much flawlessly for me. Including properly setting up my laptop screen properly :-D[/QUOTE]

I have the same trouble with the disks that Ubuntu sent me, packaging and all.  I can't install either the 32 or the 64 bit version on my computer.

I'm hoping to find a solution here.  The dvd solution sounds semi-promising.  I'll download it after I finish downloading Knoppix dvd, it's at 52% as I type this.

yarzer


DFI LANPARTY UT nF4 Ultra-D
AMD 64 FX-55
(BIOS 06/23/2005)
Sapphire X800 256MB
Vantec Stealth 520W PSU 24 pin
(2x512MB) Corsair TWINX Dual Channel PC3200 DDR 400MHz Memory
4x Western Digital WD2000JD SATA hdd
Lite-on 16XDVD+/-RW
Lite-On CDRW/DVD combo
Zalman CNPS7000B-Cu CPU cooler
Onboard sound

---

### Post by spork27 on 2006-02-20
I am unable to install Unbuntu as well.  System is an AMD 4400+ w/ Asus A8N SLI Premium motherboard.

I burned CDs from the following iso:
ubuntu-5.10-install-i386.iso
ubuntu-5.10-install-amd64.iso
kubuntu-5.10-install-amd64.iso
...and each fails at the same point in the "loading installer components" page.

Now what's interesting is the same CD in the same drive *does* work when used to install Unbuntu onto a VMWare image.

Guess I'll try the DVD next.  Anyone have any ideas?

---

### Post by StuartCarter on 2006-02-20
Try the DVD version - it has worked fine for me.

---

### Post by Daggett on 2006-02-20
Another tip:  This probably only applies to a tiny fraction of users, but if you happen to have an SATA DVD/CD drive, almost no Linux installer will work.  The kernel needs to have atapi_enabled=1 in order to see the DVD/CD drive during installation.  But the default is atapi_enabled=0, and there's no way (at least no way I know) to change the default.  Not even boot line parameters work for me.  (libata.atapi_enabled=1 is SUPPOSED to work, but it doesn't).   So the installer won't see the DVD/CD drive and will crash.  Depending on the distro, you may or may not find out why the installation crashed, so some distros don't even give you a clue as to what went wrong.

---

### Post by marcthepunk on 2006-02-20
sorry to be such a pita but i still can't get this installation completed.  i also downloaded versions 5.04 for the amd and i386, netiher were able to install.  they also bomb out at the additional components installation step.  i feel stupid and fustrated.  i really want to have linux install and my choice for ubuntu seems to be wrong.
by the way stuartcarter, where did you find the dvd .iso?
my system is compatible for the install.  i got a partition drive available.  do i in anyway have to prepare this allocated space for the ubuntu install?  i noticed on snpashots of the installation that there's a screen for partitioning the drive.  i haven't seen this step on all my attempts.

---

### Post by StuartCarter on 2006-02-20
[QUOTE=marcthepunk]by the way stuartcarter, where did you find the dvd .iso?
[/QUOTE]

If you go to the main download page - 
[http://www.ubuntu.com/download?highlight=%28dvd%29](http://www.ubuntu.com/download?highlight=%28dvd%29)
- the DVD images are right at the bottom of the page. With BitTorrent it came down in about 26 hours.

I feel your pain! Is there no-one from the Ubuntu project looking in these forums...? It would be nice to know that Ubuntu at least *acknowledge* this issue, even if there is nothing that can be done...

---

### Post by spork27 on 2006-02-20
[QUOTE=spork27]I am unable to install Unbuntu as well.  System is an AMD 4400+ w/ Asus A8N SLI Premium motherboard.

I burned CDs from the following iso:
ubuntu-5.10-install-i386.iso
ubuntu-5.10-install-amd64.iso
kubuntu-5.10-install-amd64.iso
...and each fails at the same point in the "loading installer components" page.

Now what's interesting is the same CD in the same drive *does* work when used to install Unbuntu onto a VMWare image.

Guess I'll try the DVD next.  Anyone have any ideas?[/QUOTE]

Well, I tried the Unbuntu DVD (ubuntu-5.10-dvd-amd64.iso) and encountered the same problem at the same point in the installation.

Like others, I find this baffling and very frustrating.

The baffling part is why the same CD in the same drive works fine when boot from inside a VMWare image but fails when boot directly.  Each image I tried fails at the same point during the install.  I ran memtest86 and no errror were reported.

Is there maybe something with nforce chipset Unbuntu does not like?  Grasping at straws here...

---

### Post by RAOF on 2006-02-20
[QUOTE=StuartCarter]...
I feel your pain! Is there no-one from the Ubuntu project looking in these forums...? 
...[/QUOTE]
*No, there aren't*.  These are community support forums.  The developers rarely come here.  If you want their attention, file a bug on [www.launchpad.net/malone](www.launchpad.net/malone).  Unless you (or someone else with the problem) do that, the devs might not know about it.

I've had a similar problem - I had 2 cd drives, a DVD-ROM and a CD-RW.  It would boot from one drive, but try to load stuff from the other (empty) drive.  Solved that one by putting the cd in the other drive ;)

Not sure if that's applicable to you, but it's a similar problem I've had.

---

### Post by StuartCarter on 2006-02-20
I did not know about the launchpad site - thanks for that. I have filed a bug report.

---

### Post by gwi on 2006-02-21
[QUOTE=spork27]The baffling part is why the same CD in the same drive works fine when boot from inside a VMWare image but fails when boot directly.[/QUOTE]
I have the opposite (more or less): I booted the live CD (AMD64 version) with no problems. Under VMWare Workstation 5.5 both the live CD and the installation CD install fine, but the X-server won't start (module vmware not found).

[QUOTE=spork27]Is there maybe something with nforce chipset Unbuntu does not like?  Grasping at straws here...[/QUOTE]
I have an Asus A8N SLI (with an nForce4 chipset). Live CD works fine, haven't tried the install CD yet.

---

### Post by cthippo on 2006-02-21
[QUOTE=Daggett]Another tip:  This probably only applies to a tiny fraction of users, but if you happen to have an SATA DVD/CD drive, almost no Linux installer will work.  The kernel needs to have atapi_enabled=1 in order to see the DVD/CD drive during installation.  But the default is atapi_enabled=0, and there's no way (at least no way I know) to change the default.  Not even boot line parameters work for me.  (libata.atapi_enabled=1 is SUPPOSED to work, but it doesn't).   So the installer won't see the DVD/CD drive and will crash.  Depending on the distro, you may or may not find out why the installation crashed, so some distros don't even give you a clue as to what went wrong.[/QUOTE]

  I'm thinking that's not entirely correct.  I have  Plextor PX716SA SATA DVD drive and it seems to work just fine.  I just wish i could get the display to play nice. :mad:

---

### Post by Daggett on 2006-02-21
Maybe the SATA thing is a kernel version issue, then.  The Debian AMD64 installer uses 2.6.15.1, and atapi_enabled is set to 0 by default in that kernel.  Maybe it's not a problem with the 2.6.12 kernels that Ubuntu/Kubuntu use.

---

### Post by Tachyon60 on 2006-02-22
I'm having basically the exact same problem with the ubuntu iso's, I've verified their md5 checksum and everything but get that same error message when I try to install or run a live CD. I've also tried the DVD, but I have another CD drive hooked up as a slave so maybe it's trying to read from that? I have a VIA chipset and am getting the same problem so it's not a problem with linux and nvidia, I think it might just be a problem with the ISO or something.

---

### Post by StuartCarter on 2006-02-22
[QUOTE=Tachyon60] I have a VIA chipset and am getting the same problem so it's not a problem with linux and nvidia, I think it might just be a problem with the ISO or something.[/QUOTE]

I wouldn't exclude the VIA chipset from the equation - try updating your BIOS, see if that makes a difference? (Not that I have had bitter experience with VIA chipsets.. oh no, not at all.... darn them!)

---

### Post by Daggett on 2006-02-22
I've installed Kubuntu and Ubuntu on two systems with the nforce chipset without any problems at all.

---

### Post by StuartCarter on 2006-02-22
It may well be that more recent VIA chipsets are better behaved - the troublesome ones I have had are slightly older chipsets, from pre-2005.

---

### Post by Tachyon60 on 2006-02-22
Actually, I'm on a k8v deluxe, from around 2003 or something like that (maybe 2004). Do you think my problem might be mobo related? I have the most up to date BIOS.

---

### Post by StuartCarter on 2006-02-22
[QUOTE=Tachyon60]Actually, I'm on a k8v deluxe, from around 2003 or something like that (maybe 2004). Do you think my problem might be mobo related? I have the most up to date BIOS.[/QUOTE]

I will be decisively vague on that point.... Look over ----> there!

(Runs <---- that away ;) )

---

### Post by marcthepunk on 2006-02-24
stuartcarter, i have tried your suggestion, and *rien*.
i've just read in another thread, someone who has been having the similar problem.  a resolution has been posted, supposedly... i haven't tried it yet.

[http://ubuntuforums.org/showthread.php?t=135270](http://ubuntuforums.org/showthread.php?t=135270)

---

### Post by ShadowSystems on 2006-02-28
(Sighs, raises his hand, and gives a weary, migraine-induced "Me, too.")

I downloaded the 5.1 Breezy ISO's from four different mirrors, verified the hashes, verified the written-to-disk data, and *squat*. 

All four copies failed to install in the exact same way. They'd go through everything up to the point where they've rebooted and shows the brown bar... Never gets past that point, and refuses to give me back keyboard control so I can try to FIND an error code...

I'm not sure if it's related, but my PS2 scrollwheel mouse wasn't being recognized, either...

I ordered copies of the 5.1 release, and those barfed in the same way, too.

I'm currently downloading a copy of the 5.10 Breezy DVD (and getting a whopping 220Kbps! *SCHWEEET*), so I'll keep my fingers crossed.

I'm currently using the 32bit version, but I *WANT* to use the 64bit - otherwise my AMD 64 3500+ is just sitting there, bored & twiddling it's thumbs waiting for me to throw yet ANOTHER application at it in a futile attempt at making it start to slow down... (Maniacle laughter)

System:
AMD 64 3500+ / 2Gb Kingston DDR (2x 1Gb) / ATI Radeon 256Mb DDR X600 PCIe / WD 250Gb SATA (x2) 

I'll put the OTHER 2 1Gig sticks of RAM back into the system once I get the 64bit version to install properly, otherwise it barfs on boot. :(

---

### Post by spork27 on 2006-02-28
I tried several Breezy isos, including the 32-bit CD and 64-bit DVD, and encountered the same problem every time at the same point in the install.

I gave up on Breezy was able to successfully install amd64 Dapper on an AMD 4400+ system.

---

### Post by soce_32 on 2006-02-28
I have an EMT64 system and could not get [KU]buntu installed on it.  None of the Debian CD's or DVD's worked either and I always ran into an issue with I/O errors when the CD/DVD would spin up and try to start copying packages for the base install.  This is a SATA system running in native mode, and the CD/DVD player is recognized as a PATA device by the bios.  When I would change the bios to combined mode, the CD/DVD worked but my hard drives weren't recognized during the install process.

I managed to get Ubuntu installed with help from this site:

[http://marc.herbert.free.fr/linux/win2linstall.html](http://marc.herbert.free.fr/linux/win2linstall.html)

This machine has Fedora on it, and I managed to install to another partition by pointing grub to the installer kernel/initrd.

Fairly simple if you are already running linux, YMMV if you try to get grub going from Windows.

---

### Post by Deuzsama on 2006-03-04
I've had same issues as some of you, downloaed the AMD64 Ubuntu and it ran fine in VMware, Xserver and all, when i installed, Xserver just won't run. Keeps telling me there is no device installed.

---

### Post by Miakehl on 2006-03-04
I installed the 64 bit version on my laptop just fine using the CDs ordered from Ubuntu. You could order one from them, wait forever, then install, but if your impatient, I have no clue...

---

### Post by midol on 2006-03-05
I have a new motherboard and cpu - an Asus A8N-VM with NVIDIA® GeForce™ 6100/nForce™ 410 graphics onboard. This went in to a Fedora Core 3 system. I am thinking of switching to Ubuntu and so I downloaded and burned a 5.10 live cd. X won't start. The main console doesn't respond although I can Alt-Fn into other consoles. Is this a known issue? In Fedora I would suspect the Nvidia driver. Ideas?

Dave

---

### Post by RAOF on 2006-03-06
[QUOTE=midol]I have a new motherboard and cpu - an Asus A8N-VM with NVIDIA® GeForce&#8482; 6100/nForce&#8482; 410 graphics onboard. This went in to a Fedora Core 3 system. I am thinking of switching to Ubuntu and so I downloaded and burned a 5.10 live cd. X won't start. The main console doesn't respond although I can Alt-Fn into other consoles. Is this a known issue? In Fedora I would suspect the Nvidia driver. Ideas?

Dave[/QUOTE]
It'll be the nv driver.  Ubuntu uses the open source "nv" driver for nvidia cards by default and sometimes (like yours) newer cards aren't actually supported.  Whoops! :-? 

You could fix it by running
```
sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable
```
at one of your secondary consoles.  That will install the binary nVidia driver, which should support your card :)

---

### Post by vodgut on 2006-03-07
Would be nice to know if a bug has been filed, though I doubt it would be fixed until there was a newer release of the install media.  If you can't install in the first place...updates don't really help.

I've been seeing this problem too.  I'd try the DVD, but unfortunately the DVD burner is in my new AMD 4800+ X2 machine, which currently has no OS, making it quite a challenge to burn a DVD without removing the device to another machine, which isn't my first choice, given the various reports of success.

FWIW, I've got an Asus AN8-SLI Premium board.  Maybe I'll try FC4 on it just to get an OS on there, if that works, then burn one of these and maybe dual-boot it.

---

### Post by linuxNewb555 on 2006-03-09
I'm a complete novice, but i had a problem with my Ubuntu 5.10 install a few weeks ago. (full install version) In my excitement to move to linux, i was not using an ISO recorder to burn my image to cd, i just dragged the downloaded file to cd and then burned it... 3 times! That does not work, you must use an ISO recorder to burn the file to disk. I know that's elementary, but that's all I've got. 

system: Asus K8N, amd64, plextor 716sa dvd, SATA hd

Good luck.

---

### Post by vodgut on 2006-03-10
Just as an update, Dapper Drake worked for me.  There's obviously some sort of bug in the x86_64 version of Breezy that is unfortunately part of the installation CD's, and apparently cannot be fixed if you're using those CD's.  Dapper isn't officially released yet, but that version worked for me.

---

### Post by zonerr on 2006-03-10
Actually there appears to be a problem in several distros lately and I believe that it has to do with the kernal. It seems that older kernals like the one in Debian work fine but the newer ones have stack overflow problems. Still testing but at this point I would suggest going for yesterday's version on most distros

---

### Post by vodgut on 2006-03-11
Could be.  I got a 32-bit version of FC4 to install on the machine.  I didn't try the x86_64, though.  Seems like it's fixed in Dapper, though.  I did encounter some other issues (I had to install the nVidia driver before I could log into GNOME, for instance) but I'm mostly successfully using Dapper now.

---

