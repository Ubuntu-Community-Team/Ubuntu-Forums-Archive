---
title: "Dapper dual boot with XP, GRUB fails with 0x7 for XP load"
date: 2006-10-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by kingsqueak on 2006-10-09
System is an AMD 64 X2, single SATA disk, Dapper amd64 installed.

The Windows install is XP Media Edition, factory install from HP.

I've done a good half-dozen Ubuntu over XP installs using the automatic partitioning the installer has to shrink the XP install and install Dapper.

However, I did the same thing I always do with the amd64 install, it seemed to partition it properly and GRUB won't load XP now after the install.

I don't have the box in front of me for the cut/paste of menu.lst but basically this is it for the XP partitions.  Oddly there are two entries for XP, I'm thinking one is one of those backup images?

# The small image of the two
root (hd0,0)
savedefault
makeactive
chainloader +1

# The main image where I believe the install is by size
root (hd0,1)
savedefault
makeactive
chainloader +1

This matches up basically with any of the other three dual-boot systems I still run with Dapper on them, all with XP Pro on them.

When I select either of the XP partitions, I get the "unknown 0x7" error from grub.  If I use rootnoverify, the small partition freezes and says three finger salute, the larger image looks like it tries to boot but I just get a black screen that sits there.

Ubuntu boot lives on (hd0,2)

Is there any known issue with this?  Or a workaround?

---

### Post by kuja on 2006-10-09
I don't know anything about any issues with it, but perhaps it's not good that both of those are saved as default?

---

### Post by kingsqueak on 2006-10-09
For further info, this is *exactly* what I have in menu.lst

sda1 is definitely the installed system.  I get a disk-read-error and sent to ctrl-alt-del by grub, however the second partition below is the recovery image and that will run through diagnostics but bitch it can't do the recovery...because of my new partition scheme.

I added the hide/unide options from some digging I did, but it doesn't seem to help, it was failing without those lines as well.

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows XP Media Center Edition
hide (hd0,1)
unhide (hd0,0)
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Windows NT/2000/XP
hide (hd0,0)
unhide (hd0,1)
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader     +1

---

### Post by kingsqueak on 2006-10-09
To make it more frustrating, I can mount /dev/sda1 just fine and see the files there.

root@daemon:~# mount /dev/sda1 /mnt
root@daemon:~# cd /mnt
root@daemon:/mnt# ls
AUTOEXEC.BAT  CONFIG.SYS              MSDOS.SYS      system.sav
BOOT.BAK      Documents and Settings  NTDETECT.COM   System Volume Information
boot.ini      hiberfil.sys            ntldr          temp
cmdcons       hp                      pagefile.sys   WINDOWS
cmldr         hpWebHelper.log         Program Files
CMPNENTS      IO.SYS                  Python22

---

### Post by kingsqueak on 2006-10-10
If I do 

chainloader /ntldr 
or 
chainloader /$Boot

I get 'can't mount selected partition'

What's confusing is that I can mount the fs via linux with multiple utils and read the files on it.

It's looking like parted does something to corrupt the partitions when used to resize ntfs, from digging the only solution seems to re-install XP entirely.  The main solution is to not use the linux re-sizing utils on an XP install.

I've done many installs using the resizing in Ubuntu, both Breezy and Dapper and not had any trouble up until now.  Is something different with XP Media Center compared to XP Pro?  Doesn't make sense that it should be.

Wondering to myself.

---

