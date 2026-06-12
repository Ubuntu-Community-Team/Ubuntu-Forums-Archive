---
title: "One big dirty pile of newbie questions!!"
date: 2006-04-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by namluc on 2006-04-16
Intrepid helpers here is a list of questions to test your courage!!

Having tried out the ubuntu live cd and been really impressed, i'd quite like to install it on a partition of my hard drive to learn more.

I am currently running os x tiger on a single partition on a 40gig hard drive

_Here are my Questions_:

[LIST]
[*]1  Could somebody who routinely partitioned hard drives be able to do it without compromising the already installed data?

[*]2  If the answer to question 1 was yes!!! How likely will a point and click person like myself be able to do it!!;)

[*]3  If no that means that tiger would have to be installed all over again then?

[*]4  Whilst doing a disk partition is there a chance that the entire system will get cacked up to the extent that of being unfixable by somebody with a lot of time but no experience?

_Free Space_

I have 14gb of free space left.

[*]How much does tiger use for virtual memory?
If i dedicate 5-6gig to ubuntu.....

[*] Is that enough?

[*]will my tiger go hungry for vm?

[*]Once running.... Can Tiger see or feel and talk to Ubuntu and vice versa?
For instance my scanner seems to work better under ubuntu, could i scan photos and send them to iPhoto without using my usb stick?

_Windows XP_

[*]And for my friend who is thinking of using ubuntu to breathe life into his ageing laptop is currently running windows xp. Does it support iTunes music files quicktime and wmp in some form or other?

[*]Please could you point me to a good website offering linux drivers for 3rd party wireless cards.

[*]What is the footprint of xp compared to ubuntu?


That is a terrible lot of questions, so thanks in advance to everyone who tries to answer them!!!:D :D :D 

[/LIST]

---

### Post by hentaidan on 2006-04-16
> **namluc]
[LIST]
[*]4  Whilst doing a disk partition is there a chance that the entire system will get cacked up to the extent that of being unfixable by somebody with a lot of time but no experience?
[/list]
[/quote]

Yes, if you have slippery fingers.

> 

_Free Space_

I have 14gb of free space left.
[LIST]
[*]How much does tiger use for virtual memory?
If i dedicate 5-6gig to ubuntu.....

[*] Is that enough?

[*]will my tiger go hungry for vm?
[/list]


Ubuntu should be ok, just be careful what partitions you use, what you install, and keep an eye on free space. I dual boot MacOSX/Ubuntu, MacOSX has 10gb total and seems happy (though i dont use a great deal).

> 
[LIST]
[*]Once running.... Can Tiger see or feel and talk to Ubuntu and vice versa?
For instance my scanner seems to work better under ubuntu, could i scan photos and send them to iPhoto without using my usb stick?
[/list]


Ive had success accessing Ubuntu files from within MacOSX (needs 3rd party ext2fs reader for Mac).

> 
_Windows XP_

[LIST]
[*]And for my friend who is thinking of using ubuntu to breathe life into his ageing laptop is currently running windows xp. Does it support iTunes music files quicktime and wmp in some form or other?
[/list]


Umm, yes and no, or at least I have found that some work and others dont.

> 
[LIST]
[*]Please could you point me to a good website offering linux drivers for 3rd party wireless cards.
[/list]


Linux may well support it "out the box" said:**
> 
[LIST]
[*]What is the footprint of xp compared to ubuntu?
[/list]


As in diskspace? Difficult to say: Ubuntu comes with everything you will "ever" need, and isn't just an OS. Saying that, Ubuntu total on my system is ~4gig, 2x that of XP? (But that is *everything*: games, office...!).

> That is a terrible lot of questions, so thanks in advance to everyone who tries to answer them!!!:D :D :D

Dont ask (or google ;) ), and you'll never know.

---

### Post by joelito on 2006-04-16
I'm assuming you're running tiger on a ppc Mac..

Now being a PC guy I can't answer all of your questions but i'll try anyway.

You should be able to resize your Tiger partition without problems. Just make sure you back up the data just in case.

If you use the installer on cd I recommend that you read carefully every dialog you get to se and follow the proper instructions, shouldn't be too hard. You can check the live cd and see if there's any utility with the name gparted or qtparted. It has a nice point and click interface you can use. There's always a posibility that the previous Operating system gets damaged but it's nothing you shouldn't be able to fix.

