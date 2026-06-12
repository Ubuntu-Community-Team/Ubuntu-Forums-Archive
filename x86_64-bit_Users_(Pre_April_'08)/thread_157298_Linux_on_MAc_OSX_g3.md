---
title: "Linux on MAc OSX g3"
date: 2006-04-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by L1nVx on 2006-04-08
Hey i've been trying to get linux onto my comp

i've posted here [http://www.ubuntuforums.org/showthread.php?p=903514&posted=1#post903514](http://www.ubuntuforums.org/showthread.php?p=903514&posted=1#post903514)

they sent me around here 

so anyways basicalyl i think we figured out either it's my disc or i'ts the fact that i don't have apple firmwire cd or something it's just a regular cd-rom.... what can i do about this......

Like is there an update to update my cd-rom for that so it'll let linux boot or how can i get my cd-rom to boot linux....

---

### Post by rfruth on 2006-04-08
Will it boot any (bootable) CD everytime  (gotta hold down the C key)  ?

---

### Post by L1nVx on 2006-04-08
i dont have any other bootables except xp witch didn't work but since that's windows i didn't expet it to

---

### Post by linear on 2006-04-08
Did you verify that the iso you downloaded was good? (MD5 checksum)

Exactly what model Mac is this?

---

### Post by rfruth on 2006-04-08
Never heard of a of a G3 firmware CD (I have a G3 iMac with Panther on it) does your CD  drive work okay ?  (the XP CD should boot ((not run)))  Appledotcom has an active group [http://discussions.apple.com/forum.jspa?forumID=884]("http://discussions.apple.com/forum.jspa?forumID=884")
they may have a quick snappy answer cause I don't :confused:

---

### Post by L1nVx on 2006-04-08
i don't know exactly what model mac it is and i know the cd rom works b/c it played a music cd on the mac fine.

---

### Post by davygravy on 2006-04-08
[QUOTE=L1nVx]i don't know exactly what model mac it is and i know the cd rom works b/c it played a music cd on the mac fine.[/QUOTE]

One can know/identify a Mac by its color, in part...

Is it Beige?  (OldWorld)

================

Is it Blue & White?   (pretty much all NewWorld, I think)

Is it Gray/Graphite?

Is it White?

Does it have Mirror Drive Doors on the front?

Is is a funky iMac (clear or wild color)

...........


If it is Beige, then you will have to install/boot with BootX (can be a bit challenging)...

If it is one of the colors below the ========== line, then you are probably lucky, because it should boot up w/ the Live CD or the Install CD.

Are you sure it is a G3?  How do you know?

davygravy

---

### Post by linear on 2006-04-08
It's still not clear that the Ubuntu CD is good. When you boot in OS X, is the CD readable?

---

### Post by davygravy on 2006-04-08
Linear is right - the CD has to be good.  But if it is a Beige (OldWorld) you won't be able to boot it successfully unless you have BootX installed in OS 9.

davygravy

---

### Post by L1nVx on 2006-04-09
okpay thanks i'll have to work on it :) i'll get back to you with any news i'm only having this mac probably for a week or so so i may just not do it if it's gonan be "this hard" or whatever but we'll see right now im' going to bed tho haha :)

---

### Post by teripittman on 2006-04-09
This worked on a Beige G3. I happened to have the Yellow Dog disks, which had BootX on them. I found this on a few searches on the net. Hope it helps. You do need to have OS9 installed on the old world G3. And don't expect to get a resolution over 800x600 if you have the AV personality card installed.

Notes on Ubuntu install/Mac G3

Requires:
Ubuntu install disk
Mac OS 9
BootX (used Yellow Dog Linux disk)
A keyboard with the F function keys

Mac OS 9 MUST be installed on HFS standard, not HFS extended. 
I used a 1GB partition for Mac OS. It takes under 300MB so I could have used a smaller one. Use the Mac disk tools to format and leave the rest of the drive as unallocated.

Boot back into OS 9. Copy the BootX files into the system folder, along with the Linux Kernels folder. I also added miBoot but have yet to use it. I used the Yellow Dog Linux disk for this part. Then I used the Ubuntu disk for the vmlinux file. Copy the initrd.gz file to the System folder and rename ramdisk.image.gz. 

Boot again. When the BootX panel comes up, change the ramdisk size. I used 24000 and it seemed to be plenty. You can turn off force video in the options, but I didn't notice any difference. Click on Linux and you are off!

Follow the install until it hits the part that says &#8220;You don't have a boot loader installed.&#8221; At this point, use Option + F2 to open a new terminal. Click on Enter to activate. First, type in df. Look for the target. The number is what is important. The target on my system is hdb7. 
Type cd /target 
mkdir hfs 
mount /dev/hdb6 hfs -t hfs  (Basically, you subtract one from whatever partition your target is.)
echo '/dev/hdb6 /hfs hfs defaults' >> etc/fstab
cp boot/vmlinux hfs/System\ Folder/Linux\ Kernels/vmlinux
cp boot/initrd.img hsf/System\ Folder/ramdisk.image.gz

These commands make an hfs directory for you to copy the Mac OS stuff into. You are then copying the boot files into your linux system. If you used HFS+ for the Mac OS stuff, you'll see a file called Where_Have_All_My_Files_Gone? That's the key that you need to start from scratch.

Use Option + F1 to switch back to the install screen and write down the root=/dev/hdb7 line so that you won't forget it. You'll put this option on the BootX screen. It should finish up and restart the computer. When the BootX screen comes up, add the root= line in the appropriate place but DON'T turn off the ramdisk (YDL has you turn it off.) It should boot into Linux and finish the install.

Other stuff:
For my Palm, I used /dev/ttyUSB1. I had it autodetect my modem and put in the appropriate port. That's all it took!

---

### Post by teripittman on 2006-04-09
One last thing not on that list, if you use a USB keyboard and mouse, you need to scrounge up an old style Apple mouse. When BootX loads, it comes up before the USB drivers load. So your USB mouse won't work and you won't be able to choose a linux boot. And Ubuntu will happily run both the Apple & USB mouse at the same time. I just leave the Apple mouse plugged in. It lets me use a USB port on my keyboard and still have a mouse when I need it.

---

### Post by 3rdalbum on 2006-04-09
[QUOTE=teripittman]One last thing not on that list, if you use a USB keyboard and mouse, you need to scrounge up an old style Apple mouse. When BootX loads, it comes up before the USB drivers load. So your USB mouse won't work and you won't be able to choose a linux boot.[/QUOTE]

Or you could put BootX in your Startup Items folder, so it loads after the Finder.

---

### Post by jdp on 2006-04-09
Looking at your other thread, it's mentioned that your G3 is green and white, so it sounds like an iMac but you mention swapping in a CD drive.  I assume we are talking about a B&W (Blue & White) G3.  The B&W has a tower case with rounded handles on top and the multicolored look of the iMacs.  Does it look like this: [http://lowendmac.com/ppc/g3c.shtml](http://lowendmac.com/ppc/g3c.shtml)

If so it's NewWorld and you cna boot it directly from the Ubuntu CDs if they have been burned properly.  Those do tend to be picky about CD drives and master/slave configs.

---

### Post by nkbj on 2006-04-11
[QUOTE=teripittman]
Mac OS 9 MUST be installed on HFS standard, not HFS extended. 
[/QUOTE]

You can use HFS+ for Mac OS 9. Then you just have to use '-t hfsplus' when you mount it in Linux.

Regards,
Niels Kristian

---

