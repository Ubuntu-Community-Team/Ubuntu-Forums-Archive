---
title: "Help, system won't boot after 2.6.17-11 upgrade"
date: 2007-02-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by emakris on 2007-02-13
Hi,

I upgraded today to 2.6.17-11 and after a reboot, I get:
run-init: /sbin/init: Permission denied

I'm running edgy on a 64-bit AMD system with an nvidia chipset.

Is anyone seeing the same issue? Does anyone have a workaround?

Thanks
Ernie

---

### Post by pay on 2007-02-13
[Here's ](http://www.ubuntuforums.org/showthread.php?t=359132&highlight=can%27t+boot+after+upgrade) a similar thread.

---

### Post by emakris on 2007-02-13
Thanks for the info. Looking at the thread though, it implies that one can boot into the older kernel on the grub selection list. I'm unable to even boot into the earlier kernel. 

I can boot from the live cd, but don't know what to do next. I can't seem to mount the existing sata disk either, maybe because the driver is not loading....

---

### Post by pay on 2007-02-13
To mount the disk try ```
sudo mkdir /mnt/ubuntu 
sudo mount /dev/sda1 /mnt/ubuntu
```

---

### Post by emakris on 2007-02-13
I can boot via the live cd and I can mount the disk now. I read in the following post:
[http://ubuntuforums.org/showthread.php?t=223773&highlight=%2Fsbin%2Finit+permission+denied](http://ubuntuforums.org/showthread.php?t=223773&highlight=%2Fsbin%2Finit+permission+denied)

Where I can do something like this:

sudo mount -t ext3 -o rw /dev/hda1 /mnt
sudo chroot /mnt
sudo apt-get update; apt-get upgrade; apt-get install udev

Minus the udev install, is this ok to do? I attempted it and it wanted to update the 2.6.17-10 kernel for some reason.

I'm thoroughly confused now :)

I guess its time to backup since I can mount it ok.

---

### Post by pay on 2007-02-13
The only think I can think of is try changing the permissions to that file. ```
sudo chmod  755 /sbin/init 
```755 imight not the right one to use though.

---

### Post by pay on 2007-02-13
> **emakris said:**
> I can boot via the live cd and I can mount the disk now. I read in the following post:
[http://ubuntuforums.org/showthread.php?t=223773&highlight=%2Fsbin%2Finit+permission+denied](http://ubuntuforums.org/showthread.php?t=223773&highlight=%2Fsbin%2Finit+permission+denied)

Where I can do something like this:

sudo mount -t ext3 -o rw /dev/hda1 /mnt
sudo chroot /mnt
sudo apt-get update; apt-get upgrade; apt-get install udev

Minus the udev install, is this ok to do? I attempted it and it wanted to update the 2.6.17-10 kernel for some reason.

I'm thoroughly confused now :)

I guess its time to backup since I can mount it ok.It's ok to do that. You are mounting and then chrooting into your old environment, so then you can use it from the shell.

---

### Post by emakris on 2007-02-13
> **pay said:**
> The only think I can think of is try changing the permissions to that file. ```
sudo chmod  755 /sbin/init 
```755 imight not the right one to use though.

Hi,

Thanks so much for your help btw.

The perms on /sbin/init are 755 to begin with. I'm going to try the upgrade path after everything is backed up.

---

### Post by emakris on 2007-02-13
I backed up, but now running:

sudo chroot

from the first virtual console gives:

chroot: cannot run command '/bin/bash': Permission denied.

This blows :confused: 

I'm just trying to get to the point where I can back out the 11 kernel or reinstall the 10 kernel.

---

### Post by pay on 2007-02-13
The [Gentoo handbook](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml) is good for learning how to chroot into your installation```
# swapon /dev/hda2
# mount /dev/hda3 /mnt/gentoo
# mkdir /mnt/gentoo/boot
# mount /dev/hda1 /mnt/gentoo/boot
# mount -t proc none /mnt/gentoo/proc
# mount -o bind /dev /mnt/gentoo/dev
# chroot /mnt/gentoo /bin/bash
# env-update
>> Regenerating /etc/ld.so.cache...
# source /etc/profile
# export PS1="(chroot) $PS1"
```Obviously change the partitions to your partitions.

---

### Post by emakris on 2007-02-13
Is it a mistake to perform those commands via the edgy live CD? Should I use a gentoo cd?

---

### Post by pay on 2007-02-13
You could use any liveCD. It doesn't matter. With a Ubuntu one though, you will have to put sudo infront of some of those commands.

---

### Post by emakris on 2007-02-13
hmmm. I actually did.

I did sudo mount, and managed to mount /dev/sda1 great. I actually used this to back everything up last night.
But when I tried sudo chroot /mnt it failed with the previous error. 

Do I really have to mount the proc and swap for the /mnt partition?

Thanks
Ernie

---

### Post by pay on 2007-02-13
> **emakris said:**
> hmmm. I actually did.

I did sudo mount, and managed to mount /dev/sda1 great. I actually used this to back everything up last night.
But when I tried sudo chroot /mnt it failed with the previous error. 

Do I really have to mount the proc and swap for the /mnt partition?

Thanks
ErnieYou probably dont need to mount those, but I do anyway. This is pretty much all the help that I can give. Sorry. Hopefully someone else with more knowledge helps you out.

---

### Post by emakris on 2007-02-13
Thank you! You've been a great help!
I'll try these commands later and post the results.

---

### Post by emakris on 2007-02-13
I still get the same thing trying to chroot.

'/bin/bash' permission denied :(

---

### Post by muzzamo on 2007-10-05
I'm getting this error after upgrading the kernel on gutsy 32-bit beta.

This is all looking too hard so it looks like i'm just going to do a re installation :-(

---

### Post by Kilz on 2007-10-05
> **muzzamo said:**
> I'm getting this error after upgrading the kernel on gutsy 32-bit beta.

This is all looking too hard so it looks like i'm just going to do a re installation :-(

Did you as a good beta tester , report this problem/bug on launchpad?

---