As for the disk space, 5gb should be enough to use  Ubuntu with some user data and stuff, you should also have at least 500mb to use as virtual memory for ubuntu on a separate partition(swap area)

I think the HFS+ filesystem used by OSX is supported by Ubuntu. And I think the Darwin system (OSX kernel and basic userland) support the ex2 and ext3 filesystems so they should have no problem to find each other (You'll probably have to mount manually) 

For your friend:
Most of the media codecs need to be installed manually. However there are tools like EasyUbuntu and Automatix that make the task as easy as a few point and clicks...

The drivers are another issue. There's plenty of information in the forums about dealing with drivers that are not included but I can't count them all in this post (You and your frind will have to look around or come with specific information about the devices you have/will have)

---

### Post by aimislame15 on 2006-04-16
1: Yes, you can create a new partition without erasing all data. There are some utilities to do this such as DriveGenius (<--what I use ;-)). There is a way to do it without any utilities, but it could be very dangerous for someone not familiar with the command line.
2: With utilities, its a very painless process. With the command line, I don't really know how able you are with a command line.
3: If you decided that you didnt want to try partitioning with a utility or command line, then yes, you would have to reinstall Tiger.

On my iBook G4 (800mhz, 640mb ram, 60gb HD) I had 20 gb before I started. I set 10 aside for ubuntu and 2 aside for a swap partition. After defragmenting my hard drive and installing ubuntu, my ibook is as fast or maybe .00000000000001% faster :P.

5-6gb should cover you with your partition for ubuntu, then it might be a good idea for like 1gb swap space.
Chances are, tiger, although it loves just using as much VM as it can at any time, prolly wont make a fight with it.

It is not well supported but I do it all the time, talking back and forth between my ubuntu and OSX partition, you can use the mount command from ubuntu to mount your OSX partition, and then you can use ExtFSManager on OSX to contact your ubuntu partition.

I myself do not have any running x86 boxes. I have two that are, lets say old. Not just regular old, but 33mhz processor old.

I do know that x86 linux is a bit better supported than ppc linux.

I hope I adressed most of the issues at hand.

---

### Post by aimislame15 on 2006-04-16
Quite a nice set of answers really fast :P;)

---

### Post by namluc on 2006-04-16
Wow thanks guys:mrgreen: 

Just downloading the trial version of drivegenius now. I hope it works!

Checked out the box of the wireless card, it is completely unbranded. Which is impressive in itself though it does say it is compatible with redhat. Just doesn't seem to like ubuntu.

Think i'll go for the 5gig option with half gig of swop space.

Thanks again for your help:KS 

i'm off to take a carving knife to my computer!!

---

### Post by Ptero-4 on 2006-04-16
> 1 Could somebody who routinely partitioned hard drives be able to do it without compromising the already installed data?

The ubuntu installer's built-in partitioner tool can resize OSX partitions without deleting them.

>  If the answer to question 1 was yes!!! How likely will a point and click person like myself be able to do it!!

If you can navigate through the ubuntu installer, then yes. You definitelly can.

> 4 Whilst doing a disk partition is there a chance that the entire system will get cacked up to the extent that of being unfixable by somebody with a lot of time but no experience?

If you're on a PPC Mac, there's no chance of breaking your computer by just doing a bad install. Believe me, I have installed all sorts of linuxes on both my older iBook G3 500MHz and my eMac G4 1.42GHz and I have never gotten them dead as result of a f*ck'd up install, if your ppc mac goes unbootable, all you need to do is format and install again. If OTOH you're on the Intel variety of Macs, then. Well you might probably end up triggering an hidden intel "anti-piracy" hardware (an embeded anti-OSS/anti-Linux chip) and kill your Mac.

> I have 14gb of free space left.
How much does tiger use for virtual memory?

AFAIK, OSX uses as much as twice your installed RAM.

> If i dedicate 5-6gig to ubuntu.....
Is that enough?

Yes. in fact, ubuntu can run fine on 3gig of HD space.

> will my tiger go hungry for vm?
Well. I don't have Tiger, but Jag and Panther never had issues with VM usage. But since Tiger is quite rough in some areas, it may have some memory leaks.

