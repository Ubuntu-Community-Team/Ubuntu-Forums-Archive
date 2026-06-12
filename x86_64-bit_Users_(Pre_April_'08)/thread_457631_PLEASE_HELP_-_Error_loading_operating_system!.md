---
title: "PLEASE HELP - Error loading operating system!"
date: 2007-05-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by khayman80 on 2007-05-28
I built my current machine about a month ago.  It's got 2 750 GB SATA drives set up in a RAID 1 array, an Athlon 64 x2 4200+ processor and a K8N Neo Platinum motherboard.  When I installed Windows XP, I left 20GB of free space on the RAID array for a linux distribution.  I've never used linux before, but figured I'd give dual-booting a shot.

I downloaded Kubuntu 7.04 for x86 64-bit users, then burned the CD and booted it up.  The installation seemed to go fairly smoothly.  I chose "guided- use the largest free space" for installation.  Then at the end it restarted, prompted me to take out the CD and I did.  When the computer rebooted it simply went straight to windows- no GRUB loading screen at all.  I checked the disk management tool in Windows and noticed that the 20GB of free space still read as unpartitioned.

I then tried to install Kubuntu again, in exactly the same manner.  I'd thought that maybe I restarted it too early and it didn't have time to finish setting up GRUB.  The installation procedure was identical, and I gave it a good 20 minutes to finish everything it needed to do after the last prompt before I hit restart.

Then my nightmare began.  Right after my bios check, I simply get the message "Error loading operating system".  I backed up my system before the install, but there's only so much backing up you can do with 700GB of data, so there's a significant amount of data left on the disk that I'm terrified of losing.

Please help!  I can only hope that somewhere in this digital wilderness exists a wise and kind Linux God, who will share his nearly infinite knowledge with me.  Perhaps there's a command I can type into the terminal on my Kubuntu Live CD to undo whatever Kubuntu did?  I'm not worried about recovering the Linux distribution or completing the install procedure (but that would be a nice bonus).  All I want is to recover my windows installation from whatever Kubuntu did....

Thanks in advance...

-Bryan

---

### Post by kuja on 2007-05-28
I've no idea what it would have tried to do, but there are plenty of things to fear here. For example, last time I checked (which was about 7 or 8 months ago, last release), K/Ubuntu did not support FakeRAID. In the worst case scenario it might have tried to overwrite one of the drives because it couldn't see the partiton. Lets hope that's not the case, because that'd be a hell of a mess. 

Anyhow, here's where I'd start:

Pop in the Kubuntu live cd and wait for it to load.
After it's loaded up, hit alt+space and when katapult comes up type in Konsole
In Konsole type the following in:

```
sudo apt-get install dmraid testdisk
sudo /etc/init.d/dmraid start
```

That should get the fakeraid support going if it wasn't there (and I don't think it was ... but I could be wrong yeah?)

Now that we presume that everything is a ok, lets see how dmraid is behaving, hopefully it sees the (logical, but not physical) device.

in Konsole, type 

"ls -l /dev/mapper/"

It should come up with a list of devices, the name of them will look a lot like gibberish, those are the ones.

Now, still in Konsole:

```
sudo testdisk /dev/mapper/whateverdeviceitcameupwithwhenyoulistedthem
```

Play around in the program and see if it sees a partition setup faithful to the one that you had setup. If not, post back, if so, then continue on.

Assuming since your continuing that the partition structure is indeed okay, we're going to try and mount them to see if the files are in fact fine:

"sudo mkdir /media/test1 /media/test2 /media/test3"

Now, with the device you got before, there should be more than one entry of it, There should be one without a number at the end, and then one with a one, two, three, etc, up to the number of partitions that exist on the volume. 

To mount them, it'd look something like this:

"sudo mount /dev/mapper/gibberish_1 /media/test1" for the first partition
"sudo mount /dev/mapper/gibberish_2 /media/test2" for the second partition

and so on. Granted, I've not mounted an ntfs partition in a while, it might be more involved, check this doc for more information: [https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

Try to look at the data and if everything seems okay, then all is okay. I kind of hope this is the case anyhow. Lets see, aside from that, you might be able to recover the master boot record by using the Windows Install CD, with some sort of repair option (if I remember correctly). Certainly do give that a go too. Good luck, and be sure to post back.

---

### Post by igloocentral on 2007-05-29
Your FakeRAID device is not supported by the main installation CD. If you try to install it anyway, you will get your current situation. Check your data, but I don't think it should be affected.

