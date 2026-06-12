---
title: "Mounting USB drive"
date: 2006-02-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by John Jason Jordan on 2006-02-13
I have a 60 GB USB pocket drive. In the past, if I simply plugged it into a USB port on my AMD64 laptop with Ubuntu-64 Breezy, it would just automount. However, after a disaster using dump to make a backup to it yesterday, it is no longer recognized. The disaster is involved, but basically dump is stupid. It did not have enough space on the pocket drive, so it stopped and asked me where to put volume 2. Realizing that I should have deleted some files from the pocket drive before starting the backup, I aborted the dump backup. Then I unplugged the pocket drive. Later the computer started acting weird -- menus wouldn't drop down, and other bizarre behavior. I decided to restart. When it restarted I could not log in. Turns out the laptop hard disk was full. It seems that to dump "abort" means sort of like "no" to a cat, i.e., not while I'm watching. So when I unplugged the pocket drive dump just continued the dump to the mount point /media/usbdisk until it completely filled the laptop hard disk. Worse, after I shelled to a command line and manually moved several GB of mp3s to my Windows desktop, I was able to log in, but amazingly dump had relaunched itself after the computer restarted and just continued the dump. Soon I was out of space again and had to move more files off the laptop.

I finally got everything fixed and I'm back to normal, but now the laptop does not automount the pocket drive. 

So here's what I've done:

1) In a terminal became su and then did dmesg | grep -i "SCSI device". This listed it as /dev/sda, so Linux sees it OK.

2) There was nothing on it I wanted, so I formatted it ext3. (It had been formatted ext3 previously.)

3) Created a folder /home/jjj/Desktop/USB_Drive to use as a new mount point.

4) Made a backup of fstab, then did echo "/dev/sda /home/jjj/Desktop/USB_Drive ext3 jjj,noauto,uid=jjj,gid=jjj 0 0" >> /etc/fstab

5) Did mount USB_Drive

At that point the drive light blinked and I heard the drive spin, so something happened. But I got an error message:

mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

And dmesg | tail gives me:

[ 4958.544728] EXT3-fs: Unrecognized mount option "uid=1000" or missing value

So what am I doing wrong?

---

### Post by RAOF on 2006-02-13
Yup.  As the dmesg says, the "uid=" and "gid=" options are not valid on ext3 filesystems (they actually support real file-permissions, so these options aren't necessary anyway).  Try it again without those options.

---

### Post by John Jason Jordan on 2006-02-13
[QUOTE=RAOF]Yup.  As the dmesg says, the "uid=" and "gid=" options are not valid on ext3 filesystems (they actually support real file-permissions, so these options aren't necessary anyway).  Try it again without those options.[/QUOTE]
OK,got it mounted. Unfortunately, for some reason only root can mount it.The line in fstab now says:

/dev/sda /home/jjj/Desktop/USB_Drive ext3 0 0

If I look at Properties for it in Konqueror it is owned by root. I tried sudo chown jjj:jjj /dev/sda, but it didn'thelp. How do I change the ownership/permissions?

---

### Post by RAOF on 2006-02-14
You could "sudo chown jjj:jjj /home/jjj/Desktop/USB_Drive".  That's what you were after in the first place - you want to own the files on the filesystem, not the raw device.  Running "chown /dev/hda" and the like is never going to help anything, as far as I know.

---

### Post by John Jason Jordan on 2006-02-14
[QUOTE=RAOF]You could "sudo chown jjj:jjj /home/jjj/Desktop/USB_Drive".  That's what you were after in the first place - you want to own the files on the filesystem, not the raw device.  Running "chown /dev/hda" and the like is never going to help anything, as far as I know.[/QUOTE]
OK, I did that. And now I own the folder/mount point. But I still have to be root to mount the device. I don't want to have to be root to mount it. 

What I really want is for it to automount like it used to before dump screwed up my computer yesterday morning. I've had a lot of minor problems ever since, because in an effort to log in I had to move a lot of files off the computer. I thought all I moved were data files -- OO.o text files, for example. But ever since getting things back to normal I've had things that can only mean missing config files. E.g., Firefox is using some strange font and I can't change it because it no longer sees any of the fonts I have installed on the system (but OO.o still sees them). 

I've googled for the past four hours and I can't find anything that works to get it to automount. Right now I can't even get it mounted manually. The line in fstab still says 

/dev/sda /home/jjj/Desktop/USB_Drive ext3 0 0

But when I try to mount it I get the same error message as before:

mount: wrong fs type, bad option, bad superblock on /dev/sda,
missing codepage or other error
In some cases useful info is found in syslog - try
dmesg | tail or so

And when I do dmesg | tail I get:

[570.644311] EXT3-fs: unrecognized mount option "0" or missing value

The error message from dmesg is different, but I don't understand why it worked before and now it doesn't. The only change I made was making myself owner of the mount point.

Mostly I don't understand why mounting things is so godawful confusing. 

Thanks for listening to my ranting. It's late, I've spent hours on this, and I'm frustrated.

---

### Post by RAOF on 2006-02-14
[QUOTE=John Jason Jordan]...
/dev/sda /home/jjj/Desktop/USB_Drive ext3 0 0
...[/QUOTE]
Sorry - I didn't notice this bit.  This line is missing the "options" segment - the fstab lines go 
```
<device> <mountpoint> <fstype> **<options>** <somenumber> <someothernumber>
```
If you add "defaults,noauto,user,user_xattr" between the "ext3" and the first 0 it should:
1) Be mountable.
2) Not be mounted at boot time (noauto)
3) Be mountable by not-root (that's what the "user" option is)
4) Have extended metadata support on (user_xattr).  Optional, but some things (beagle particularly) really like this to be on.

Once you've got it mounted, you'll then want to "sudo chown -R jjj:jjj /home/jjj/USB_Drive" to own all the stuff on the drive.

I'm not sure how to fix your automount, though.  You could try removing the configuration files and getting a fresh set by
```
sudo apt-get remove --purge gnome-volume-manager
sudo apt-get install ubuntu-desktop
```
But it sounds like you've got more problems than just the automount :(
You could try the same thing with each program that's not working properly.  That might work.

---

### Post by John Jason Jordan on 2006-02-14
[QUOTE=RAOF]Sorry - I didn't notice this bit.  This line is missing the "options" segment - the fstab lines go 
```
<device> <mountpoint> <fstype> **<options>** <somenumber> <someothernumber>
```
<snip>
I'm not sure how to fix your automount, though.  You could try removing the configuration files and getting a fresh set by
```
sudo apt-get remove --purge gnome-volume-manager
sudo apt-get install ubuntu-desktop
```
But it sounds like you've got more problems than just the automount :(
You could try the same thing with each program that's not working properly.  That might work.[/QUOTE]
I should have posted back -- about an hour ago I finally got it mounted and I think it is auto-mounting also, although I haven't tested that yet. I changed the line in fstab by adding "defaults" in the options section, and that was all it took. 

However, now that I have it mounted, I'm trying to use Kdar to make backups to it. I finally got Kdar pretty well configured, and it is making backups to the pocket drive, but about one out of four times Kdar locks up Linux tight as a drum. No mouse, no keyboard -- dead. Gotta hit the power button to get out. And once (so far) it just logged me out and brought up the Ubuntu login splash screen. This is seriously not cool. 

I also decided to try a Restore, only to discover that it can't restore from the archive unless the archive is on a local filesystem somewhere. That's lame. But finding a simple backup solution for 64-bit Ubuntu is not easy. Not much to choose from. :(

Thanks for the mount help. :)

---