> Once running.... Can Tiger see or feel and talk to Ubuntu and vice versa?
For instance my scanner seems to work better under ubuntu, could i scan photos and send them to iPhoto without using my usb stick?

Well, ubuntu can read and write to hfs+, and OSX can read and write to ext2/ext3. But OSX can't access reiserfs, jfs, or xfs.

> And for my friend who is thinking of using ubuntu to breathe life into his ageing laptop is currently running windows xp. Does it support iTunes music files quicktime and wmp in some form or other?

For iTunes music files you'll probably be able to run the Windoze version of iTunes under wine, but setting up and using wine is still quite complex. You best bet would be having a Mac around for your iTunes music needs. As for quicktime and wmp, well quicktime is easy since IIRC there are OSS quicktime codecs and there's a non-free wrapper to allow you to use the windoze wmp codec on ubuntu.

> What is the footprint of xp compared to ubuntu?
Ubuntu takes 3gigs with everything installed. WinXP takes 2gigs by itself with nothing else installed. Ubuntu takes one gig more than XP, but that's including *everything* (Office suite, web browser, games, utilities, internet and conectivity suites, a photoshop-grade image editing app, etc).

In the end. If you're on a PPC Mac, go ahead and install ubuntu, it won't break. If you're on an Intel Mac, don't install ubuntu. It WILL surelly kill your Mac and even if it doesn't, ubuntu doesn't yet include elilo (the bootloader required for the Intel Mac's open firmware implementation). As for the Wintel, if it's older than 2002, install ubuntu, if it's newer than that. Don't install it. Installing Linux or OSS on a Intel Mac or a PC made on 2002 or later WILL surelly break it.

---

### Post by namluc on 2006-04-16
Cheers there Ptero4

Knowing nothing about computer hardware, ihave no idea what kind of stresses are exerted when doing something major. i dunno pop a jumper or something!!

as chronicled in the recommended thread with umpteen hits just below this one (at time of writing), I took the plunge and turned off journaling in osx then squeezed down that partition! It was quite nerveracking. But seemed to work. Me mac didn't dissapear in a puff of smoke anyhow!

As i didn't understand what i was typing when squeezing the osx partition down i gave ubuntu 2 more gig than i wanted to, but i can live with that!:) 

My new problem, and the answer to this one i'm sure is staring me in the face, is that i've lost tiger. Can't find it. On rebooting the system I only get a single boot in to ubuntu, no option for osx at all! Maybe its sulking!:rolleyes: 

So where can it be? And more importantly how do i call it back?:-k

---

### Post by 3rdalbum on 2006-04-17
[QUOTE=namluc]
My new problem, and the answer to this one i'm sure is staring me in the face, is that i've lost tiger. Can't find it. On rebooting the system I only get a single boot in to ubuntu, no option for osx at all! Maybe its sulking!:rolleyes: 

So where can it be? And more importantly how do i call it back?:-k[/QUOTE]

Okay. I've never actually put the Mac OS into the boot menu (it always suited me better to use OpenFirmware to boot into Linux), but the first step is to find out which partition your Mac is on.

From Ubuntu, go into System > Administration > Disks. Type your user password when it asks. Click the "Partitions" tab to list the partitions of your disk. Keep clicking through them until you find the Mac OS one(s). (You will know because the "Size" bar will show the correct free space of the partition).

Look at the "Device" field. It should say something like /dev/hda7. Remember this. Now go into a terminal and type:
```

sudo gedit /etc/yaboot.conf
```
And type your user password when it asks.

Now, the next step is the bit I've never done. Create some new lines in the file and put "macosx=/dev/hda7" (or whatever the pathname was). Save the file, then run the command "sudo ybin".

Hopefully, this should make the Mac OS an option in yaboot. And if it doesn't... well, as I've just followed my own instructions, then I'm stuffed! (I'll reboot and post back to tell you if it worked).

EDIT: I tried it, and yaboot still wouldn't boot the Mac side. I did notice that, to boot OS X, you must point yaboot to the Apple Bootstrap partition, not the actual OS X partition. See here: [http://www.debian.org/ports/powerpc/inst/yaboot-howto/ch6.en.html](http://www.debian.org/ports/powerpc/inst/yaboot-howto/ch6.en.html). Also, if you REALLY need to get back to OS X in a hurry, you can start up from a system disk - then Open Firmware will start up the Mac by default.

