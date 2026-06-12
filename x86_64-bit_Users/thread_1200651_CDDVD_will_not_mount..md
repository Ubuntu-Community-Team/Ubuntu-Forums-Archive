---
title: "CD/DVD will not mount."
date: 2009-06-30
forum: x86 64-bit Users
---

### Post by jdh on 2009-06-30
I replaced my DVD-RW drive with a Pioneer DVR-116D. Hardy assigned /dev/scd0, but complained about the sr driver needing an update. 
I commented out the entry for my old drive, was /dev/hda, and I added the following to /etc/fstab:
 
/dev/scd0 /media/cdrom0   udf,iso9660 user,noauto,exec,uf8 0 0.

I cannot mount any media, auto or manually. I get an 'invalid mount option' error. What am I missing?

---

### Post by tenmoi on 2009-06-30
As far as I know this Pioneer DVR-116D uses the old PATA interface not the new SATA one so you must assign it the hdb or hdc prefix according to which channel the CD-rom drive is on. So a sample line would look like this:
/dev/hdb /media/cdrom0 udf,iso9660 user,noauto,exec,uf8 0 0, where your cdrom drive is on the second master channel.

Take a quick look at this: [http://en.wikipedia.org/wiki/Block_devices](http://en.wikipedia.org/wiki/Block_devices), to refresh your memory of linux naming convention.

Rgds.

---

### Post by jdh on 2009-06-30
I changed from /dev/scd0 to /dev/hda. this is the only IDE connected device in the system. I get this error (attached). 

Here is dmesg:
22.517961] usb 1-2: new low speed USB device using ohci_hcd and address 3
[   22.526056] ata3.00: ATAPI: PIONEER DVD-RW  DVR-116D, 1.08, max UDMA/66
[   22.697953] ata3.00: configured for UDMA/66
[   22.803016] usb 1-2: configuration #1 chosen from 1 choice
[   22.896247] scsi 2:0:0:0: CD-ROM            PIONEER  DVD-RW  DVR-116D 1.08 PQ: 0 ANSI: 5
[   22.896311] scsi 2:0:0:0: Attached scsi generic sg1 type 5
[   22.904172] Driver 'sr' needs updating - please use bus_type methods
[   23.059420] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[   23.059425] Uniform CD-ROM driver Revision: 3.20
[   23.059470] sr 2:0:0:0: Attached scsi CD-ROM sr0

It is assigned to SCD0 and not hda like the old one.

---

### Post by tenmoi on 2009-07-02
Please confirm that this DVD-rom uses the PATA interface as can be seen here:
[http://www.cdrinfo.com/Sections/Reviews/Specific.aspx?ArticleId=23814](http://www.cdrinfo.com/Sections/Reviews/Specific.aspx?ArticleId=23814)

It's strange that this drive should be recognized as an SATA one. But after carefully reading your first post again there is this line that I overlooked: "I get an 'invalid mount option' error".
please make sure that cdrom0 does exist by :
 cd /media
 dir

and see if cdrom or cdrom0 is there.
and try this:
/dev/cdrom  	/media/cdrom  	auto  	ro,auto,user,exec  	0 0

Rgds.

---

### Post by jdh on 2009-07-02
> **tenmoi said:**
> Please confirm that this DVD-rom uses the PATA interface as can be seen here:
[http://www.cdrinfo.com/Sections/Reviews/Specific.aspx?ArticleId=23814](http://www.cdrinfo.com/Sections/Reviews/Specific.aspx?ArticleId=23814)

It's strange that this drive should be recognized as an SATA one. But after carefully reading your first post again there is this line that I overlooked: "I get an 'invalid mount option' error".
please make sure that cdrom0 does exist by :
 cd /media
 dir

and see if cdrom or cdrom0 is there.
and try this:
/dev/cdrom  	/media/cdrom  	auto  	ro,auto,user,exec  	0 0

Rgds.
Thanks for the reply tenmoi.
Still no joy.
I checked /media and cdrom0 is there as an directory. I tried the entry '/dev/cdrom' and get the cannot mount error attached to my last post. programs like K3b and K9copy fail with cannot open /dev/scd0. Before I read your reply I put a knoppix disk in the drive to see if it would boot, it auto mounted and was readable. It also booted. I check the link and that is the drive, the sheet that came with the drive states Interface is 'PIO Mode 4, Multi word DMA mode 2, Ultra DMA mode 4' is that PATA? Any other ideas?

---

### Post by huntzire on 2009-07-02
I posted about this a while back and got no traction on it,

My DVDroms plextor and samsung dont work at all either, the fact that dmesg detects them as PATA but fails.

Works on every version up to 8.10

very anooying for ubuntu to get much better in most of the desktop experience only to fail flat in DVDrom detection

---

### Post by tenmoi on 2009-07-03
> **jdh said:**
> Thanks for the reply tenmoi.
Still no joy.
I checked /media and cdrom0 is there as an directory. I tried the entry '/dev/cdrom' and get the cannot mount error attached to my last post. programs like K3b and K9copy fail with cannot open /dev/scd0. Before I read your reply I put a knoppix disk in the drive to see if it would boot, it auto mounted and was readable. It also booted. I check the link and that is the drive, the sheet that came with the drive states Interface is 'PIO Mode 4, Multi word DMA mode 2, Ultra DMA mode 4' is that PATA? Any other ideas?

THis is definitely maddening, but as a last resort you could:
+ Replace your new dvd drive with the old one and see if the latter works. IF it does then replace it with the new one and try as follows:

+ Comment out the dev/cdrom in the etc/fstab file and everything related to cdrom.
+ Then reboot, then pop in a music cdrom and see if ubuntu will automatically offer to play it.
+ If it won't, you can eject it and then pop in a data cd or dvd and then 
sudo mount -t iso9660 /dev/cdrom /media/cdrom0 -o loop,unhide,ro
+++++REMEMBER to use a data cd, you cannot mount a (music) cd this way.
+ And this is the very last resort: YOur dvd drive needs a firmware update because there might be a bug with it. CHeck it out on the PIONEER website and see if there's any update for it. 

P.S
This is the fstab file on my 32 bit jaunty.
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=78a061b9-0209-4e0c-9e63-93a855e52c84 /               ext4    relatime,erro$

+And this is the fstab file on my debian lenny 64:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda8       /               ext3    errors=remount-ro 0       1
#/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
#/dev/sdc1       /media/sdcard   vfat   rw,nosuid,nodev,user,noauto     0       0

I commented out the line containing /cdrom as I don't want the system to automount cdrom and you see the /scd0 because this is an SATA ASUS dvd-rom

---

### Post by tenmoi on 2009-07-03
YOu could look at this thread, post #25

[http://ubuntuforums.org/showthread.php?t=34516&page=3](http://ubuntuforums.org/showthread.php?t=34516&page=3)

---

### Post by jdh on 2009-07-03
Thanks tenmoi for pointing me in the right direction. I was totally confused. I replaced the IDE cable! Commented out all the 'CD" entries in fstab. Now all media automounts (haven't tried r\w disks). Programs can now access /dev/scd0. Now dmesg shows PATA being set-up. Have not tried burning anything yet but I think it will work. I'll go back and try my old drive on my other IDE controller when I get another cable.

Rgds.

---

### Post by tenmoi on 2009-07-03
Glad that I could help.

I don't want to sound patronizing but next time if you should have a problem just do a google, for example: problem with Pioneer xyz on linux and you will not have to spend your time waiting.

:p

---

