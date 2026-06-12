---
title: "How to access Drives"
date: 2008-09-19
forum: x86 64-bit Users
---

### Post by tesla.coil on 2008-09-19
hi i have dual booting windows and now installed ubuntu( with File system as EXT3). the problem is am not able to access my other drives that have applications and movies from ubuntu it says "cannot mount volume". wht do i need to do to mount those drives that have NTFS partition on them.

---

### Post by cariboo on 2008-09-19
Could you post the output of fdisk -l in your next post. To do this opem a Applications-->Accessories-->Terminal and type:

```
sudo fdisk -l
```

Highlight the output and paste it into your post using the code tags. The code tags can be used by clicking the # sign in the advanced editor.

Jim

---

### Post by tesla.coil on 2008-09-20
> **cariboo907 said:**
> Could you post the output of fdisk -l in your next post. To do this opem a Applications-->Accessories-->Terminal and type:

```
sudo fdisk -l
```

Highlight the output and paste it into your post using the code tags. The code tags can be used by clicking the # sign in the advanced editor.

Jim

[IMG]http://i36.tinypic.com/23rv911.jpg[/IMG]
here is the pic i have a 80 GB HDD with 20 GB alloted to ubuntu.

---

### Post by philinux on 2008-09-20
The ntfs-3g driver is installed by default in ubuntu Hardy. You might need ntfs-config though. I've no windows on my machine so it's not something I need.

You'll find more info here. [http://www.ntfs-3g.org/](http://www.ntfs-3g.org/)

---

### Post by satshen on 2008-09-20
> **tesla.coil said:**
> hi i have dual booting windows and now installed ubuntu( with File system as EXT3). the problem is am not able to access my other drives that have applications and movies from ubuntu it says "cannot mount volume". wht do i need to do to mount those drives that have NTFS partition on them.

I had a similar problem .. got around this as follows:

Applications -> Accessories -> Terminal

sudo blkid 

I got the following output 

/dev/sda1: UUID="632A50F727C08CF9" LABEL="WindowsVista" TYPE="ntfs" 
/dev/sda5: UUID="3ADC6D9FDC6D5663" LABEL="NEW VOLUME-D" TYPE="ntfs" 
/dev/sda6: UUID="44b3b60e-81ec-426b-a4dc-5db43f29a76e" TYPE="ext3" 
/dev/sda7: TYPE="swap" UUID="d94bcb16-23c4-4431-8002-4ae4722a13a1"

again in terminal 

sudo cd /media

Next step is to create 2 sub-directories in the media directory to mount the Windows ntfs volumes

sudo mkdir WinVolume1
sudo mkdir WinVolume2

Then edit the fstab file 

sudo gedit /etc/fstab 

Made the following entries in fstab

# WINDOWS

#sda1

UUID=632A50F727C08CF9	       /media/WinVolume1	ntfs-3g	defaults,sync,locale=en_US.UTF-8 	0	  0

#sda5

UUID=3ADC6D9FDC6D5663	       /media/WinVolume2	ntfs-3g	defaults,sync,locale=en_US.UTF-8	 0	  0

so that my fstab looked like 


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=44b3b60e-81ec-426b-a4dc-5db43f29a76e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=d94bcb16-23c4-4431-8002-4ae4722a13a1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

# WINDOWS

#sda1

UUID=632A50F727C08CF9	       /media/WinVolume1	 ntfs-3g	defaults,sync,locale=en_US.UTF-8	0	0

#sda5

UUID=3ADC6D9FDC6D5663   	/media/WinVolume2	 ntfs-3g	defaults,sync,locale=en_US.UTF-8	0	0

Saved fstab & rebooted... the Windows ntfs drives auto mounted on boot & could read/write to the volumes.

---

### Post by tesla.coil on 2008-09-20
> **satshen said:**
> I had a similar problem .. got around this as follows:

Applications -> Accessories -> Terminal

sudo blkid 

I got the following output 

/dev/sda1: UUID="632A50F727C08CF9" LABEL="WindowsVista" TYPE="ntfs" 
/dev/sda5: UUID="3ADC6D9FDC6D5663" LABEL="NEW VOLUME-D" TYPE="ntfs" 
/dev/sda6: UUID="44b3b60e-81ec-426b-a4dc-5db43f29a76e" TYPE="ext3" 
/dev/sda7: TYPE="swap" UUID="d94bcb16-23c4-4431-8002-4ae4722a13a1"

again in terminal 

sudo cd /media

Next step is to create 2 sub-directories in the media directory to mount the Windows ntfs volumes

sudo mkdir WinVolume1
sudo mkdir WinVolume2

Then edit the fstab file 

sudo gedit /etc/fstab 

Made the following entries in fstab

# WINDOWS

#sda1

UUID=632A50F727C08CF9	       /media/WinVolume1	ntfs-3g	defaults,sync,locale=en_US.UTF-8 	0	  0

#sda5

UUID=3ADC6D9FDC6D5663	       /media/WinVolume2	ntfs-3g	defaults,sync,locale=en_US.UTF-8	 0	  0

so that my fstab looked like 


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=44b3b60e-81ec-426b-a4dc-5db43f29a76e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=d94bcb16-23c4-4431-8002-4ae4722a13a1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

# WINDOWS

#sda1

UUID=632A50F727C08CF9	       /media/WinVolume1	 ntfs-3g	defaults,sync,locale=en_US.UTF-8	0	0

#sda5

UUID=3ADC6D9FDC6D5663   	/media/WinVolume2	 ntfs-3g	defaults,sync,locale=en_US.UTF-8	0	0

Saved fstab & rebooted... the Windows ntfs drives auto mounted on boot & could read/write to the volumes.

lol that sounds little complex ill try it out! if any thing goes wrong are my ntsf drives screwd?

---

### Post by satshen on 2008-09-20
Hi

A quick way to access ntfs drives is 

Applications -> Accessories -> Terminal

sudo mount -a

 however you will need to run this every time you boot into Ubuntu

Accessing ntfs from linux is always risky - create a backup to be on the safe side.

---

