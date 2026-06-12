---
title: "disk manager missing ubuntu 6.10"
date: 2006-10-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by ashenlight on 2006-10-20
I have noticed that disk manager is missing
from the administation menu in ubuntu 6.10 64 bit amd.
  Would other users have found this?

   Many thanks,
              Nigel

---

### Post by Dr. Nick on 2006-10-20
I saw it missing aswell in the 32bit ver, not sure exactly why. They implemented another disk utility somewhere called [B]Baobab. 

[/B]I used it once, but am not sure what all it does , or if its a replacement.

---

### Post by Dr. Nick on 2006-10-20
Try this in a terminal

gksudo disks-admin

That may get it, Im not at home so cant try myself

---

### Post by mrhealthpatriot on 2006-10-29
I noticed it was missing. I send my backup files to another drive. So I went back to 6.06. Also, about half of my extensions worked in Firefox 2.0  Also, some of the programs I use were not available, or did not function properly with Edgy Eft. I may try upgrading or a fresh install (seems to "mesh" better) in 2 or 3 months. Had to fix my fonts, broke some of the audio settings, etc.
Didn't see any improvements, outside of OpenOffice, anyway.

---

### Post by VFiend on 2006-10-29
disks-admin was unmaintained, so it was dropped from GNOME. At least, that's what I read somewhere.

---

### Post by gloomdragon on 2006-11-01
This is exactly the type of BS that will keep microsoft going for a very long time still. For crying out loud, I am not completely IT illiterate and have been trying to get Ubuntu 6.10 to work for the past two days. The LIVE CD crashed twice when I asked to install and has a number of bugs during startup. Then, for some bizarre reason the computer refuses to start, although I suppose it could be unrelated to ubuntu.
But then, just I finally get the thing running I find that there is no way the damned thing will access my Windows partition. Instead you get the stupid file system with a bunch of folders
Then you spend you look for help and ubuntu's help sends you to an utility that doesn't exist anymore.  Then you search the net and you find solutions that only pop up a command not found. And in fact that is if you are even able to find the inaptly named bash hidden away in the menus. It's exactly the type of obnoxious programmer bs that will keep general users away.

HELLOOOO!!!! how do you ever expect Linux to be a real competitor to windows if you need to be into programming to be able to even get the damned thing to find your drives and partitions??? I actually used UNIX in college and I still can't get this stuff to work.

I've had it. Stuff Linux. I really wanted to use linux instead of windows or at least as a complement. Break the monopoly and all of that. But this is nerve-wrecking, annoying and you really have to hate Bill a lot to put up with it. It's not worth the frustration.
I'll still use Firefox, and Openoffice and a number of other non-proprietary software which has figured out what user-friendly means but Linux is dead. See you in 20 years maybe when it actually becomes suitable for normal HUMANS. 
Ciao

PS: AND THE DEFINITION OF THE SCREEN IS REALLY BAD TOO!!! All of the lines and details look blurred as if i needed glasses. This stuff is bad for your eyes

PPS: And what's more, how is it possible that UBUntu comes with Firefox and  you can't get it downloaded with firefox? Instead of saving the ISO you get the code of it opened. Another masterstroke for computer semi-illiterates to feel comfortable with the thing hey?

---

### Post by danielph on 2006-11-02
> **gloomdragon said:**
> This is exactly the type of BS that will keep microsoft going for a very long time still. For crying out loud, I am not completely IT illiterate and have been trying to get Ubuntu 6.10 to work for the past two days. The LIVE CD crashed twice when I asked to install and has a number of bugs during startup. Then, for some bizarre reason the computer refuses to start, although I suppose it could be unrelated to ubuntu.
Without more details difficult to say what the problem is however, I would check your media here (on the boot screen) and also check the the iso or maybe you want to try something tried and tested such as dapper. Edgy is pushing forward a little more and it dapper is considered more stable. 


> **gloomdragon said:**
> 
But then, just I finally get the thing running I find that there is no way the damned thing will access my Windows partition. Instead you get the stupid file system with a bunch of folders
Then you spend you look for help and ubuntu's help sends you to an utility that doesn't exist anymore.  Then you search the net and you find solutions that only pop up a command not found. And in fact that is if you are even able to find the inaptly named bash hidden away in the menus. It's exactly the type of obnoxious programmer bs that will keep general users away.
Disk-admin was dropped as it was not considered a worthwhile tool. I agree with this to a degree, it never really did update fstab properly and there are other tools that seem to work better. It is unfortunate that you didn't learn of these other tools. They are gparted and pysdm. There are others including endeavour2 and baobab that do various disk tasks.
 
 Setting up Linux to see an NTFS partition is not too difficult. For your situation pysdm is able to mount drives as disk-admin could.
 
