---
title: "64-Bit v 6.10 not booting"
date: 2007-02-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by Capt.Marion on 2007-02-17
Okay, I recently installed Ubuntu 64-bit 6.10 on a second partition, the first one having windows XP home. Installation went fine. Now, when I select Ubuntu to boot to in the GRUB boot loader,  I get the black screen with "Ubuntu" and what looks like the loading things (grey hash marks) below that. After 5-10 minutes, the screen changes to a command-prompt style thing saying 


"BusyBox V1.1.3 (Debian1.1.3-2ubuntu30 Built-in Shell (ash)"

/bin/sh: can't access tty; job control turned off

any help?

Thanks from a Ubuntu Nub
Capt.Marion

EDIT: Duh, system specs:

AMD Athlon X2 64 4400+
WD 300 gb hard drive
nVidia 7600GS Graphics Card
Creative X-Fi Soundcard
nVidia-chipset Gigabyte K8N Pro-SLI Motherboard
1 Gig RAM

---

### Post by pay on 2007-02-17
Make sure that grub is pointed to the right partition. Also, [here's](http://www.ubuntuforums.org/showthread.php?t=279884) a similar thread.

---

### Post by Capt.Marion on 2007-02-17
and I would do that how?

EDIT: Never mind. Right now I am downloading the 64-bit alternative install CD. We'll see how that works

---

### Post by pay on 2007-02-17
```
sudo fdisk -l
```That will tell you what partition grub needs to point to and then ```
sudo nano /boot/grub/menu.lst
```and make sure that it is the same partition that you got from fdisk. [This](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=10) will hopefully help you understand howto edit the grub file. Goodluck.

---

### Post by Capt.Marion on 2007-02-18
alright, I even tried the Kubuntu alternate CD, hoping there would be some difference...

its still hung up looking for root whatever...

I have a 300 GB disk, with three partitions:
1-136 GB NTFS with Windows XP Home
2- 83.82 ext3 with, supposedly, Kubuntu 64-bit on it
3- 58.92 MB- Swap Space (does this need to be bootable?)

I would assume my Root partition is the 2nd one...

when I tried sudo fdisk -i, it gave me a bunch of stuff about fdisk, but nothing about my harddrive or my partitions...

sudo nano /boot/grub/menu.lst gave me nothing....

---

### Post by Colonel Kilkenny on 2007-02-18
I had to use noacpi (or something like that) when loading the kernel (*-10?) which comes with Edgy. Kernel update (*-11) fixed that problem but the usplash image is still exactly like you described. Grey and broken.

You could try to edit the corresponding line in grub (let grub start and then press e and to the correct line add "noacpi" to the end) and then boot tr to boot with it.

---

### Post by Capt.Marion on 2007-02-18
It seems like it just can't find the root... I've tried pointing GRUB to the right partition, and I even installed LILO boot manager, and it still didn't work... still looking for some file or folder or other...

---

### Post by tgm4883 on 2007-02-19
isn't 60GB of swap space a little much?

---

### Post by John Jason Jordan on 2007-02-19
> **Capt.Marion said:**
> It seems like it just can't find the root... I've tried pointing GRUB to the right partition, and I even installed LILO boot manager, and it still didn't work... still looking for some file or folder or other...
Grub uses some odd syntax that can screw you up. If Grub is not finding the partition where the kernel is located there are a couple of lines where the problem might be located.

The following instructions may be too elementary for you. If so, ignore them.

The first thing to grasp is that the boot menu you see on screen is controlled by a file called /boot/grub/menu.lst. You have to be root to edit the file, so open a terminal window and type:
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.old 
Which will make a backup of the file, and then:
sudo gedit /boot/grub/menu.lst
Which will open the menu.lst file in Gedit with editing privileges. 

Scroll down to the place where it lists the menu entries. That will be a place that will look something like this:

## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=b784928a-d61f-445c-8575-3205597f421d ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

Those are the first two entries in my menu.lst file. I call your attention to a few things in those entries. First note after the root line it says "(hd0,1)." That is Grub's way of saying /dev/hda2. Grub calls the first hard disk 0 and the first partition on it 0. So "hda" in Grubese is hd0 and hda2 in Grubese is (hd0,1). Odd, but that's the way Grub thinks.

Second, note the end of the kernel line on the two entries. The first one says root=/dev/hda2 and the second one has a big long *** string of numbers and letters. Now, the location of root was already stated on the root line we just talked about, so I don't understand why Grub needs it repeated, but I guess it does. Probably Grub don't read so good. Whatever. But more important is that the location of the root partition is stated differently in the two entries. That is because yours truly edited the first one to read /dev/hda2 because that entry used to have the same big long *** string of numbers and letters as the second one. And guess what? That string of numbers and letters specifies a particular sector on the hard disk where Grub expects to find the root partition. Unfortunately, when I upgraded my old Dapper to Edgy the install utility mucked things up and specified a UUID for hda3 instead of hda2. I was unable to boot until I manually edited that line and set it to /dev/hda2. Note that should also edit the second entry to /dev/hda2, I just haven't gotten around to it. Actually, there is a command I could use that will tell me the UUID for /dev/hda2 and Linux purists tell me that the UUID is a better way to specify the location of the root partition, but I'm not going to bother. /Dev/hda2 works and I don't care. It's odd that Grub needs the root line to state (hd0,1) but will take normal syntax for the kernel line. And computers say humans are illogical.

So now that you have had a mini tutorial on editing the menu.lst file, maybe you can fix it so it will boot to the proper partition. There is also a complete Grub manual available on lots of sites online that you can download and print out so you will have something to read when you can't sleep.

Hope that helps.

---

### Post by Capt.Marion on 2007-03-02
TMG- yes it is, that's why it was a typo... 60 MB I'm purdy sure.

I will try your idea John Jason Jordan, but for now I have given up and removed Linux for a while. I'll try again another weekend. Thanks all the less, guys...

---

### Post by tgm4883 on 2007-03-03
isn't 60mb kinda small?

Does it boot into the wm from the live cd?  Have you tried feisty?  I was having trouble with 6.10 on my X2 3800+ because it wasn't fully supported by the kernel.  Feisty works great though.

---

