---
title: "Hoary-64 Desktop Freeze &amp; System Crash"
date: 2005-06-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by 8oluf7 on 2005-06-01
I have a homebuild SFF machine which ran Warty 64 without problems. I upgraded to Hoary and, some time later, started to get random desktop freezes. The first symptom is that the active window stops responding to the mouse buttons, although the cursor can still be moved across the screen. The task bars respond for a little longer. If I force the machine into terminal mode it asks for login, but then produces an error message:

ata1: command 0x35 timeout, stat 0xd0 host_stat 0x20
ata1: called with no error (D0)!
Buffer I/O error on device sda1, logical block 5692

(the numbers above are examples, as they are not the same each time this happens)

The keyboard is now ineffective, so the only option is to use the reset button. The system restarts, but the BIOS can't find the hard drive (no entry in the list of IDE devices). I have to press the on/off switch for a full 'from cold' restart - which works. Reiserfs sorts out the file system and I'm good for another random period (yesterday these ranged from 20 to 40 minutes of Firefox or Freecell).

System Specification:

Antec Aria SFF case and PSU
MSI K8NM FISRB motherboard (MATX with nForce3/250 chipset and RTL-8129 Gigabit Ethernet)
Athlon 64 3200+ CPU
2 x 512MB Kingston PC3200 RAM (on MSI approved list)
160GB Seagate ST3160827AS SATA hard drive
NEC ND3500A CD-RW/DVD-RW
Connect3D 256MB ATI Radeon 9550 8xAGP graphics card (passive cooling)
NEC 1970NX 19" TFT monitor (connected via DVI and running at the default 1280x1024 resolution)

I did a full default installation of Hoary, preserving my /home partition. I frequently check for updates with Synaptic and install any it finds. Inspired by maqi's HOW TO I have installed the ATI fglrx drivers - but they make no difference to the freeze problem. 

Searches of various forums reveal that there are far more theories about what is causing this problem than I can get my head round. 
[list]
[*]It's a kernel problem - with lots of different 'solutions'
[*]It's a graphics driver problem - also with lots of different 'solutions'
[*]It's a motherboard problem - not enough power to the PS/2 connectors - switch to USB
[*]It's a PSU problem
[*]It's a temperature problem [if so, why do I get **more** time after a restart]
[/list]
But there are also many 'This didn't work for me' messages.

Any advice on how to narrow down the options, such as how to install and set up monitors, which logs to examine, which config. files might hold the secret, would be much appreciated. I want to start using the machine for some serious work - with deadlines!

---

### Post by thrift on 2005-06-01
It could be that your drive is simply going bad.   At the very least something is up with either the drive, the controller, or the driver for the controller(kernel).

Once way to test is to boot from a  livecd, then do some heavy IO on the drive.

Mount the drive, cd to the directory you mounted it on, and then try a command like this

find | xargs cat > /dev/null

when it is done run

dmesg

and see if you have a million ata errors in your log.

To make sure it's not the filesystem alone, create another filesystem with any extra space left on the drive, and then do some big writes and reads to the new partition.  If you get I/O errors when you do this you can be pretty sure it's the drive or controller.

You can be pretty sure it's not the controller because you said you were running fine for quite a while, unless you simply weren't noticing the errors.  Hooking up another drive to the controller and trying to do some big reads/writes to the partition will tell you if it's the controller or not.  If you get IO errors with a different drive, it's the controller/driver for the controller.  If you don't get IO errors this way, but you do with another drive, you can be pretty sure it's the drive/filesystem.

Hopefully this will help you diagnose where the  problem is occuring at, as you need to figure out what problems are causing the symptoms for us to be able to help.

---

### Post by 8oluf7 on 2005-06-01
[QUOTE=thrift]It could be that your drive is simply going bad.   At the very least something is up with either the drive, the controller, or the driver for the controller(kernel).

Once way to test is to boot from a  livecd, then do some heavy IO on the drive.

Mount the drive, cd to the directory you mounted it on, and then try a command like this