To install (K)ubuntu to your FakeRAID system, you'll need to use the Alternate CD (or the DVD) and one of the FakeRAID install methods. The quick-and-dirty one is called FakeRaidEdgy and the long-but-more-complete one is known as the FakeRaidHowto. (click one below) Post back if you have problems.

---

### Post by khayman80 on 2007-05-29
Thank you both for your suggestions.  

kuja:

As you suggested, I loaded my Windows CD and installed my RAID drivers, then the Windows recovery console was able to find my C:\WINDOWS installation.  I followed the following procedure (gleaned from other websites):

fixboot c:
fixmbr
bootcfg /rebuild

I thought it was kind of odd that fixmbr didn't give any output at all (although typing in fixmbr /? reveals help so I know the command is present), but there didn't seem to be any problems with these commands.  Unfortunately, rebooting the system gave the same "Error loading operating system" error.  

The rest of your suggestions appear to be oriented around making sure that my data is still intact, which I'm relatively sure it is.  Again, thanks.

igloocentral:

Wow.  Look like I should have done my homework before I installed Kubuntu on my RAID array.  I've glanced through FakeRaidEdgy and dear god does it look involved.  I'm sure that someone with a even a little experience with the linux command line would find it easy, but I'm almost a complete newbie.  Nevertheless, if I were to do this (assuming I can) then regardless of my previous attempt to install Kubuntu, would my windows installation be accessible again?  If so, I'll call this "plan B" and try to exhaust all other options before I dive into that procedure...

On a more practical note, is there any shorter way to accomplish my actual goal: to get my windows installation working again?  Frankly, at this point I'm wondering why the hell I wanted to tinker with linux in the first place, seeing the huge mess I've gotten myself into.  I really just want my computer (and all my data) back.  Maybe there's a shorter way to install GRUB only, so that it over-writes the boot sector (which the windows commands fixboot, fixmbr and bootcfg apparently couldn't accomplish)?

In any case, thanks for your suggestion.  It's always good to know exactly what went wrong, and what tactic I can use to avoid this problem next time (if there is a next time).

---

### Post by kuja on 2007-05-29
](*,)Though a bit (okay, a lot) lengthy, the FakeRaidHowto is both straightforward and comprehensive. It's involved, but everything has been handed to you on a silver platter. It tells you the commands to use (most of it is even copy+pastable). I've used it before and it works pretty well. 

For future installations involving Linux, or Linux+Windows dualboots, I personally recommend against FakeRaid due to the additional complications it throws in (as you've already found out). Perhaps one option is a spare hard drive to install linux on in addition to t he other hard drives in FakeRaid. Yet another option is to buy a real hardware RAID card. Another option yet is to not use RAID at all (if you don't really *need* it). 

I've no idea why windows isn't picking up on itself for you, it should. Perhaps a full blown repair or reinstallation is in order. Bah, windows is such a pain in the neck ](*,)

---

### Post by igloocentral on 2007-05-29
google keeps telling me that you should use "fdisk /mbr"

---

### Post by poppers1957 on 2007-05-29
I would find an old hard disk and load Linux on it.  At first install keep it the only HD connected.  When completed hook up as many  HD's you want, and set which to boot from in BIOS.  I have had a few problems with grub when I loaded Linux on free space of a drive.  Seems they just don't get along.  I believe it is Windows fault.  You can see and use the drives with the different formats in Linux, but not in Windows.  But Windows will let you reformat it to their requirements, doesn't that sound fishy to you.

But a solution to your data is this.  First get "File Scavenger".  It is a program that will find any data that hasn't been overwritten 3 times, works awesomely.  You will be able to retrieve your data. Then get Partition Magic and break down that 700 gig hard drive to smaller chunks.  It will run more efficiently.  And when you reload windows onto say a 50 gig partition, put your important data on a different partition, then you will not be as likely to lose it when Windows fails and needs to be reinstalled.  

Good luck.  I hope you will try Linux again.  It is a great OS.  And you will learn it quickly and come to enjoy the freedom.  But trying to mix anything Windows with it is like trying to mix a Chevy with a Ford.

---

### Post by khayman80 on 2007-05-29
igloocentral:

