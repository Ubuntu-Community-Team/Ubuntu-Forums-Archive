---
title: "hi i wanna install ubuntu in new hp laptop"
date: 2008-08-03
forum: x86 64-bit Users
---

### Post by invid1 on 2008-08-03
i got this new laptop , i wanna make a partition to install ubuntu, ill keep windows to play 2 games that i like like leanege2 battlefield 2142, wow, diablo 2.
 but before doing it, i wanna see if do u think its a good move. this is the stats:

Model: dv5-1004nrProduct Depth10.2"
Processor BrandAMD
ProcessorAMD Turion(TM) X2 Ultra
Processor Speed2.1GHz
Display TypeWXGA high-definition widescreen display with BrightView technology and 1280 x 800 resolution
Screen Size15.4"
Cache Memory2MB on die Level 2
System Memory (RAM)4GB
System Memory (RAM) Expandable To8GB
Type of Memory (RAM)DDR2
Hard Drive TypeSerial ATA (5400 rpm)
Hard Drive Size250GB
Optical DriveDouble-layer DVD±RW/CD-RW
Optical Drive SpeedsDrive speeds not specifiedGraphicsATI RADEON HD 3200 graphics RS780M
Video MemoryUp to 1918MB total available
MPEG Yes
Built-in WebcamYes
Additional Audio/Video Connectors1 HDMI
SpeakersAltec Lansing
PCMCIA Slots1 ExpressCard/34/54
USB 2.0 Ports4
Operating SystemWindows Vista Home Premium 64-bit with SP1

so hopefully it will help u guys, btw im really new to linux, so pls explain to me in easy terms.
thanks for help
im trying to really get into linux, im tire of windows, really tire

---

### Post by Sef on 2008-08-03
Run the Live CD for a while.  If you have a problem with it, then almost certainly that problem will exist upon install.

---

### Post by xen-uno on 2008-08-03
Hell yeah man. The 250 GB drive ... partitioned? If not then you need to defrag the disk in Windows to try and move all the data forward to front of disk (may have to do it several times). After that, you need to resize your C: so that you can add 2 more partitions (2 GB for Ubuntu swap, 50+ for Ubuntu system) ... leave both unformatted (but not un-allocated). I don't know if Vista has partition resizing capabilities, or if the Ubuntu install disk does. I used Paragon Hard Disk Manager via XP to do mine.

1st off though, do an image burn of the Ubuntu x64 Live CD and see if it will boot and run. If you can't get to the Ubuntu desktop (you want to start Ubuntu, not install at this point) then I would suggest you go with the alternate install disk (I did). If you can get to the desktop, then you can use that disk to install (after setting up your partitions).

---

### Post by Ptero-4 on 2008-08-04
Both Vista and Ubuntu disks come with partition software capable of resizing partitions (don't know if the Vista one handles linux formated partitions though).

---

### Post by castor_troy on 2008-08-04
Download the Ubuntu 64 bit cd image and burn it onto a blank disc at low speeds 2x-8x. Boot with the cd in the drive and use the live cd.

Use it for a while. If there are any problems they will show up. The live cd will run considerably slow than an full install.

Dont worry about partitioning and stuff. If you have free space you can easily create partitions. Ubuntu Setup helps you with this in an easy graphical way when you run the setup.

---

### Post by Funk Phenomena on 2008-08-04
So it sounds like you're going to need to select Other Options on boot, x mark the acpi=off, esc, then install.  It disables wireless, sound and other stuff I can't think of, but search kubuntu tx2500 and you'll see a thread dealing with this.  But there is a how-to and while it's for a tablet, the specs are almost exactly the same, so I think you're in the same boat.  Though I can't get my microphone to work in cheese or skype...  Surprisingly the ir remote works without fiddling, though just some of the buttons.

But for the boot other options... Ubuntu thinks the laptop is overheating so shuts down by default.  Acpi=off prevents this, then you upgrade to proposed, blacklist thermal, set sound to toshiba, etc (as shown in the how-to).

---

### Post by Thelasko on 2008-08-04
> **Ptero-4 said:**
> Both Vista and Ubuntu disks come with partition software capable of resizing partitions (don't know if the Vista one handles linux formated partitions though).

I've used the Vista partition manager.  I've never used it to manage my ext3 file system, but I did use it (sort of) to create my Ubuntu partition.  I recommend it because you will be sure you didn't do any damage to Vista (I hear it's picky).  I just used it to shrink the size of my Vista partition, and left the space I planned to install Ubuntu unformatted.  When I installed Ubuntu, I just told it to install on the unformatted section of the harddrive.

I believe I learned how to do it from [this article]("http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm").  It's been updated since I first read it.

---

### Post by Dougie187 on 2008-08-04
Also, make sure you check out wine for your games, I know that at least Diablo 2 and WoW both work fine under wine (i actually play Diablo 2 on it, and have tried WoW on it before). Im not sure about the other two, but its worth a shot. Then you won't have to reboot just to play games (i use to do that and its a total pain, you end up spending more time in windows, just because you want to game) but it should work, its not too hard and there are guides out there to help you with the task. Good luck!

---

### Post by thegnark on 2008-08-04
The guide for the tx2500 in my sig may help you out getting things installed & configured if you're having difficulty

---

### Post by bambam123 on 2008-08-23
Here is another tread on the dv5-1004nr laptop and the issues I found

[http://ubuntuforums.org/showthread.php?t=884749&highlight=dv5-1004nr](http://ubuntuforums.org/showthread.php?t=884749&highlight=dv5-1004nr)

---

### Post by elmoosecapitan on 2008-08-23
Your computer specs are perfectly fine, you should not run into any major problems. The only issue I foresee, something that we all eventually face, is not finding that everything is fully compatible, i.e., flash-10 on firefox 3.0.x. It can be frustrating at times (like this morning). You eventually discover workarounds and hacks, so don't worry. Good luck and welcome to the open world!

---

