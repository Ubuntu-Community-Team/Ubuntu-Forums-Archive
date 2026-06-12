---
title: "Yaboot just will not install"
date: 2005-10-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by kioshi on 2005-10-21
Everything in my nstallation went smoothly, the instaler set up all partitions on a 20gig partition on my drive, made the boot, swap and the system partition. I use a iMac G3 400. But the yaboot thingie failed to install. It`s a FW drive but since it's a Mac I have always been using it as my main drive for OS X Tiger with no problem.

So what do I do? Anyway to install this yaboot thing? Or to boot my Ubuntu anyway else?

The installer said I could boot it by using /boot/vmlinux kernel and then using dev/sda4 with root=dev/sda4 as a variable but I absolutely have no idea on how and where to use this. :confused: 

Thanks!

---

### Post by bohsup on 2005-10-22
I have the same problem with my slot loading iMac.:???:

---

### Post by kioshi on 2005-10-23
[QUOTE=bohsup]I have the same problem with my slot loading iMac.:???:[/QUOTE]

Same thing happens even using the internal HD to me...
Nobody here seems to help anyway.

---

### Post by TAGLonewolf on 2005-10-23
Same problem..Everything allright till the 83% of the yaboot installation..Then error, and I don't know what to do...
(External HD)

---

### Post by kioshi on 2005-10-23
[QUOTE=TAGLonewolf]Same problem..Everything allright till the 83% of the yaboot installation..Then error, and I don't know what to do...
(External HD)[/QUOTE]

Exactly, 83% - both on my external FW drive and my internal iMac slot loading G3 400.... and then it says it fails to install and gives you no reason for that...

---

### Post by TAGLonewolf on 2005-10-23
:confused:

---

### Post by bigbadben on 2005-10-23
i had the same proble....because i tried to install on external hd.So i decided to install on my main hd(imacg3500mhz)....i tried to install at boot(install-safe)install went well and the yaboot too.
(btw your external hd has to be off) to make an perfect install cause i dont know why, but it produce the same yaboot error.So just turn your extern hd to off and install yaboot again.
:D

---

### Post by daller on 2005-10-26
On my PowerBook G4, YaBoot stalls at 50%

...Just as an information

Safe-install???

---

### Post by daller on 2005-11-01
I think it has something to do with yaboot not being able to create another partition for ubuntu successfully!

Has any of you tried to install it by letting it erase the hard disk?

---

### Post by bigbadben on 2005-11-01
[QUOTE=daller]I think it has something to do with yaboot not being able to create another partition for ubuntu successfully!

Has any of you tried to install it by letting it erase the hard disk?[/QUOTE]
that is how i did it.......use all the main drive and auto partition.
:smile:

---

### Post by felix_stegerman on 2005-11-01
You might want to take a look at this:
[http://www.sowerbutts.com/linux-mac-mini/](http://www.sowerbutts.com/linux-mac-mini/)

It's about Debian, but the info on partitioning might be helpful.
I used it to install Debian on my Mac Mini without problems. ;-)


Felix

---

### Post by Andrus on 2005-11-12
I had this problem while installing Ubuntu Breezy onto a Mac Mini. Tried onto an external firewire drive several times with no luck. Finally I backed up my Mac's OSX internal volume to the firewire drive and just tried to install onto the internal drive, still no luck. Ubuntu would install right up to the Yaboot bootloader and then tell me that Yaboot could not be installed. 

As soon as I turned off the external firewire drive, it worked! Maybe Yaboot just gets confused with external drives, or maybe multiple drives. I want to try again by opening the mini and detaching the power to the internal drive and see if Yaboot would then install to the firewire drive, but not today.

I backed my OSX volume up using Bombich software's NetRestore, a free download from [http://www.bombich.com](http://www.bombich.com). By "restoring" my boot drive to the firewire drive, I got a perfectly booting copy of my Mac Mini OSX volume. The software got to the point of "checking" the drive for space and seemed to hang, but I waited and it was actuallly making the copy, although the progress bar never moved past about 10 percent. A requester came up and told me it was done after a couple of hours (70Gigs).

I then just allowed the Ubuntu installer to go with the defaults and format & partition the drive itself. Worked perfectly and I have a nice little Linux machine that seems just as fast as my 3 Ghz. P4 machine, if not a little faster.

I plan now to go back and partition the Mini for both Mac OS X and Ubuntu.

To do this, I plan to fire up the boot DVD for the Mac Mini (use the CD if that's what you've got), and partition the drive using the Mac Disk Utility into two main partitions. This will make a "secret" third partition at the head of the disk for the partition table, about 32kb.

Then, I'm going to go ahead and install Mac OS X first.

Once that's done, I will go and re-run the Ubuntu installer. I'll probably delete the open mac partition, and use the guided partitioning on the free space,

Okay, let's see how all that goes...

---

### Post by oskude on 2005-11-12
could be some help...
[http://www.ubuntuforums.org/showpost.php?p=474404&postcount=5](http://www.ubuntuforums.org/showpost.php?p=474404&postcount=5)

---

### Post by Beowulf the Geat on 2005-11-13
I had the exactly same problem!

I've been trying since I received my CDs one week ago... version 5.04.

A burned CD 5.1 version freeze while is uncompressing, giving a beautiful kernel panic...

Once it didn't install because I had not set 'boot' for any partition... :-/ then, even setted, not install the 'yaboot'...

In one of hundred times 'yaboot' was intalled but, by the time the iMac reboot, I only got the '?' and 'mac face'... not found a OS...

Now I am trying using the preferred partitioning schemes of Mac OS drive setup (using a mac OS boot disc)...

Last time the installation freezed at language... almost the end...

Green iMac 233Mhz 32MB memory with IR port

Question: If Ubuntu is so great why have I to set the partition by myself???
All the big distributions have a automatic partitioning tool!! 

Why Ubuntu doesn't?

---

### Post by kioshi on 2006-02-04
So... If I just erase my internal HD and install Ubuntu or Kubuntu from scratch (while my FW HD is turned off) it will work flawlessly?

Sorry for asking again, I just wanna be sure before I delete my internal HD.

---

### Post by 3rdalbum on 2006-02-06
As far as anyone will be able to tell you, it will work with the Firewire drive turned off. Ubuntu doesn't work well with Firewire and that probably won't change anytime soon.

Hoary doesn't boot off a Firewire drive; isn't Breezy the same in that regard?

Beowulf, Ubuntu DOES partition the hard drive automatically, but it can only access the unallocated portion of the disk (licensing complications mean it can't ship with the necessary drivers to access HFS and HFS+ partitions). Also mate, Ubuntu won't work with only 32 megs of RAM. You'll need to upgrade to 64 to run a text-only server, or 128 to run with a GUI.

---