find | xargs cat > /dev/null

when it is done run

dmesg

and see if you have a million ata errors in your log.

To make sure it's not the filesystem alone, create another filesystem with any extra space left on the drive, and then do some big writes and reads to the new partition.  If you get I/O errors when you do this you can be pretty sure it's the drive or controller.

You can be pretty sure it's not the controller because you said you were running fine for quite a while, unless you simply weren't noticing the errors.  Hooking up another drive to the controller and trying to do some big reads/writes to the partition will tell you if it's the controller or not.  If you get IO errors with a different drive, it's the controller/driver for the controller.  If you don't get IO errors this way, but you do with another drive, you can be pretty sure it's the drive/filesystem.

Hopefully this will help you diagnose where the  problem is occuring at, as you need to figure out what problems are causing the symptoms for us to be able to help.[/QUOTE]

Thanks for the prompt response. I'll try the live CD idea and report back.

**Results** 
I booted the system from a Warty live-CD (I don't have a Hoary one handy). 

The system has been running for two hours so far without a hiccup, which I think indicates that you were spot on in focussing on the hard drive. 

The desktop shows three hard drive partitions - hde1, hde6 and hde7. I ran

find | xargs cat > /dev/null

for each, followed by dmesg

hde6, which was set up as 100GB ReiserFS3 for /home - no errors
hde7, which was intended to be a 30 GB windows file repository, and is currently empty - no errors
hde1, which was set up as 30GB ReiserFS3 for / - multiple errors of the form:

Buffer I/O error ...
cloop: Read error ...
cloop: error -3 ...

There were also some indications in the dmesg file of problems during the boot from CD.

I closed down (clumsily, so I got the 'can't find the hard drive' error and had to do a cold restart). This time there were no error messages in dmesg either from the boot itself, or from a repeat of the tests. 

Weird. I think I'll sleep on this and try again tomorrow!

It could be finger trouble while partitioning during the installation. I tried to set up a FAT32 partition called /Windows (to act as a file repository for the other - Windows - machines on the network); the partition is there as hde7, but the folder called 'Windows' is shown under hde1. Since both hde 1 and hde7 were intended to be 30GB I may have confused the system!  

Thanks for your help.

---

### Post by thrift on 2005-06-01
It sounds like your filesystem on hde1 is partially corrupt, but it looks like the drive is ok.

Boot of the livecd, make sure hde1 is not currently mounted, and then use reiserfsck to fix the problem.

Personally I've never had a lot of luck with reiser under anything but SuSe.  XFS I've never had a lot of luck with.  EXT3 seems to be the most solid...it "just works".  If you continue to have problems with the filesystem consider EXT3.

Good Luck.

---

### Post by 8oluf7 on 2005-06-04
[QUOTE=thrift]It sounds like your filesystem on hde1 is partially corrupt, but it looks like the drive is ok.

Boot of the livecd, make sure hde1 is not currently mounted, and then use reiserfsck to fix the problem.

Personally I've never had a lot of luck with reiser under anything but SuSe.  XFS I've never had a lot of luck with.  EXT3 seems to be the most solid...it "just works".  If you continue to have problems with the filesystem consider EXT3.

Good Luck.[/QUOTE]
I tried to use reiserfsck as suggested, but the system kept reporting something like 'superblock not found'. So, last night, I proceeded to your Plan B - backed up the /home stuff onto a CD and did a full default reinstall, this time selecting EXT3. Everything went as before, but without the crashes. Double-checked this morning - system has now been running for well over 4 hours with no signs of a freeze.

Many thanks for your prompt help in localising and fixing this problem.

**Added 17 June 2005** 
After 30 restarts, the EXT3 FS tries to carry out a full check - **and fails**. Now I can't even boot. I can boot from a live CD and see the HD (once all partitions, once all but one, from memory). The symptoms are consistent with corruption of the journal file, I think. 

Research on other forums lead to a mention of a possible SATA/journalling FS incompatibility and advice to switch off 'writeback' using hdparm. Is this a red herring, out of date info or something I need to do? If so how - given I have a trashed system?

Another possibility, looking at the Seagate support area, is incorrect setting of the IDE Access Mode in the BIOS (I just accepted the defaults, as the BIOS appears to recognise the drive correctly). 

If the file corruption is due to bad physical blocks on the drive, how do I check for this and format to skip the bad blocks? Can I do this for the suspect partition, or do I have to do it for the whole drive?

Mike G.

Note for the wise: Always include 'finger trouble' on the list of possible causes!

---

### Post by 8oluf7 on 2005-07-06
[QUOTE=8oluf7]**Added 17 June 2005** 
After 30 restarts, the EXT3 FS tries to carry out a full check - **and fails**. Now I can't even boot. I can boot from a live CD and see the HD (once all partitions, once all but one, from memory). The symptoms are consistent with corruption of the journal file, I think. 
[/QUOTE]
This was finger trouble! I had not activated 'Show hidden files' in Nautilus. So, by selecting the top level folder and its contents to burn onto a backup CD (lazy noob that I am), I backed-up the  journal files as well. Worse, when I restored (as I thought) my data files by doing a select and copy all - I overwrote the journal files!! No wonder the machine got confused. 

My bad.

---

### Post by 8oluf7 on 2005-08-23
[QUOTE=8oluf7]**Added 17 June 2005** 
After 30 restarts, the EXT3 FS tries to carry out a full check - **and fails**. Now I can't even boot. I can boot from a live CD and see the HD (once all partitions, once all but one, from memory). The symptoms are consistent with corruption of the journal file, I think. 

If the file corruption is due to bad physical blocks on the drive, how do I check for this and format to skip the bad blocks? Can I do this for the suspect partition, or do I have to do it for the whole drive?[/QUOTE]Found out how to do this from postings on this and other forums:
[list=1]
[*]fire up with a live CD
[*][FONT=Courier New]sudo fdisk -l[/FONT] to find out what the partition names are
[*]backup any data on the suspect partition that you want to keep
[*]unmount the suspect drive
[*][FONT=Courier New]sudo mke2fs -ccvj <partition description>[/FONT] (/dev/hde5 in my case)
[/list]The -cc ensures that repeated reads and writes are performed and the -vj displays progress and records the results. **NB - all data in the partition will be overwritten!** 

In my case I ran mke2fs for the whole drive, having re-partitioned it as a single partition during an unsuccessful attempt at a fix. mke2fs chewed its way through and, to start with, the block count incremented about 4,000 blocks per refresh. Then the program found a problem. It appears to respond by reducing the blocks checked at a time; certainly the block count increment reduced. When a quick calculation showed that the check was going to take a week or more to complete (it was a 160GB drive!) I gave up and scrapped the drive.

---

### Post by DancingSun on 2005-08-23
That sucks!

Is the drive still under warranty? Maybe you can get it exchanged for a new one. BTW, how do you identify journal files?

---

### Post by 8oluf7 on 2005-09-17
[QUOTE=DancingSun]Is the drive still under warranty? Maybe you can get it exchanged for a new one. BTW, how do you identify journal files?[/QUOTE]I tried various distros and live CDs when I was commissioning the machine (last Christmas). Ubuntu was the only one I had that recognised the hardware and installed itself properly. Red Hat, Mandrake, Beatrix and Knoppix all failed for one reason or another, usually failure to cope with a SATA-only setup. One of these trials produced an error message to the effect that the install was trying to write to disk sectors that didn't exist - followed by graunching noises. So, I think a warranty claim would probably fail, even though the drive is less than a year old.

I didn't specifically identify the journal files; I deduced that they might be candidates for corruption from the  machine behaviour.

I have been running the machine temporarily with a 40GB IDE drive. I have now bought a 250GB SATA drive which I will probably install when Breezy is released. It's a Hitachi because they are the only manufacturer I could find which claimed that their tools would cope with Linux filesystems.

---