If you find you want to get Linux working then there are answers to your problems. This software is available for free and it is your choice to use it or to use something else. I too was frustrated on first switching over, but like anything you have to give it a fair trial. 
 
> **gloomdragon said:**
> 

HELLOOOO!!!! how do you ever expect Linux to be a real competitor to windows if you need to be into programming to be able to even get the damned thing to find your drives and partitions??? I actually used UNIX in college and I still can't get this stuff to work.

I've had it. Stuff Linux. I really wanted to use linux instead of windows or at least as a complement. Break the monopoly and all of that. But this is nerve-wrecking, annoying and you really have to hate Bill a lot to put up with it. It's not worth the frustration.
I'll still use Firefox, and Openoffice and a number of other non-proprietary software which has figured out what user-friendly means but Linux is dead. See you in 20 years maybe when it actually becomes suitable for normal HUMANS. 
Ciao

Your choice, but I used to work for Microsoft and now I won't even have Windows installed as a dual boot. Linux is so much better IMHO. Sure there are problems, but these are computers not toy soldiers. 

> **gloomdragon said:**
> 
PS: AND THE DEFINITION OF THE SCREEN IS REALLY BAD TOO!!! All of the lines and details look blurred as if i needed glasses. This stuff is bad for your eyes
Sounds like a problem with the configuration. Not normal at all. Unless there is a problem with Ubuntu running on your hardware.


> **gloomdragon said:**
> 
PPS: And what's more, how is it possible that UBUntu comes with Firefox and  you can't get it downloaded with firefox? Instead of saving the ISO you get the code of it opened. Another masterstroke for computer semi-illiterates to feel comfortable with the thing hey?

Not really sure what you are saying here. Ubuntu 6.10 comes with Firefox 2.0. This is included in the iso that you download and included in the repos. As I said - what are you saying here?

---

### Post by gloomdragon on 2006-11-02
well, turns out ubuntu just doesn't run with MSI or Asus notebook bios. The computer just doesn't boot. Apparently a conflict with the APICs. Unless you disable them you don't get it to run, or if you do then the pc won't boot after using Ubuntu.

I apologise for blowing up but when you see your brand new pc just not working... Anyway, enough said.

The definition problem, I went through all of the settings before getting rid of ubuntu and all the settings were fine. Yet I just don't get a sharp image. 

The Firefox issue. It's just that if you simply click on the mirror to download IE ask you where you want to save it and Firefox simply goes on to opening the code. Sure, I can sort that easy. But a fairly PC illiterate user might not. I mean, it would be the first contact with the thing. Anyhow, Frustration mostly.

Thanks for the help anyhow but I just can't run Linux on my PC unless I disable APICs and since I can't find out if I need them for the things I use my PC for I'm not going to do that. 

I worked in a helpdesk and part of my job included sorting out XP issues. That's part of why I wanted to try Linux :-)
Maybe I'll try Mandriva if I find out that it doesn't conflict with Asus and MSIs

Thanks anyhow danielph

---

### Post by danielph on 2006-11-02
> **gloomdragon said:**
> well, turns out ubuntu just doesn't run with MSI or Asus notebook bios. The computer just doesn't boot. Apparently a conflict with the APICs. Unless you disable them you don't get it to run, or if you do then the pc won't boot after using Ubuntu.

