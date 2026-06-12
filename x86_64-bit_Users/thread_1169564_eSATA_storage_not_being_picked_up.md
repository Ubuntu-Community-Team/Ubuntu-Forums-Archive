---
title: "eSATA storage not being picked up?"
date: 2009-05-25
forum: x86 64-bit Users
---

### Post by javahollic on 2009-05-25
Hi,
I just got a shiny new Verbatim 2TB raid esata box : [http://www.play.com/PC/PCs/4-/9564816/Verbatim-2TB-RAID-Extrernal-USB2-0-eSATA-Hard-Drive-Enclosure/Product.html](http://www.play.com/PC/PCs/4-/9564816/Verbatim-2TB-RAID-Extrernal-USB2-0-eSATA-Hard-Drive-Enclosure/Product.html), is detected fine under windowsXP (which I used _just_ to test it worked when 'buntu failed me!), but not so much as /var/log/messages chatter on esata connection/powerup.

Anyone confirm eSATA support supports hotplug configuration? Is it just me (again!)?

Had the problem on 8.10, have since upgraded to 9.04, same results.

---

### Post by pixel :-) on 2009-05-25
Start a tread here

[http://ubuntuforums.org/forumdisplay.php?f=332](http://ubuntuforums.org/forumdisplay.php?f=332)

you'll get a faster solution.

Post here and there your /var/log/dmesg as an attachment

Normally, these things are treated like usb keys

in
system>administration>users and groups>your self>properties>user privileges

"access external storage devices automatically" is active?
also activate FUSE, maybe it would help.

---

### Post by javahollic on 2009-05-26
heres the dmsg

---

### Post by pixel :-) on 2009-05-26
it is recognized as sde. If i remember correctly, i'm not sure, it doesn't prompts me that a usb key is in, if it went threw bootup. Have tried to hutplug it? And did you checked your rights?

try 

mount | grep sde

it will tell you if its alredy mounted and where

ls /dev | grep sde

normally it will tell you 
sde
sde1

manual mount

mount -t type /dev/sde1 "/a directory you whant it to show in, just create one"

type = vfat, ntfs, ext2, ext3, ext4 
depending on the formating

---

### Post by javahollic on 2009-05-29
Close but no ceegar.  sde is the internal raid array.  **fdisk -l** does not show the new device, so the system doesn't/isn'y recognisig it, but XP did fine....

When I hit the 'on' button it ought to hotplug, but doesn't and I get no /var/messages chatter that would happen with usb keys....

---

### Post by ronparent on 2009-05-30
Since the external drive is a raid box, is a driver necessary for windows to use it? Do the specs say it can be used with linux?

Just a possibility, but if the raid box has the equivalent of a fakeraid controller, maybe the program dmraid could discover it. You would have to install it - enter **sudo apt-get install dmraid -y** in a terminal. Then run sudo **dmraid -r**. If that command gives an output, then run **sudo dmraid -ay**. If that produces output then you will find the symbolic links for the raid array in /dev/mapper (**ls /dev/mapper**). Those links can be mounted with a normal mount command to any place you create in your file system for that purpose. This is a reach, but if the raid box is supported by the dmraid interface I can give you more specifics if you need.

---

### Post by javahollic on 2009-08-05
Hi, thanks for the feedback, got diverted :)  Interesting, will check that later.  I currently use the box with Ubuntu9.04 x86_64 without incident (USB only!)

thanks

---

### Post by javahollic on 2009-08-07
Tried dmraid -r, got:
```

/dev/sdd: pdc, "pdc_bdejdjb", stripe, ok, 976562432 sectors, data@ 0
/dev/sdc: pdc, "pdc_bdejdjb", stripe, ok, 976562432 sectors, data@ 0
/dev/sdb: pdc, "pdc_bdejdjb", stripe, ok, 976562432 sectors, data@ 0
/dev/sda: pdc, "pdc_bdejdjb", stripe, ok, 976562432 sectors, data@ 0

```
These are the internal raid devices.

Tried dmraid -ay, got:
```

RAID set "pdc_bdejdjb" already active
RAID set "pdc_bdejdjb1" already active
RAID set "pdc_bdejdjb2" already active
RAID set "pdc_bdejdjb3" already active
RAID set "pdc_bdejdjb5" already active
RAID set "pdc_bdejdjb6" already active
RAID set "pdc_bdejdjb7" already active
RAID set "pdc_bdejdjb8" already active
RAID set "pdc_bdejdjb9" already active
RAID set "pdc_bdejdjb10" already active
RAID set "pdc_bdejdjb11" already active

```

Most of these are my OS partitions:
```

/dev/mapper/pdc_bdejdjb1 on /boot type ext4 (rw,noatime)
/dev/mapper/pdc_bdejdjb2 on / type ext4 (rw,noatime,errors=remount-ro)
/dev/mapper/pdc_bdejdjb3 on /var type ext4 (rw,noatime)
/dev/mapper/pdc_bdejdjb5 on /tmp type ext4 (rw,noatime)
/dev/mapper/pdc_bdejdjb6 on /usr type ext4 (rw,noatime)
/dev/mapper/pdc_bdejdjb7 on /home type ext4 (rw,noatime)
/dev/mapper/pdc_bdejdjb8 on /usr/local type ext4 (rw,noatime)
<9 is swap>
/dev/mapper/pdc_bdejdjb10 on /srv type ext4 (rw,noatime)

```

Fdisking /dev/mapper/pdc_bdejdjb11 didn't give me the right size to be the device in question...

Anything else I can try?

---

