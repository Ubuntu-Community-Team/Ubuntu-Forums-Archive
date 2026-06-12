---
title: "Will not mount NTFS drive"
date: 2006-06-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by TechMage89 on 2006-06-08
I have recently installed Ubuntu 6.06 on my second hard drive (reformatted it). When I try to access my main drive (with Windows XP and all my important files) from Ubuntu, I get a mounting error. What could be causing this?
This is my first time installing any linux distro, so please use small words.

---

### Post by kb3hkg on 2006-06-08
please post the error, it would be really helpful. It is hard to say what is wrong otherwise.

---

### Post by TechMage89 on 2006-06-08
Here is the error:

Unable to mount the selected volume
      error: device /dev/hda2 is not removable
      error: could not execute pmount

---

### Post by tzenes on 2006-06-08
This may or may not be the solution to your problem, but windows doesn't like being booted off the slave drive

so open up /boot/grub/menu.lst

which should look something like this:

```
title Windows
rootnoverify (hd1,0)
makeactive
chainloader +1
```

and add the following:
```
title Windows
rootnoverify (hd1,0)
makeactive
chainloader +1
[B]map (hd1) (hd0)
map (hd0) (hd1)[/B]
```

now I'm assuming windows is booting off the first partition of hdb.

if for example it was on the third partition of hdb then you would want

```
title Windows
**rootnoverify (hd1,2)**
makeactive
chainloader +1
map (hd1) (hd0)
map (hd0) (hd1)
```

if you post your
```
 $cat /etc/mtab
```
I can figure out what the values should be (assuming this is your problem)

---

### Post by TechMage89 on 2006-06-08
Well, windows isn't actually being booted off the slave drive, ubuntu just set up its drive as hd1 for some reason. I will try what you suggested, though.

---

### Post by mattm591 on 2006-06-09
Hi,
I'm having a similar problem trying to use access my Windows drive. When I double click the icon for it in "Computer" I get the error,
> 
Unable to mount the selected volume
error: device /dev/sda1 is not removable

error: could not execute pmount

Would what you put above solve this? I am using SATA and I think Windows is installed onto SATA1 and Ubuntu on SATA2

I ran the cat /etc/mtab command and got this output:
> 
/dev/mapper/Ubuntu-root / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
/sys /sys sysfs rw 0 0
varrun /var/run tmpfs rw 0 0
varlock /var/lock tmpfs rw 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
devshm /dev/shm tmpfs rw 0 0
/dev/sdb5 /boot ext3 rw 0 0
/dev/hdb /media/cdrom1 iso9660 ro,noexec,nosuid,nodev,user=matt 0 0


---

### Post by danellisuk on 2006-07-14
I too am having this problem.

On a newly installed 6.06 all my windows partitions are not accessible with the error:-

**Unable to mount the selected volume.**
error: device /dev/sda2 is not removable
error: could not execute pmount


(This did work on 5.10 which I had on for about a day before realising there was 6.06)

I have tried mounting from the command line using:-
"sudo mount /dev/sdb1 /mnt/data_drive"

Which works, but then the mount point is only accessable from the command line when using "sudo su".

Is their a way to mount the partition in a way so that I can browse and use the partition with the file browser gui?

Regards,
Daniel Ellis.

---

### Post by Lil_Eagle on 2006-07-15
modify the file /etc/fstab and add your windows drive there.  Make sure you mount it read only.

Here's a line similar to what you need.
```
/dev/sdb1 /mnt/data ntfs ro,auto 0 0

```

---

### Post by Washington Irving on 2006-07-15
I am also having this problem and have tried the two methods listed here but neither seemed to work although I can open it as root.

---

### Post by walkerx on 2006-07-15
this is how i've set my fstab to read my ntfs drive

/dev/sda2	/windows/downloads	ntfs	nls=utf8,umask=0222 0 0

this works fine under latest 64bit kernel as well as the last 2

to get the right drive assignment goto system, administration, disks

this showed me what devices they actually were, so i created a windows\downloads folder

i then used umount -a

and then edited /etc/fstab

and then re mounted them

---

### Post by danellisuk on 2006-07-18
I have found the answer !!

(I'm new to this though so bare with me if anything is wrong.)

The problem is when clicking on 'Places' then 'Computer' in ubuntu 6.06.  The windows partitions which are automatically detected are not accessible, and you receive the following error:-

**Unable to mount the selected volume**
error: device /dev/hda2 is not removable
error: could not execute pmount

This is because pmount is being used by the system instead of mount.  pmount is used because it can be executed by normal users.  However pmount is designed for removable media and only if the user has the permission to mount removable devices.

I looked in the help for pmount, by typing 'man pmount' and found that non-removable devices can also be mounted if they are listed in the pmount.allow file.

So edit the file and add the device to the end of the file.  In my case I typed 'sudo vi /etc/pmount.allow'

Then navigated to the end of the file.  Pressed 'a' for append.  Then typed the device.  For me that was:-

/dev/sdb1

I then saved the file by typing

Esc : wq Enter

I was then able to mount the partition using the browser.

Hope that helps, its been very interesting learning this so far!

Daniel Ellis.

[Edit:  Ive just noticed this is in a 64bit forum.  I'm using the  x86 version, so I suppose this issue is not 64bit specific]

---

### Post by happyisland on 2006-07-18
Just wanted to write to say thanks to danellisuk for the solution to my beginner problem. My NTFS drive now works! 
Now, would you please explain how to get skype and flash to work in 64?
Thanks again,
HI

---

### Post by papichulo on 2008-04-15
well it work for me too...

instead of "vi"

i used this:

```
sudo gedit /etc/pmount.allow
```

its much more easier.
:)

---

