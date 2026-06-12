---
title: "32 going on 64!"
date: 2006-09-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by hk_2999 on 2006-09-17
Help! I received an ubuntuLinux Dapper x86 CD, and now that I installed it, I was reconsidering to get the 64-bit version. I am using an AMD Athlon64 AM2 procesor, and am wondering how can I upgrade to 64-bits. I can't seem to work it out on Synaptic.

---

### Post by kuja on 2006-09-17
You'll have to get yourself a 64-bit install cd and do a full reinstall. There is no way to just "upgrade" to the 64-bit version.

---

### Post by hk_2999 on 2006-09-17
Really? No way. But I have seen a few linux-amdk8-64 packages on the ubuntu packages site.

Anyway, if that is so, I guess I'll just shipit edgy with 64 next month. aw...

anyway, if it can be done now, i am willing to take any risks to download and replace my base linux system to 64.

---

### Post by kuja on 2006-09-17
I have my own ideas on how it may be possible to do so; however, they're complicated and I've not tested them myself, so I can't recommend anything. Perhaps I'll get a small, new hard drive for the sake of testing things later so I won't have to risk my own data in the process.

---

### Post by hk_2999 on 2006-09-17
Thanks! 

By the way, why wont you guys use the 64-bit version as your default OS. After all, you can still run 32-bit programs in AMD's 64-x architecture, and if there are any incompatibilities, we can just recompile them.

---

### Post by kuja on 2006-09-17
If you don't mind doing a little experimenting, I've cooked up what I think will do the trick. It's quite similar to how I set up my system (I had special reasons for doing it though). You can do it from the cd you installed with.

Requirements for doing this: a little patience, and a reasonably fast internet connection... I managed okay on my satellite connection @ about 80kbs. Also, copying and pasting this whole bit won't work. Some parts need a little friendly interaction.

```

sudo apt-get install dchroot debootstrap ## and maybe others

sudo mkdir /target

# <brackets> denote that you have to enter it yourself!!
# here you'll need to mount the partition you wish to install on...
sudo mount -t <fstype> /dev/<location> /target

sudo mkdir /target/dev
sudo mount --bind /dev /target/dev
sudo mkdir /target/proc
sudo mount -t proc proc /target/proc
sudo mkdir /target/sys
sudo mount -t sysfs sysfs /target/sys

sudo debootstrap --arch amd64 dapper /target

sudo cp /etc/apt/sources.list /target/etc/apt
sudo cp /etc/resolv.conf /target/etc
sudo cp /etc/hosts /target/etc

# run in the now installed system
sudo chroot /target

#if at some point in here you get prompted something about a symlink, just say yes
apt-get update
apt-get install grub
apt-get install linux-amd64-generic
apt-get install ubuntu-minimal

#Before we continue, lets set up a few things
# <brackets> denote that you have to enter it yourself!!
hostname <whatever-you-want-your-computer-to-be-called>
addgroup --gid 1000 <user>
adduser --uid 1000 <user>
adduser <user> adm
adduser <user> dialout
adduser <user> cdrom
adduser <user> floppy
adduser <user> audio
adduser <user> dip
adduser <user> video
adduser <user> plugdev
adduser <user> lpadmin
adduser <user> scanner
adduser <user> admin

apt-get install ubuntu-desktop #(or kubuntu-desktop, or xubuntu-desktop, take your pick!

```

It's not a mere upgrade, it's actually a full install, but this **should** get you the 64-bit install you desire. I think. I make no promises.

Alternatively, you could probably do it from within your current install instead of from the livecd, but that would require more work. Something along the lines of doing the debootstrap and initial setup in the chroot, then rebooting with the livecd, deleting everything from the root filesystem, and moving the stuff out of the chroot (/target) into root (/)

---

### Post by kuja on 2006-09-17
> **hk_2999 said:**
> Thanks! 

By the way, why wont you guys use the 64-bit version as your default OS. After all, you can still run 32-bit programs in AMD's 64-x architecture, and if there are any incompatibilities, we can just recompile them.

Who is "you guys" and who says it's not my default :p

---

### Post by hk_2999 on 2006-09-17
Sweet! gotta try this tomorrow! btw. its no problem for me, i got a 384kbps satellite connection!

btw. sorry about that last post. sometimes i type without thinking and all. Hehe. Oh well, got to add that to my moral code or something - "Thy shalt not post without thinking first!" :KS

---

### Post by Kilz on 2006-09-17
> **hk_2999 said:**
> Anyway, if that is so, I guess I'll just shipit edgy with 64 next month. aw...


Right after a new release it can take up to 2- 2 1/2 months to get the shipit disks. So the wait is going to be about 3 to 3 1/3 months.

---

### Post by hk_2999 on 2006-09-18
Uh oh...

```
hk@hk-desktop:~$ sudo apt-get install linux-amd64-generic
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-amd64-generic
hk@hk-desktop:~$

```

So, what repository do I need to add in order to get the linux-amd64-generic file?

---

### Post by Kilz on 2006-09-18
> **hk_2999 said:**
> Uh oh...

```
hk@hk-desktop:~$ sudo apt-get install linux-amd64-generic
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-amd64-generic
hk@hk-desktop:~$

```

So, what repository do I need to add in order to get the linux-amd64-generic file?

If you are running the 64bit version the generic kernel is installed by default. But other kernels can be installed. The eaisest way to get the list is to do a search for linux-image in synaptic.
If on the other hand you want to install the 64bit version you are going to need a install cd.

---

### Post by kuja on 2006-09-18
Actually Kilz, it looks more to me like he missed a step. 

As I said, you're running all of this from the **livecd** right?
Everything would also have to be done preferably one line at a time, and in exact order. 

hk@hkdesktop instead of root@ubuntu tells me that something doesn't look quite right.

---

