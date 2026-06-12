---
title: "IPOD shuffle not mounting"
date: 2006-05-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by ravpaul on 2006-05-27
Hi guys, I am new to linux and only installed Ubuntu about two weeks ago. The first thing I did was join the forums and found the support and answers to many of my questions, however I am stumped on a particular issue, which is that my IPOD is detected but I cannot mount it. I followed some instructions that my mate emailed me but have reached a crossroad.

I currently have an IPOD shuffle 1GB and was told in order for me to be able to fully utilise it with a majority of packages including gtkpod I would have to mount it onto my HDD.

The problem begins as I was told to mount it as:

/dev/sda2 /mnt/ipod vfat user,noauto,umask=000 0 0

but that particular partition is my /boot. The next partition type that I have is sda5 but when I try to mount that I "special device /dev/sda5 does not exist"; but I am worried about changing sda2 as it is my boot partition. What do I do? Please help.

---

### Post by John Jason Jordan on 2006-05-27
[QUOTE=ravpaul]I currently have an IPOD shuffle 1GB and was told in order for me to be able to fully utilise it with a majority of packages including gtkpod I would have to mount it onto my HDD.[/QUOTE]
It's hard to help without knowing more about what drives you currently have. Best would be for you to plug in your iPod, then open a terminal window and type "mount." Copy and paste the results here. The "mount" command without any additional arguments just shows what Linux sees. If you run it after plugging in the iPod it should show what Linux is calling it.
If the results from "mount" are not clear, try "dmesg | tail" instead. I'm not sure, but I think you have to run dmesg as root, so make that "sudo dmesg | tail."

One word of caution: If you get your iPod mounted, be SURE to run the "umount" command before unplugging it. Failure to do so can cause the iPod database to become corrupted. This would be a Very Bad Thing. The only way out of that scenario is to reformat and reinstall the database.

---

### Post by ravpaul on 2006-05-28
/dev/sda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-23-amd64-generic/volatile type tmpfs (rw)
/dev/sda2 on /boot type ext3 (rw)
/dev/sda4 on /home type ext3 (rw)
/dev/sdf1 on /media/ipod type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8)

Hope this helps make things clearer.

---

### Post by ravpaul on 2006-05-28
Perfect reply mate.

Just changed the text "/dev/sda2 /mnt/ipod vfat user,noauto,umask=000 0 0"
to "/dev/sdf1 /mnt/ipod vfat user,noauto,umask=000 0 0" and mounted the drive. 

Sorted. Cheers!!!

---

### Post by ravpaul on 2006-05-28
Damn theres a fault with my theory as the ipod is being mounted as a different devive each time. I.e. is being mounted as /dev/sdg1 this time and sdb1 the time before that.

Is there any way of setting a static mount?

---

### Post by John Jason Jordan on 2006-05-28
[QUOTE=ravpaul]Damn theres a fault with my theory as the ipod is being mounted as a different devive each time. I.e. is being mounted as /dev/sdg1 this time and sdb1 the time before that.

Is there any way of setting a static mount?[/QUOTE]
Sorry, I'm too new to Linux and don't know the answer to that. I generally just plug in a USB thing, then do "dmesg | tail" if I need to see what it is this time.

I have read some things about the mount point, "/mnt/ipod" in your case, and most people think that /dev is not where things should be mounted on a modern Linux system. I can't remember why. A better location is /media. I use /media/iPod for my mount point. You might try that to see if it helps.

Another thing to try would be to mount it with a GUI file browser. I don't know if Nautilus can mount things, as I banned it from my computer after it ate most of my mp3 collection one day. For a file browser I use Konqueror instead, but it doesn't have a mount utility. Therefore, I also installed Krusader, which I launch as root. It has a GUI mount utility so I can just click on the Mount icon and then see what it finds. Wherever the USB device is, I can right-click on it and select Mount from the popup. Ditto for Unmount. I not only have an iPod, I also have a USB flash drive that I need at the university and a 60 GB USB pocket drive that I use for backups. I have the same experience as you -- they are always different.

In my case I mount my iPod only once every couple of months when I have enough new mp3s that I decide it's time to add them. I just save up all my iPod housekeeping so I don't have to mess with it often. However, mine is 60 GB and all I have is classical, so I'm in a somewhat different world than the average iPod user.

PS: If you use gtkpod to change tags (which I do a lot) it's a good idea to use gtkpod to copy all your mp3s off the iPod to your hard disk and then make backups from there. The reason is that gtkpod will change the tags, but it does so only on the mp3 file on the iPod; the original mp3s on your hard disk are not changed. So if you mess up your iPod you'll have to restore the mp3s from a backup, and you want those files to be the same as what you had on the iPod. And eventually you *will* mess up the iPod. The Apple database system is not very robust, plus mounting and unmounting on Linux is problematic, as you're discovering. All it takes is to forget to unmount it and pull it out sometime when it was still writing to the disk. (Been there, got the t-shirt.):(

---

### Post by %hMa@?b&lt;C on 2006-05-28
your shuffle should always mount as /media/ipod
at least my 5G and my brother's shuffle do that.  
also if you have trouble unmounting your shuffle, you should run this command so that your ipod is fully unmounted before unplugging 
```
sudo chmod +s `which eject`
```

---

### Post by John Jason Jordan on 2006-05-28
[QUOTE=jeffc313]your shuffle should always mount as /media/ipod
at least my 5G and my brother's shuffle do that.  
also if you have trouble unmounting your shuffle, you should run this command so that your ipod is fully unmounted before unplugging 
```
sudo chmod +s `which eject`
```[/QUOTE]
What does that command do? How is it different from what I use?
```
sudo umount /media/ipod
```
Then again, normally I use the Mount utility in Krusader.

---

### Post by ddonky on 2006-06-05
this works for me:

'sudo eject ipod'

---

