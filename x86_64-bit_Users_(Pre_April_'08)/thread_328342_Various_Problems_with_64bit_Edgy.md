---
title: "Various Problems with 64bit Edgy"
date: 2006-12-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by Raptor45 on 2006-12-30
I have had the 32bit version of Edgy installed since release, but never really used it often due to reliability problems (most likely due to buggy rt61 wireless drivers) and the fact that Windows tends to be better at "just working" on a day to day basis. Since I like fooling with computers, and Linux was just sitting there unused, I figured I'd try reinstalling with 64bit to fiddle with things some. I had expected to run into some issues (flash, etc), but kind of assumed the OS would work as expected. Unfortunately, so far I've had problems right from the start. So far this includes the following:

The splash screen is black and white, as reported [here]("http://www.ubuntuforums.org/showthread.php?t=304673"). I assume this is unfixable as yet, and is just going to have to be annoying.

My NTFS Hard Drives are not showing by default. I was going to check the disk manager as stated in the help, only to find its [missing]("http://www.ubuntuforums.org/showthread.php?t=280933"). I'm kinda curious why the 64bit version didn't autodetect those drives like 32 did. Anyway, how can I get it to see these drives?

Overall I'm pretty frustrated with the 64bit version of ubuntu; it seems even the basics aren't working right. I hoped for better. Keep in mind that I don't have a problem needing to spend some time fixing this stuff for fun. I just don't want to spend a bunch of time working at this before realizing 64bit will never be as useful as just using 32 from the start. I'm kinda worried about what other problems I'll find as I go. If 64bit is truly as gimped as it appears right now, please let me know and I guess I'll just go back to the way it was before.

---

### Post by pross on 2006-12-30
the splash IS fixable...just follow these simple instructions...

```

sudo apt-get install build-essential
sudo apt-get nstall usplash-dev
wget http://archive.ubuntu.com/ubuntu/pool/main/u/usplash-theme-ubuntu/usplash-theme-ubuntu_0.6.tar.gz
tar xzfv usplash-theme-ubuntu_0.6.tar.gz
cd usplash-theme-ubuntu-0.6
mv usplash-theme-ubuntu.c usplash-theme-ubuntu.c.orig
wget http://librarian.launchpad.net/5247731/usplash-theme-ubuntu.c
make
sudo make install
sudo update-initramfs -u

change defoptions line in /boot/grub/menu.lst to:
# defoptions=quiet splash vga=791

sudo update-grub

```

As for the NTFS problem..i see no entry for hda1 in my /etc/fstab so it wont ever be visable will it...

---

### Post by Raptor45 on 2006-12-30
I just got wifi going, and no crashes yet, so that has me hopeful. I'll try that fix for the splash screen as soon as everything gets updated.

Anyone have a way to get Linux to detect those NTFS drives? I'm sure its possible, I just don't have a clue how to go about doing it.

---

### Post by beamo on 2006-12-30
Here is the how to I used to set up my windows partition:

[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

I set it up so that I could read/write and haven't had any problem whatsoever...yet. I have to say I'm surprised at how good Ubuntu is now overall. I ran 5.04 a couple of years ago and had many, many crashes but since using 6.06 and now 6.10 I have had none and almost no other problems to speak of. The only thing I still use Windows for is Civilization4 and Oblivion as well as whatever absolutely cannot run in Linux. However, after installing Windows on my vmware server I no longer need to dual boot for anything except those games and I don't play them much anymore. Now if I could only figure out how to mount my other partitions from within the vmware server...

---

### Post by Raptor45 on 2006-12-30
Splash screen is fixed. Got the NTFS drives working. Instead of using the ntfs-3g I just found online how to edit fstab to mount the drives. My only question is, how do I get Ubuntu to see it as a true drive (with the applicable icons & links, etc), rather than just appearing in /mnt/?

And also, does anyone else have an issue where edgy will lock up on startup approximately 1/3 of the way through? I have had this issue on both 32 and 64 bit, but it only happens like 10% of the time.

---

### Post by Lil_Eagle on 2007-01-23
> Instead of using the ntfs-3g I just found online how to edit fstab to mount the drives. My only question is, how do I get Ubuntu to see it as a true drive (with the applicable icons & links, etc), rather than just appearing in /mnt/

First, create the directory that you want it to mount in.  If you want it inside your home directory for example:

sudo mkdir /home/windows

Then modify fstab to mount it there instead of in /mnt/ by just changing the mountpoint to whatever directory you created.  

While /mnt/ is the standard unix mount point, you can mount filesystems to wherever you want.

---

