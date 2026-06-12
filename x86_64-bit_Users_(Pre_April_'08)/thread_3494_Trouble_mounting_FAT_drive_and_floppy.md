---
title: "Trouble mounting FAT drive and floppy"
date: 2004-11-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by A64Biter on 2004-11-06
I am not sure if my problem is specific to the 64 bit install but a search did not reveal any similiar post in the general forum so here goes.

First problem is I can't get my windows FAT32 partition to mount properly. My FSTAB line is;

/dev/hda1   /mnt/win    auto   users,ro,noauto   0     0

I don't get any errors when I mount the drive, but when I try to browse the disk strange things happen. I see icons for the files on the drive, but directories look the same as files. If I right click an icon ( to try to view properties ) the icon disappears.

I tried changing my FSTAB line to;

/dev/hda1   /mnt/win    fat   users,ro,noauto   0     0

but then I can't mount the drive.Says the kernal doesn't support FAT. LSMOD does show that the FAT module is loaded. Also tried 'vfat' and it works the same as 'auto'

My second problem is I can't mount my floppy drive. The FSTAB line is;

/dev/fd0   /media/floppy0    auto   rw,user,noauto   0     0

When I try to mount the drive I get the error,
"special device /dev/fd0 does not exist"

Sure enough, /dev does not have a device block for fd0. Did the installer miss something?

My system is an ASUS K8V SE Deluxe

Thanks for any suggestions ](*,)

---

### Post by wallijonn on 2004-11-06
bump.

changing [COLOR=BLUE]/dev/fd0 /media/floppy0 noauto noauto 0 0[/COLOR] to [COLOR=BLUE]/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0[/COLOR] kills /dev/fd0, right? 

If we change it to [COLOR=BLUE]/dev/fd0 /media/floppy0 auto rw,user,owner,noauto 0 0[/COLOR] does it fix the problem?

---

### Post by Werpon on 2004-11-07
"fat" is not a valid type, try "msdos"; but it looks like your problem has nothing to do with fs types...

If your system can't find /dev/fd0 and you're sure your floppy drive is standard (not some IDE drive or something) you can try

```
cd /dev/ ; ./MAKEDEV fd0
```

---

### Post by A64Biter on 2004-11-07
[QUOTE=Werpon]"fat" is not a valid type, try "msdos"; but it looks like your problem has nothing to do with fs types...

If your system can't find /dev/fd0 and you're sure your floppy drive is standard (not some IDE drive or something) you can try

```
cd /dev/ ; ./MAKEDEV fd0
```[/QUOTE]

Thanks! "msdos" fixed my hda problem.

Still no luck with my floppy. Its a standard floppy, pluged into the motherboard. Works with Window$. 

I didn't get any errors when I did the ./MAKEDEV fd0, but when I try to mount the drive I still get,
"special device /dev/fd0 does not exist".

Also tried wallijonn's suggestion but it made no difference. I am new at this, but it seems like it points to the fact that I don't have a device block for fd0 in /dev.

What should I see in /dev?

---

### Post by wallijonn on 2004-11-07
bump.

why isn't it listed under 
```
# lsmod
```?

So I 
```

cd /dev
sudo sh ./MAKEFILE fd0

```
And it still doesn't work.

Just for the hell of it I
```
[COLOR=RED]modprobe floppy[/COLOR]
```
and then
```
[COLOR=RED]mount /media/floppy0[/COLOR]
```
eureka!!

It mounts, I can access it.

guess I'll have to use an 
```
[COLOR=RED]umount /media/floppy0[/COLOR]
```
seeing as right-click 'unmount floppy' doesn't work.

When I ```
[COLOR=BLUE]lsmod[/COLOR]
``` it lists [COLOR=GREEN]floppy[/COLOR].

<I give myself a pat on the back> :D

Now, I did do one other thing: When I went to /dev/fd there was a "0" there and when I clicked on it once it disappeared. After my modprobe command did it create a new one? or did the disappearance of it cause it to be regenerated? (before I issued the modprobe command).



.

---

### Post by wallijonn on 2004-11-07
okay,

I edited /etc/fstab as [COLOR=RED]/dev/fd0  /media/floppy0  vfat  rw,user,noauto  0 0[/COLOR], I start a root terminal, [COLOR=RED]modprobe floppy[/COLOR]. 

Computer -> Disks -> Floppy 1, and I can read/write to the floppy. (This way I don't have to fuss around with privs). 

I can right-click floppy0 on the desktop -> [COLOR=BLUE]Unmount Volume[/COLOR] and it umounts it.

**How do I make modprobe permanent?** insmod?

/lib/modules/2.6.8.1-3-686/kernel/drivers/block/floppy.ko already exists.
/lib/modules/2.6.8.1-3-386/kernel/drivers/block/floppy.ko already exists.

-----------------------------------------------------------------------------------------------------------------------------------

Before, I started a root terminal,
mount -a
modprobe floppy

If I mount it in the root terminal I have to [COLOR=Green]cp[/COLOR] through the CLI and [COLOR=Green]umount[/COLOR] through the CLI. 

Just going to Computer -> Disks -> double-click floppy0 allowed me full access.

.

---

### Post by wallijonn on 2004-11-08
cd /dev
[COLOR=BLUE]sudo depmod -a 
sudo modprobe floppy[/COLOR]

is still no better than just 
[COLOR=BLUE]cd /dev
modprobe floppy[/COLOR]

trying 
[COLOR=BLUE]cd /etc
update-modules[/COLOR]
next

no. didn't work on a reboot.

-----------------------------------------------

**The fix:**

```

[COLOR=BLUE]cd /etc
sudo gedit modules[/COLOR]

```

add [COLOR=GREEN]floppy[/COLOR] to list.

modules should now look like this:
```
[COLOR=RED]
# /etc/modules: kernel modules to load at boot time.
#
# This file should contain the names of kernel modules that are
# to be loaded at boot time, one per line.  Comments begin with
# a "#", and everything on the line after them are ignored.

psmouse
mousedev
ide-cd
ide-disk
ide-generic
lp
floppy
[/COLOR]
```

<reboot>

Hitting the disk icon should now mount your floppy.


.

---

### Post by A64Biter on 2004-11-09
Thanks for your help!!

---

### Post by Datchew on 2005-01-25
i'm also having trouble. 
I performed the above fix and now my "modules" thing (is it like a dll file) shows the floppy in the list AFTER a reboot. 

however, i still cannot find where to access the floppy drive anywhere. 
in my computer->disks 
all i see is cd-rom1, cd-rom2, filesystem, and network... no floppy shows up. 

Am i just missing information as to how to find it in the file manager (i think it's called Nautilus)????

please advise. 
Thanks,
Datchew.

---

### Post by Datchew on 2005-01-29
nevermind. 

never got any help, but i was able to find a MUCH EASIER solution [HERE!](http://ubuntuforums.org/showthread.php?t=12282&highlight=floppy+drive+mount)

Datchew.

---

### Post by Tyler Szabo on 2006-02-26
The ./makedev fd0 worked like a charm when I lost my /dev/fd0 (bad fstab entry involving setting type to vfat,msdos,auto). My fstab line looks like the following:
```
/dev/fd0        /media/floppy0  vfat    rw,user,noauto  0       0
```

Note: The vfat entry is intended to allow me to read long filenames from my old windows disks; it works!

---