Check out [http://en.wikipedia.org/wiki/Intel_APIC_Architecture](http://en.wikipedia.org/wiki/Intel_APIC_Architecture) under Operating System Issues
They mention using noapic or nolapic kernel parameters.

> **gloomdragon said:**
> 
I apologise for blowing up but when you see your brand new pc just not working... Anyway, enough said.no worries

> **gloomdragon said:**
> 
The definition problem, I went through all of the settings before getting rid of ubuntu and all the settings were fine. Yet I just don't get a sharp image.  The install may not have correctly detected your monitor. If you do decide to try again you may try logging on to terminal (select sessions terminal only at logon) and run the command sudo ```
dpkg-reconfigure xserver-xorg 
```

Some cases you may need to know your hardware details, but it will try and detect your hardware and make an xorg.conf file for you (/etc/X11 folder). 

> **gloomdragon said:**
> 
I worked in a helpdesk and part of my job included sorting out XP issues. That's part of why I wanted to try Linux :-)
Maybe I'll try Mandriva if I find out that it doesn't conflict with Asus and MSIsI found Suse to be pretty good, a little bloated but good hardware configuration and very polished.

Good Luck

---

### Post by Dr. Nick on 2006-11-02
Some of the problem with firefox opening the code is related to the mirror I believe, I have this issuse once in a blue moon, But 9.9 times out of 10 the program saves like it should, I dont believe thier is a option to set that behavior.

---

### Post by uid0 on 2006-11-05
> **VFiend said:**
> disks-admin was unmaintained, so it was dropped from GNOME. At least, that's what I read somewhere.

Great!  So now what do we use to partition disks that has a nice front end?](*,)

---

### Post by danielph on 2006-11-05
> **uid0 said:**
> Great!  So now what do we use to partition disks that has a nice front end?](*,)
You can use pysdm (as root) which is like disk admin or to partition you can still use gparted

---

### Post by rg_stephens on 2006-11-06
HELP !!! 
I'm a new Linux user, and I can't get Ubuntu 6.10 to recognize my XP partitions which I created with the CD. The 'Administration' menu doesn't have a disks manager, or anything like it. I installed qtparted, but it can't find anything except my USB drives. How do I install the other utility? 

Thanks for all your help :)

---

### Post by danielph on 2006-11-06
> **rg_stephens said:**
> HELP !!! 
I'm a new Linux user, and I can't get Ubuntu 6.10 to recognize my XP partitions which I created with the CD. The 'Administration' menu doesn't have a disks manager, or anything like it. I installed qtparted, but it can't find anything except my USB drives. How do I install the other utility? 

Thanks for all your help :) I am assuming you are running Gnome here.

You can install pysdm (Storage Device Manager) and gparted (Gnome Partition Manager) through Synaptic Package Manager (from the menu in Gnome - System, Administration). You will need to enter your user password to gain root access.

In case you cannot find them with a search in Synaptic you may need to enable the correct repository. I believe they are in the Universe repository (enabled in Synaptic - Settings, Repositories)

Or you can use the terminal (Applications, Accessories, Terminal) and type ```
sudo aptitude install pysdm gparted
```

---

### Post by rg_stephens on 2006-11-06
Thanks Danielph!!  
After I installed the Storage Device Manager and clicked 'Mount' everything was ok.

---

### Post by MiKom on 2006-12-23
But pysdm cannot make the disks appear on my desktop or in the places menu. Also after fresh edgy installation disks are not mounted. I was bit confused with this because Dapper found the disks with no problem just after install. This seems like regression. Is it going to be resolved in Feisty?

---

### Post by danielph on 2006-12-24
Is the problem that the disks are not mounted or that the mounted disks do not get displayed?

---

### Post by MiKom on 2006-12-24
As a matter of fact, both. 
After fresh edgy installation windows disks are not mounted anywhere therefore they don't show on the desktop and in Places. They are visible in device manager but not mounted. 
When I mounted them with pysdm I could reach them only through /media/hdx. I think that this presence on the dekstop probably has something to do with HAL and pysdm doesn't inform HAL about it's work.

---

### Post by danielph on 2006-12-24
The mounting is controlled in fstab. For example```
/dev/hda3       /media/hda3     ext3    defaults     0 0
```The displaying of mounted volumes is a configuration setting that you can access with  gconf-editor. Normally you don't need to go there as I think the default is to display mounted volumes. The setting is /apps/nautilus/desktop/volumes_visible [true|false].

Perhaps you can try this switch and see if it works for you. I have had some problems in this area also. Maybe it only refers to network mounts and USB.

---

### Post by MiKom on 2006-12-25
After setting the disks with pysdm and rebooting the disks appeared. Sorry, I should have tried rebooting after setting. Nevertheless windows disks should be detected during istallation and should appear in fresh system without user interaction (pysdm).

---

### Post by danielph on 2006-12-26
I agree that if you are installing Ubuntu a tool such as pysym should be included by default. Windows partitions are detected early in the installation and you can include them to be mounted by choosing to manually edit your mount points in the partition editor (gparted) on installation. Just add a mount point for the windows partitions to /windows or /media/hda1 for example. I just did an edgy install on a laptop and gparted will include the windows partition and suggest mounting it at /media/hda1 by default when you choose manually partitioning.

---

### Post by juff on 2006-12-26
Hi Danielph

How do you run gparted or pysdm?  Neither of them are in the menus and they don't work from the console either.

---

### Post by Azakus on 2006-12-26
They don't come preinstalled.
```
sudo aptitude install gparted psydm
```
I tend to prefer gparted because it looks cleaner.

---

### Post by juff on 2006-12-26
> **Azakus said:**
> They don't come preinstalled.
```
sudo aptitude install gparted psydm
```
I tend to prefer gparted because it looks cleaner.

OK, thanks [COLOR="Blue"]Azakus.[/COLOR]  Didn't realise that these disk manager apps didn't come pre-installed (bit of an oversight?).  gparted installed fine using your suggested console command.

---

### Post by leep on 2006-12-30
I'm unable to automatically mount new partitions with gParted.
And configuring a new fat32 partition with psydm creates a new read-only device mounted on /media/hdbc2.
How do I change /media/hdbc2 to let every user write to it? Chmoding 777 /media/hdbc does not have any effect.
Thanks.
S.

---

### Post by drr422 on 2007-01-08
Im running into that problem with psydm not giving any user write permissions as well, and i found that this occurs with my sata hard drive, because it works fine with my ide hard drive.  Even when you go into preferences and you change the owner, it still doesn't mount.  I think that a restart might help, but im using the livecd so its not a option. 
 I was just searching for another tool that could do the same thing that pysdm is doing, but do it right. If anyone knows of this tool, please let me know :-)

---

### Post by ubanto on 2007-02-13
This is nonsense to me. Every OS on Earth has a disk manager: Mac OsX has disk utility, every user-friendly distro has a disk manager. Even windows has something that does the job.
How can an OS come without one?

---

### Post by yme on 2007-05-19
> **danielph said:**
> Disk-admin was dropped as it was not considered a worthwhile tool. 


This is such a stupid decision. It was a really neat GUI interface and excellent for dealing with all USB drive problems. 

It is especially a stupid decision when GParted is not installed in the basic setup.

Is someone trying to put people off Ubuntu? The Disk Manager in Dapper was so much more easy to use for the average users needs than running a handful of terminal commands in order to format a USB drive.

---

### Post by danielph on 2007-05-19
> **yme said:**
> This is such a stupid decision. It was a really neat GUI interface and excellent for dealing with all USB drive problems. 

It is especially a stupid decision when GParted is not installed in the basic setup.

Is someone trying to put people off Ubuntu? The Disk Manager in Dapper was so much more easy to use for the average users needs than running a handful of terminal commands in order to format a USB drive.

I am sure the developers intention is not to put people off, they certainly had their reasons (some of them mentioned in this thread). If you feel this strongly then you can always raise a feature request to bring it back or use another distribution. I don't mean that to sound harsh, just that you have the freedom to choose.

---

### Post by yme on 2007-05-19
Yes, the freedom to choose and also the freedom to waste a good bit of time because I can no longer easily reformat USB drives using Feisty because someone took it into their head to remove a very neat and useful tool. 

As I said before it is amazing that no program to reformat a USB drive is available ready installed in Feisty. I also run an old box with BeaFanatIX Linux. It is basically Ubuntu Breezy parred down to the guts in order to make it run on borderline obselete machines. And that had GParted installed as default ](*,)

Anyway, I couldn't find GParted available for Feisty, instead there is QTParted. I installed and ran this is order to reformat a USB drive that has got a bit messed up (as they do). Straight away I can see there is no nice easy option to unmount the volume as with the Disk Manager in Dapper. Instead I have to open another window to do this (with Dapper it was a quick click of a button and obviously flagged to the newbie as something that needs doing),

Already it is not looking promising and, of course, I get an error message when I try to format. I go to the FAQ of QTParted and get the following piece of incoherence:
Q: When I hit the "save/commit" button i get "Error commiting device... please read the FAQ... /etc /etc". What about this?
A: I know... this is a problem :( I don't want to blame kernel developers, but this is not a bug of qtparted, but a kernel bug! I think that even if a device is busy 'cause there is mounted a partition you must be able to re-read partition table... kernel developers don't think so :( I will work for some kind of work around, but i cannot do miracles, even if i solve some problems you will not be able to use the full power of QTParted! A solution is to use qtparted on a live distribution, see the links page for more info!

It seems that a pretty important and useful little tool on Dapper has been replaced by was seems to be a fairly lousy piece of software. Dapper would have had no problem reformatting, kernel developers or no!

It is pretty stupid that the best solution to the problem that I can now see is to get my BeaFanatIX Linux (yes, the parred down Breezy!) going tomorrow and use GParted ...

I'd really love to know exactly what the decision to abandon Dapper's Disk Manager was based on ....

yme

---

### Post by danielph on 2007-05-19
> **yme said:**
> 
It is pretty stupid that the best solution to the problem that I can now see is to get my BeaFanatIX Linux (yes, the parred down Breezy!) going tomorrow and use GParted ...
yme

According to [http://packages.ubuntu.com/feisty/gnome/](http://packages.ubuntu.com/feisty/gnome/)

gparted is available in Feisty. Just install it.

It wasnt on the ISO for space reasons.

[https://bugs.launchpad.net/ubuntu/+bug/93604](https://bugs.launchpad.net/ubuntu/+bug/93604)

Or get your hands dirty and run "mkfs". Typing the command "man mkfs" will give you info you need.

---

