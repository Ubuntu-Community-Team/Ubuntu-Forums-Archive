---
title: "Powerbook Dual-Boot"
date: 2006-04-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by ismh on 2006-04-06
I have a 15-inch (1.33Ghz/1.5GB RAM) Powerbook that I want to dual-boot OS X and Ubuntu 5.10. I have the Ubuntu install (PPC) CD in my hand.

How do I partition my hard drive so OS X is the default OS? I assume I need 3 partitions- 1 for OS X, 1 for Linux, 1 for boot loader. How much space can I make the Linux one? I would like enough room to play with, but not a ton. 4GB enough? How big should the bootloader part. be?

Is there a way to hide the bootloader so it only comes up if a key combo is pressed at start-up?


I am new to this, sorry. I have years of Max experience, but this is new to me.

iSMH

---

### Post by linear on 2006-04-06
You don't need to make the bootloader partition yourself. First read these:

[https://wiki.ubuntu.com/Installation/PowerPC]("https://wiki.ubuntu.com/Installation/PowerPC")
[http://www.askdavetaylor.com/how_do_..._mac_os_x.html]("http://www.askdavetaylor.com/how_do_i_dual_boot_ubuntu_linux_mac_os_x.html")

This worked for me:

1. Back up OS X partition. ([Carbon Copy Cloner]("http://www.bombich.com/software/ccc.html") works well.)
2. Repartition disk. Make two partitions, leave first as free space and second for OS X. Disk Utility is destructive (another reason for the back up), or there is a howto [here]("http://ubuntuforums.org/showthread.php?t=89960") on using **parted** to resize non-destructively. A partition of 4-5GB should be fine.
3. Boot from the Ubuntu install disk. When you get to the partitioning step, tell the installer to use the largest free space. It will take care of the rest.

---

### Post by moldor on 2006-04-16
[QUOTE=linear]You don't need to make the bootloader partition yourself. First read these:

[https://wiki.ubuntu.com/Installation/PowerPC]("https://wiki.ubuntu.com/Installation/PowerPC")
[http://www.askdavetaylor.com/how_do_..._mac_os_x.html]("http://www.askdavetaylor.com/how_do_i_dual_boot_ubuntu_linux_mac_os_x.html")

This worked for me:

1. Back up OS X partition. ([Carbon Copy Cloner]("http://www.bombich.com/software/ccc.html") works well.)
2. Repartition disk. Make two partitions, leave first as free space and second for OS X. Disk Utility is destructive (another reason for the back up), or there is a howto [here]("http://ubuntuforums.org/showthread.php?t=89960") on using **parted** to resize non-destructively. A partition of 4-5GB should be fine.
3. Boot from the Ubuntu install disk. When you get to the partitioning step, tell the installer to use the largest free space. It will take care of the rest.[/QUOTE]

Hi gang,

My experience was almost an anti-climax. It installed perfectly and I now have a dual-boot Powerbook G4. Here's a step-by-step of how I did it;

1. Defrag the hard drive - I used Drive Genius, but anything else that you're familiar with will work fine.

2. Also using Drive Genius, I reduces the size of my MACOSX partition from 97Gb (100Gb drive) to 82Gb, leaving me around 15Gb for Kubuntu.

3. Reboot, holding the C key down, into the Kubuntu installer.

4. When you see the partition map, and I should have photographed it at the time, you'll see an Apple partition as #1, then some free space (135Mb on mine), then your OSX partition, then the rest of your free space. It is important that you create a NewBoot partition in that first Free Space area just after the Apple partition.

5. Create a partition for SWAP, same as your RAM size is a good rule-of-thumb - mine is 2Gb.

6. The remainder of the free space after the OSX partition is for Kubuntu, mounted as /. You could create a /home partition as well if you have the space, but as you can create files in your OSX partition anyway, in your normal user account, it doesn't seem necessary.

For the rest of the install, basically just follow the prompts. I tyhink I just took all of the defaults and it works fine.

Only three things left to do;

a. Get my Airport Express card working
b. Have MACOSX as the default OS in the boot menu
c. Make the font of the boot menu bigger (it's about 6 point at the moment !!!.

Interestingly, when it was copying from the CD to the hard drive, it said it was going to take 49710d 6h 28m 15s to complete - that's over 135 years !!

Rule: NEVER trust the time estimate !!!

---

### Post by RAV TUX on 2006-04-18
just curious...any plans to set up a triple boot?

ubuntu/mac/xp?

---

### Post by AlphaMack on 2006-04-18
I'd suggest creating three partitions - one for OS X (first and approx 8-16+ GB depending on what you have for apps), one for Ubuntu (free space...if you want a /home, maybe add 1-2 GB), and one for data storage for both (HFS+, WITHOUT journaling).  Use Disk Utility to accomplish this on your OS X installer.  Install OS X first.  Then install Ubuntu.  When you get to the partitioner, have it automatically partition the free space but don't commit to the changes.  Resize the / (ext3) partition so that you have more free space for /home.  Take the free space and "create" a partition out of it.  Ubuntu will automatically assign it as /home.

Once you have Ubuntu up and running, edit your /etc/fstab to have it automatically mount that third partition.

Enter the following:

/dev/hdaX /mnt/nameofhd hfsplus defaults 0 0

where X is the partition number (get it from System->Admin->Disks) and "nameofhd" is the name of your partition (whatever you choose).  Now create a folder in /mnt with "nameofhd."  In the Disks program, enable the partition (and it should already have the path to the mount point you just created!).

---

### Post by projectle on 2006-04-18
As a note...

49710d 6h 28m15s
 - or - 
4294967280s
 - or - 
11111111111111111111111111110000

A full 32-bit register with the 4 least significant bits disabled.

Either way, this is an obvious glitch in the counter to determine how long each package fetch takes. All counters that I have worked with in the past start assuming that it will take an infinite time to complete the task (assume full 32-bit register fully active, not last four disabled), compare to some value, where $remaining_time = ($download_speed / $remaining_size);

One variable may be undeclared or mistyped in that calculation, in turn resulting in a possible divide by zero error.

---

### Post by maxdevis on 2006-05-03
[QUOTE=moldor]

Only three things left to do;

a. Get my Airport Express card working
b. Have MACOSX as the default OS in the boot menu
c. Make the font of the boot menu bigger (it's about 6 point at the moment !!!.
[/QUOTE]

[http://www.askdavetaylor.com/how_do_i_dual_boot_ubuntu_linux_mac_os_x.html](http://www.askdavetaylor.com/how_do_i_dual_boot_ubuntu_linux_mac_os_x.html)
To modify yaboot so that the default operating system is actually Mac OS X isn't too hard. There&#65533;s a great yaboot reference document online at the yaboot site. It turns out that the change is trivially simple: in the file /etc/yaboot.conf on the Linux side of things, you simply needed to add the line defaultos=macosx.

---

### Post by Ptero-4 on 2006-05-03
> 
riginally Posted by moldor

Only three things left to do;

a. Get my Airport Express card working
b. Have MACOSX as the default OS in the boot menu
c. Make the font of the boot menu bigger (it's about 6 point at the moment !!!.


The yaboot font is IIRC unconfigurable. It's done like that b/c someone big decided that mkaing it like that and making yaboot text-based instead of gui-based would satisfy the "boss" interests.

---

### Post by BlastXng on 2006-05-03
[QUOTE=yozef]just curious...any plans to set up a triple boot?

ubuntu/mac/xp?[/QUOTE]

Triple Boot will be interesting in the future, but you have to have a dual-core Intel Mac from Apple. XP won't work natively on PPC G3/4/5.

Check this that allows virtualization on Mac Intel boxes:
[http://www.geek.com/news/geeknews/2006Apr/lab20060427035971.htm](http://www.geek.com/news/geeknews/2006Apr/lab20060427035971.htm)

According to what I am hearing some folks are trying to get Ubuntu, Windows XP and Mac all running at the same time. Ubuntu and XP would be Virtual Machines on top of OSX.

I Digress.

As it relates to getting Linux (YDL, FC5, Ubuntu/Kubuntu) running on a Powermac, the best way I have found to do this is to back up the data. Boot from OS9 CD or X if you'd like. 

Create 2 partitioins. 1 OSX the other unused. Osx should be first.

Install OSX.

Reboot with CD for Linux and install to unused partion. partd should see the unused one for you on your Mac and automatically set it up for you if you let it, which includes modifying the boot partition that Apple installs to provide you with a menu choice at boot time. :p

---

