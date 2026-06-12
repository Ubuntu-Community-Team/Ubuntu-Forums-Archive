---
title: "FakeRAID debootstrap 64bit Feisty Problem"
date: 2007-09-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by rwillia2001 on 2007-09-27
Hi,

I have had success installing 32bit raid1 on my fake raid system (ASUS P5B-E, intel E6600, ICH8R. However, when I try and and install the 64 bit system starting from a LIVE CD I do:

sudo debootstrap --arch amd64 feisty /target

then it errors after the download, validation and extraction with

W: Failure trying to run: chroot /target mount -t proc proc /proc

and if I try

sudo chroot /target

chroot cannot run command /bin/bash: Exec format error

I think this is something to do with building a cross-platform system, starting the install from a i386 LIVE CD and then trying to chroot into the amd64 bit feisty system. However, it looks like people have solved this problem. I would be very grateful if anyone could give a short explanation as to how to start an install  in 32 bit and end in 64 bit (debootstrap install).

Many thanks

RMW

---

### Post by halleyfdee on 2007-09-29
I got the similar problem. I have tried the following code, and passed, and encountered a new situation

```
sudo debootstrap --foreign dapper /target
```

retrieving,validating,....

```
cd /target/debootstrap
./debootstrap dapper /target
```

validate.unpack,extract,config,

The process stoped at the point "Base system installed successfully", did not return to the prompt.
BUT, when unpacking libc6-i686,it failed 5 times. 
"W: Failure while installing base packages. This will be re-attempted up to five time."

So I tried this in another terminal:
```
sudo chroot /target
apt-cdrom -m add fail. 
```
"apt-cdrom: error while loading shared libraries: libstdc++.so.6: cannot open shared object file: No such file or directory"

Maybe this helps
[http://ubuntuforums.org/showthread.php?t=218485&highlight=raid+debootstrap]("http://ubuntuforums.org/showthread.php?t=218485&highlight=raid+debootstrap")

---

### Post by rwillia2001 on 2007-10-10
Hi,

Thanks for the tip. The new gutsy 64 bit live CD might get me over this particular hump - however my initial tests suggested that fake raid was not at all supported with this release (for my system). I await the official release version. Also I am suspecting that packages marked as i686 are not 64bit.

BYE!
RMW

---

### Post by magikx21 on 2007-10-11
I wonder if this issue is the reason that half the time I adjust my settings trying to get Twinview to work I reboot X getting a blank screen. I've learned that keeping a backup of xorg.conf saves me alot of time.

---

