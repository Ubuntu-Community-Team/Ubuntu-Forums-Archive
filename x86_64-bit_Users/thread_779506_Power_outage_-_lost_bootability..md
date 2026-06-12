---
title: "Power outage - lost bootability."
date: 2008-05-02
forum: x86 64-bit Users
---

### Post by stalthar on 2008-05-02
Hey everyone, I've been using Ubuntu for about 6 months now on my AMD64, but I'm new to posting. Searched all over but couldn't find an answer. Here's what happened. The power in my apartment complex blinked off for a second and my desktop running Hardy switched off. When I turned it back on, it said that there was not a valid boot device. I booted to the Hardy live cd and opened GParted from there and there is an ! next to my /dev/sda2 drive (ext3, boot). I ran the check and repair option and got the message: 

"The superblock could not be read or does not describe a correct ext2 filesystem. If the device is valid and it really contains an ext2 filesysem (and not swap or ufs or something else), then the superblock is corrupt, and you might try running e2fsck with an alternate superblock: e2fsck -b 8193 <device>

e2fsck 1.40.8 (13-Mar-2008 )
e2fsck: No such file or directory while trying to open /dev/sda2"

So I opened a command prompt and tried e2fsck -b 8193 /dev/sda2 and got back the exact same result.

On my work computer, I downloaded the GParted live cd, burned and booted my laptop to the cd. When the gui opened, there was not an ! next the partition. I thought this was excellent, and ran the check/repair again. It came back saying that there were no errors and everything was fine. I rebooted and came up with the no boot device error message again. Hardy live cd booted, opened gparted, and the ! is back with all my error messages when I try and check/repair.

Does anyone know if there is a way to fix this, or am I stuck reformatting? I didn't have much stuff on this partition, as most of it was on external drivers, but I don't really want to go through the tweaking and customizing of Ubuntu all over again. Is there any more information I can provide? Thanks!

---

### Post by Sef on 2008-05-02
Sounds like a partition got messed up.  I would use [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") to see you can fix the problem.

---

### Post by Gripp on 2008-05-03
i'm not completely certain, as i use Wubi, but if you have windows installed you may be able to go in and run chkdsk <drive>: /F 
i believe it checks ext3, etc. partitions, at least it does with my Wubi install.. and fixes bad sectors errors that keep me booting linux just fine

if not, you may be able to fsck from a live cd on that partition.  

this may be helpful, at least it fixes almost all of my boot problems: boot from live cd and fire up the terminal and enter:

```
sudo mkdir /win
sudo mount -o loop /media/<nameOfMyDrive>/ubuntu/disks/root.disk /win #(or in your case just a normal mount)
sudo chroot /win /bin/sh
update-initramfs -u
```

then reboot to your install.  if it recognized the drive on the mount command, then maybe all is not lost...

lastly, if nothing else works you could use LVPM to recreate that install, if it can read from it, to a new partition.  i'm only 99% but i dont think you will loose any of your customization if you do it this way.  then just remove the old partition. 

good luck!

---

### Post by stalthar on 2008-05-03
Thanks for the suggestions! I'm out of town for today, but I'll be back with my dead desktop tomorrow and give it a try. Thanks!

---

### Post by stalthar on 2008-05-04
Thanks for the tips. I tried running testdisk and fsck, but neither one worked. Testdisk ran checks on the partition but they all came back ok. It did successfully display the file list, as well. I tried having testdisk fix the MBR, but that did not fix my problem either. Since it seemed to be an issue with the MBR, I tried installing grub again, as per the directions at [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) but this failed at the point where grub started the actual installation.

So tonight I being the task of reinstalling Ubuntu. I'm not too broken up about it, though, as the previous installation was my first one and then upgraded to Hardy, so I'm excited to have a clean Hardy to work with.

Thanks again.

---

### Post by stalthar on 2008-05-04
Heh, worse than I though. I used gparted to delete all partitions, booted the Hardy liveCD, went through the install, and rebooted to get to my fresh new system. Before hitting grub, though, got the error again: Disk Boot failure, insert system disk and press enter

So it looks like I'll be ordering a new HDD from tiger tonight :)

---

### Post by stalthar on 2008-05-04
Last post, I promise. I just ordered my new HDD, and for fun decided to install ubuntu to my flash drive so that I could access my data drives and burn some cds for work (hard to do while running a live cd). So I went to my bios to turn on booting from USB and just for fun, check out my hdd boot order. For some reason, these were backwards! It was trying to boot from my internal data drive before my internal boot drive, and therefore not finding a boot sector... Working fine right up until the lightening storm. Bizarre... Oh well. I have a new 500gig hard drive to replace my 80, on the way.

---

