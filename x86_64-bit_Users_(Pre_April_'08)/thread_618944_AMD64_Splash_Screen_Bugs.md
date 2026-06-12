---
title: "AMD64 Splash Screen Bugs"
date: 2007-11-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by ap0c0lyps3 on 2007-11-20
Ok, so where do I start....  1 - I just installed Linux Ubuntu 7.10 Gutsy Gibbon on one of my machines...  This is the very first OS other than Win9x-Vista OS I have messed with...  Needless to say I had no clue what to expect when I dipped my hands in what I have gotten myself into...  I have been told I'm nuts for doing it the way I did...  I have been told that I cannot fix this issue, but now I've come down to...  Hey...  The best way for me to learn how to fix it is via the longer method... Not just reinstalling everything...   If I reinstall everything.... I don't learn what I did wrong in the first place...  As well...  After hours on end of research trying to figure out the solution to this problem, I have found out that it is a very BIG issue with the AMD64 Gutsy Gibbon.  I will go ahead and state a few minor things up front...

System Specifications:
2GB of RAM ((DDR 333MHz, PC3200))
AMD Athlon 64-Bit Dual-Core 4200+ Processor (Socket 939)
250 GB of HDD Space ((7.2k RPM, 8MB Buffer))
PCI-E NVidia Geforce 8800 GTS 320MB ((possibly 640))
OnBoard Sound Card Realtek '97 Audio


Ok, now that we have that out of the way....  I began my journey with Vista on my back, and confidence in GRUB's ability to sort through my OS's without having to much configuration (actually none at all)...   When I first inserted the actual LiveCD (AMD64) to install with, it booted to the CD's Boot Options fine....  However whenever I chose to run the LiveCD and/or install....  The screen would immediately black out on me, and my monitor would lose all signs of connection with the system...  Now after rebooting mutliple times and coming to the conclusion Linux didn't like me... I just left it be...  Now after sometime had passed in the midst of me getting up and moving over to play Halo 3... I heard a sound from my speakers...  Nearly 10 minutes had passed and it actually booted completely into Ubuntu...  I was astounded, but extremely happy... I went ahead and installed Linux on another partition...  Now after I completely rebooted and booted the hard drive and chose gutsy to boot... It did the same thing again on the splash screen...  This time around though it only took approximately 1 minute to completely boot to the Login screen.  From there I went ahead and updated my drivers and began my journey with Ubuntu...

Now after my 2 days of falling in love with Ubuntu and its abilities...  I came across how to edit my menu.lst ...  Not to great of an idea for a beginner to mess around with, but after troubleshooting as to why my splash wasn't working... I promptly removed the quiet splash and found out that I needed to add vga=791 (I do not know if this is proper or not, as I do run DVI on my system, but I use a VGA to DVI Dongle for my system to connect to my monitor)...  After booting up like this, I realized that the splash was running properly, and the video driver was loading properly...  I could see the Text Splash now atleast...

Welp, I had the intelligent idea to go ahead and attempt to add a splash screen...  After I edited the menu.lst file and attempted a reboot... I recieved an Error 17, and could no longer boot to ANY OS...  I quickly went ahead and reinstalled Ubuntu 7.10 and whiped my ENTIRE drive...  After that I went ahead and came about it another way... I gave it a nice attempt to install usplash on my system...  That time around it caused the system to boot up splash screen and now I am recieving the error of..

VFS: Cannot open root device "UUID=6cc5a988-8f5c-4c30-a814-b02e555905d0" or unknown-clock(0,0)
Please append a correct "root=" boot option; here are the available partitions: (none listed)
Kernel Panic - Not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

Now...  This specifically happens each time I try to mess with my splash screen...  Perhaps the darn this is bugged beyond belief? YAH!

---

### Post by CorlanMcD on 2007-11-24
I'm surprised the "vga=***" code help you, as it didn't nothing to help my "black screen," "input not supported" problems. For me to boot, I had to remove "quiet splash" so I know get the classic bootup listing all the preboot processes, fun (it works though)!

Don't mess with the boot stuff/menu.lst too much, as you can see :). it messed me up as well.

---

### Post by John Jason Jordan on 2007-11-24
> **ap0c0lyps3 said:**
> That time around it caused the system to boot up splash screen and now I am recieving the error of..

VFS: Cannot open root device "UUID=6cc5a988-8f5c-4c30-a814-b02e555905d0" or unknown-clock(0,0)
Please append a correct "root=" boot option; here are the available partitions: (none listed)
Kernel Panic - Not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
Here's whatcha gotta do.

1) Boot to the recovery mode. To do this, when you see Grub starting to load on your screen (right after the BIOS stuff) hit Esc. That will take you into the Grub menu list so you can choose the Recovery mode option. Recovery mode will boot you to a command line. From there you can edit the menu.lst file (nano /boot/grub/menu.lst). See information below for editing the menu.lst file.

2) If this doesn't work, use the live CD to boot (I actually prefer a Knoppix or Slax live CD) and after it boots see if it has mounted your hard drive. If so, continue below. If not, download Knoppix or Slax or something that will boot from a live CD and mount your filesystem.

EDITING menu.lst:

3) Once you are running, open a terminal and type 

sudo tune2fs -l /dev/hda2

Where you change hda2 to what your root partition is called. For example, if it is a SATA drive it will be sda#. The # refers to which parition on the hard drive it is. For example, when I set up my computer I created a swap partition first, so the swap is sda1. My root partition is sda2. 

4) The above command will give you the UUID= number of your root partition. A UUID number is a long-*** number referring to a specific point on the hard disk. Copy the number, open /boot/grub/menu.lst (as root), insert the correct UUID number in the boot line, and save the file. When you reboot all should be well.

ALTERNATIVE IF THE ABOVE FAILS:

Assuming you know what your device is (hda1, hda2, sda1 etc.) when the Grub boot menu comes up hit Esc and then e. This will allow you to edit the menu on the fly. Any edits you make here will not be saved, so if what you do here allows you to boot, once you have booted, open menu.lst in a text editor and make the changes permanent.

Once the entry is up in edit mode, arrow down to the boot line and hit e again. This allows you to edit the boot line. Delete the UUID= line at the end (including the UUID=) and replace it with /dev/hda1 or whatever your root partition is called. Grub will boot this way instead of a UUID= number. There has been a lot of discussion why Grub insists on using a UUID number, pros and cons, but you can research that later. For now, just stating the dev/xxxx should get you booted.

Looking over what I wrote it is a bit disjointed but I'm in a hurry tonight and don't have time to write a dissertation. Hopefully you can figure out what to do. If not, post back and we'll try again.

---

### Post by Laryllan on 2008-01-02
Please take a look at this solution:
[http://ubuntuforums.org/showpost.php?p=4057740&postcount=3](http://ubuntuforums.org/showpost.php?p=4057740&postcount=3)

Maybe it works for you too.

---