If you do that, you can still get back to Linux - just start up with Cmd-Opt-O-F held down, and type "boot hd:6,yaboot" at the prompt. Substitute the number 6 for your Linux partition (if you can't remember, guess... it doesn't do any harm to keep going up through the numbers until you get the right one).

---

### Post by namluc on 2006-04-17
Cheers 3rd album!

I take it that the new line of code goes in yaboot.conf and not the terminal. If so I have two questions:

```

## run: "man yaboot.conf" for details. Do not make changes until you have!!
## see also: /usr/share/doc/yaboot/examples for example configurations.
##
## For a dual-boot menu, add one or more of:
## bsd=/dev/hdaX, macos=/dev/hdaY, macosx=/dev/hdaZ

boot=/dev/hda2
device=/pci@f4000000/ata-6@d/disk@0:
partition=4
root=/dev/hda4
timeout=100
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot
macosx=/dev/hda3

image=/boot/vmlinux
	label=Linux
	read-only
	initrd=/boot/initrd.img
	append="quiet splash"

image=/boot/vmlinux.old
	label=old
	read-only
	initrd=/boot/initrd.img.old
	append="quiet splash"

```

sorry for pasting all that.

1. I typed man yabot.conf in the console but to no effect i assume i'm lacking a run command. That isn't sudo by any chance is it?

2.The command that i'm supposed to write seems to already be there! How can it be there and not give me the option to dual boot already?:-k 

3. The last time I had a dual boot was ages ago between Windows 3.11 and NT and i remember there being a definate choice. Is there always a visible choice now or is there a button i don't know about to press upon hearing the chime that selects which os to load?

4. If that command had been absent would it have made any difference where I put it?

Thanks for everybody's help:KS

---

### Post by hentaidan on 2006-04-17
[QUOTE=namluc]So where can it be? And more importantly how do i call it back?:-k[/QUOTE]

Might wanna read through the wiki entry on [Macintosh PowerPCs Dual Boot]("https://wiki.ubuntu.com/YabootConfigurationForMacintoshPowerPCsDualBoot")

---

### Post by namluc on 2006-04-17
Thats fantastic:KS 

As suspected it all worked fine!! i just didn't know how to bring up the selection menu (alt) as it boots in to ubuntu by default! I now have a dual boot system with all my os x stuff still there and unharmed (as far as I can tell!):mrgreen: 

One final question: is it possible using terminal or what not to resize the ubuntu partition downwards then give the leftovers to  tiger?

---

### Post by 3rdalbum on 2006-04-18
lol... I tried my own instructions and I still can't get Mac OS 9 going on the boot menu!

My 'puter doesn't have that Option bootloader feature, so naturally I didn't think of it. Anyone care to help me now? (no great rush... I'm happy with my current dual-booting arrangement anyway, and I'm sure I'll work it all out eventually!)

---

### Post by Ptero-4 on 2006-04-19
3rdalbum. What Mac do you have? I ask b/c the Option bootloader is in all newworld PPC's IIRC. Also some Macs won't let you boot into OS 9.

---

### Post by namluc on 2006-04-19
sorry 3rd album i feel slightly responsible 4 your current predicament...:???:

---

### Post by 3rdalbum on 2006-04-20
Don't worry, namluc - I've set the computer back now to automatically boot Mac OS (and boot Ubuntu if I interrupt it), which is the way I've always had it set.

My father has expressed an interest in being able to boot Ubuntu without having to go into OpenFirmware though, so I wouldn't mind setting up the menu now!

The computer is a 333MHz iMac. It doesn't have the option bootloader, and it definately runs Mac OS 9! The only problem I have is that the OS 9 option doesn't appear in yaboot.

I've put "macos=/dev/hda7" into my yaboot.conf file and run ybin. I've used hfsutils to look at the bootstrap partition to confirm that my altered file is on the bootstrap. HDA7 is the OS 9 partition.

Does Mac OS 9 appear as a label in the Yaboot menu? (e.g. if you hit Tab, is it meant to appear?)

I'll just check that I haven't overlooked anything really obvious.

---