I've seen that suggestion in my googling as well.  Unfortunately, I've also seen stern warnings NOT to use it: [http://www.ntcompatible.com/How_to_remove_GRUB_loader_t28242.html](http://www.ntcompatible.com/How_to_remove_GRUB_loader_t28242.html) .  (See the post halfway down the page by jbirkett).  He says "You do not, i repeat, do not want to use fdisk /mbr with Windows NT or XP."

So I'm reluctant to try that.  Plus, I'd already tried to run fdisk (just to see the partition information) but it apparently isn't available (?!?) because I just get an "invalid command" error.  If I come to the conclusion that I need to run it, I think I'll have to go to bootdisk.com or something similar and burn a windows boot CD with fdisk on it.

I just talked to my office's resident hardware expert, and he advised me to do something similar to kuja's original suggestion.  He says to load the Kubuntu Live CD, open a terminal and type "linux rescue" which will apparently open another "shell" at which I can type in commands.  This is where I get kind of hazy on the specifics, but he said that if I look in the directory /proc/ide I will find out how many hard drives linux sees.  Because Kubuntu can't recognize RAID arrays by default, he thinks it will see two: hda and hdb.  Then he suggests typing fdisk /dev/hda (and /hdb) and typing "p" to print out partition table information for each drive.  Hopefully this will confirm the hypothesis that linux only over-wrote the MBR on one of the hard drives, and not the other.

I'm way out of my league here, but it seems that this disparity between the two drives could be the reason why Windows can't simply fix the problem with a "fixboot, fixmbr, bootcfg /rebuild" procedure.  If windows expects both drives to be identical in a RAID array, maybe the fact that they aren't the same is causing the problem.

I'm considering disabling RAID in the BIOS so that my system sees two separate hard drives, then either disconnecting the cable from both drives separately (pain in the *** b/c my comp is hard to open) or finding some way to disable one of the hard drives in the BIOS.  Hopefully when I disable the drive that has had its MBR over-written by Kubuntu, my system should boot normally.

The only reason I'm scared to do this is that I don't want to accidentally screw something up and lose all my data.  Ironic- the entire reason for my implementing a RAID1 array is that I'm paranoid about losing data, and it seems to be causing exactly that problem...

---

### Post by igloocentral on 2007-05-29
Your hardware guru is giving you good advice.

Read microsoft's (long) explanation:
[http://technet.microsoft.com/en-us/library/bb457122.aspx](http://technet.microsoft.com/en-us/library/bb457122.aspx)

In your situation I think the best thing for you to do is go through the FakeRaidEdgy procedure. It's not that hard, and at the end of it you will have your MBR fixed, GRUB installed and a working Ubuntu installation.

Before you do that, it would be handy to write down or print out a copy of your partition setup. Boot with the live CD and run something like:
sudo fdisk -u -l /dev/sda
sudo fdisk -u -l /dev/sdb

or
sudo cfdisk -Ps /dev/sda
sudo cfdisk -Ps /dev/sdb

Post the results.

I would like to add the solution to this to the FakeRaidHowto (when we get it figured out)...

---

### Post by khayman80 on 2007-05-29
Okay, I've decided to try the FakeRaidEdgy procedure.  I downloaded Ubuntu Alternate 64 v7.04, burned it and booted with it.  I also downloaded all the files listed in FakeRaidEdgy and put them on my USB stick.

The install process seemed to go fairly smoothly.  As instructed, I did not partition, but dropped to a shell from the menu.  I then mounted my memory stick, copied the udeb files and installed them using commands that make absolutely no sense to me, but I faithfully copied them.  No error messages in sight - the system just says "Reading database, Updating Database" when I installed libdevmapper-udeb abd dmraid-udeb.

I did not unmount my memory stick as suggested... didn't see the point.

Then FakeRaidEdgy says to type in "modprobe dm-mod" and then "dmraid -ay".  The first command produces no output at all.  The second simply says "/bin/sh: dmraid: not found"

Anyone know what's going on here?

---

### Post by khayman80 on 2007-05-29
Actually, I just noticed that I followed the links provided in the FakeRaidEdgy procedure.  Didn't notice that they're i386 and not ia64 versions.  I suppose I need the ia64 versions to work with my Ubuntu Alternate 7.04 ia64 install CD?

Also, does it matter that I'm using v7.04 rather than 6.10 as suggested in the guide?  I haven't been able to find a torrent for that version of Ubuntu (especially not the ia64 version).

Thanks again...

---

### Post by khayman80 on 2007-05-29
Now that I look through Debian's list of dmraid-udeb files, I'm wondering if I need amd64 or ia64.  I really don't know the difference.  I've got an AMD 64 x2 4200+ processor, so I'm betting on amd64, but I don't even know what ia64 means, so I thought I'd ask...

---

### Post by khayman80 on 2007-05-29
I've been downloading the amd64 versions, hoping that this will fix my problem (until someone more knowledgeable corrects me...).

So far I've found 3 of the 4 packages:

dmraid-udeb_1.0.0.rc13-2+b1_amd64.udeb
libdevmapper1.02.1-udeb_1.02.18-1_amd64.udeb
grub_0.97-28_amd64.deb

I found these by googling for PACKAGE_NAME deb (or udeb) and going to the most legitimate looking website that showed up in the results.

The 4th one (found at [http://http.us.debian.org/debian/pool/main/d/dmraid/](http://http.us.debian.org/debian/pool/main/d/dmraid/) )has two choices:

dmraid_1.0.0.rc13-2_amd64.deb OR dmraid_1.0.0.rc13-2+b1_amd64.deb 

Which should I choose?  (If, indeed, this i386 vs. amd 64 issue is causing the problem I described several posts back)

---

### Post by khayman80 on 2007-05-29
Okay, sorry for the spam, but I went ahead and installed the dmraid and libdevmapper "udeb" packages (still not sure which deb package I should install as per previous post, but I'm not there yet).

It seems to work.  dmraid -ay gives no output, but when I type "ls /dev/mapper" I now see two files in addition to control: "nvidia_hfjfcdca" and "nvidia_hfjfcdca1".

If I'm reading the FakeRaidEdgy tutorial right, I should only be seeing one file in addition to control, right?

Any ideas?

---

### Post by igloocentral on 2007-05-29
you're doing great.

i think nvidia_hfjfcdca1 is your existing partition with all your data on it. you can include it when you set up your partitions after you exit the shell and go back to setting up your partitions - set it up as an ntfs-type partition and mount it to the location /windows

keep going! you're almost there!

nvidia_hfjfcdca is the base hard drive. you can't mount that - it's only the "container" that holds all the partitions. in the partition setup you'll create partitions for your linux install and they will be nvidia_hfjfcdca2, nvidia_hfjfcdca3, etc...

---

### Post by khayman80 on 2007-05-29
After carefully reading the rest of the FakeRaidEgy article, I've come to the conclusion that I'm seeing my RAID array and the partition that's already on it- namely my precious, precious Windows XP partition.

How can I verify this?  Is there any command I can type that will show me the size of this partition or even allow me to mount it?

Also, I want to make certain that I don't over-write anything on this partition.  Since the FakeRaidEdgy tutorial doesn't seem to address the question of pre-existing partitions, is there anything I need to do in order to make sure that it doesn't touch the partition already there?

Thanks again for your help during my crisis...

---

### Post by khayman80 on 2007-05-29
ha!  thanks igloo.  guess I should have refreshed before I posted.  :)

---

### Post by igloocentral on 2007-05-29
to look at your partitions (there's only one right now actually):
sudo fdisk -u -l /dev/mapper/nvidia_hfjfcdca

when you set up your partitions, first start by setting everything to "Do not use" as it says in the directions. Then set your nvidia_hfjfcdca1 partition as /windows  - ntfs-type - this will mount it read only in ubuntu. you'll also mount nvidia_hfjfcdca2, nvidia_hfjfcdca3, etc as your linux partitions as per the wiki.

you're almost done!

---

### Post by khayman80 on 2007-05-29
I set up everything as "do not use" and told it to automatically partition the 20GB of free space.  It did so with 20GB of "/" and 937MB of "swap".

I figured it knew the best settings, so I said "okay" and said to "finish partitioning and write changes to disk"

Then I get a blood-red screen that says:

Failed to create a file system!

The ext3 file system creation in partition 2 of LVM VG nvidia_hfjfcdca, LV nvidia_hfjfcdca failed.

I chose "go back", of course.

Any more ideas?

---

### Post by khayman80 on 2007-05-29
Oh, also, should I be setting the flag on my #1 partition (with xp) to be "bootable"? (assuming I can get past this "failed to create file system" error).

---

### Post by igloocentral on 2007-05-29
I'm not sure what it will do if you tell it to "automatically partition" so i would suggest you do it manually. it sounds like the automatic way isn't working anyway.

look at the "Partition the RAID Array" section in the FakeRaidHowto (click link in my signature). you will end up running "sudo fdisk /dev/mapper/nvidia_hfjfcdca" - then create your partitions. i would recommend the following:

/boot partition - ext3 file system - size: 512MB
swap partition - linux swap type file system - size 2GB
/ (root) partition - reiserfs file system - size - whatever you have left - about 18GB

then you'll exit the shell and run the FakeRaidEdgy partitioner you've been looking at already.

i have to go out but i'll be back in about an hour.

---

### Post by khayman80 on 2007-05-29
When I type sudo fdisk /dev/mapper/blah, I get /bin/sh: sudo: not found.

According to the FakeRaidHowTo, I need to be running fdisk as an administrator (which, as I understand it, is what sudo does).  I tried going into fdisk without sudo, and it worked, but the warnings in the How To were dire enough that I'm not going to risk it.

---

### Post by igloocentral on 2007-05-30
i think you are root anyway. find out by using the command "whoami" which should return "root"

---

### Post by khayman80 on 2007-05-30
Oh, also, I'm playing around in fdisk (which should be safe as long as I quit using "q" unless I'm misunderstanding something), and I'm realizing that although I am fairly proficient with Microsoft's fdisk, I'm clueless about linux's fdisk.

I've deleted all but the 1 partition (think these were created by the automatic partitioner).  I've created a 2 partition which is 512MB in size, and set its bootable flag using the 'a' key.  I've created a 3 partition with 2GB of space, and a 4 partition with the remaining space.

Problem is their system all reads as "linux".  You've said to use ext3 for boot (2), linux swap for swap (3) and reisers for root (4).

I don't know how to do this.

Oh, as I'm writing this I noticed your message.  I tried typing whoami but also got a "not found" message...

---

### Post by igloocentral on 2007-05-30
you must  be root since you haven't created any users.

go ahead and save the partitions, exit the shell and go back to the partitioner. the partitioner should now see the partitions you've created and you can go in and set the filesystem type and mount point for each one.

---

### Post by khayman80 on 2007-05-30
got the same error message.  Failed to create a file system.  The ext3 file system creation in partition 2 of lvm vg nvidia_hfjfcdca, LV nvidia_hfjfcdca failed.

I'm sitting at the continue, go back screen...

---

### Post by igloocentral on 2007-05-30
so what do you get when you are in fdisk and you type "p"?

---

### Post by khayman80 on 2007-05-30
Part 1,2,3,4.  Part 1 is NTFS, part 2 is "Linux", part 3 is "Linux swap/Solaris", part 4 is "Linux".

---

### Post by igloocentral on 2007-05-30
well, you can continue on in the FakeRaidHowto and format your filesystems - then when that's done try the partitioner again? If you can make the partitioner happy, the install will then go ahead and do most of the work for you...

---

### Post by khayman80 on 2007-05-30
Uhh... I tried to read the section on formatting in the HowTo, but it's gibberish to me.  The author casually mentions how formatting is accomplished, but I'm so new to all this that I can't do much more than copy commands.  Plus I tried to run the commands he mentions, mkfs and mk2fs, but both of them were "not found".

Right now I'm fantasizing about paying an extra $270 for another 750GB drive+external enclosure, replacing one of my current RAID drives with the new drive, then completely reinstalling windows on the new array- wiping all the data in the process.  Then I could copy all the data from the one surviving drive back to the computer.

It would be expensive in terms of dollars and hours, but I'm pretty sure it would work, and at this point it seems like the only way I can get my files back.  With all the strange errors that I've been experiencing (sudo not working, file systems can't be created, whoami doesn't work...) do you really think that if I put another 5-6 hours of work into this that I have a good chance of recovering my windows installation?  Remember that all I really care about is getting my windows installation+files working again.  At this point getting Ubuntu working is a DISTANT second.  

I really wish there was some easier way to undo whatever Kubuntu did to my MBR.  Or a time machine, so I could go back in time and yank the Kubuntu CD out of my hands...

In any event, I really appreciate the time and effort you've put into helping me...

---

### Post by igloocentral on 2007-05-30
A time machine would be very handy!

Grub errors are probably the biggest problem everyone encounters. We're trying to convince the Ubuntu team to include dmraid in the main Ubuntu distribution so that people such as yourself do not get in trouble without it.

I tried installing Ubuntu to my Raid drives back in 2005 and soon gave up and installed it elsewhere. It took 2 years for the Raid support to get to where it is today. I finally came back to Ubuntu last month and installed it all the way. It's too bad... many people are still getting fed up and shelving their Ubuntu disk

Because your system has the Raid setup, it is suddenly a lot of work to install. You've doing well, but you're only  halfway there. There may also be a faster way that I don't know about. Good luck whichever way you go :)

---

