---
title: "[SOLVED] Update Killed Grub"
date: 2008-05-28
forum: x86 64-bit Users
---

### Post by Plasma_NZ on 2008-05-28
Ok, just did the latest update right.. for kernel etc using updater etc...

Now when it loads grun and i select the enw kernel - it gives me the error 

error 22 - no such partition 

Need help..

---

### Post by zenwalker on 2008-05-28
Edit the kernel line and give the correct root path including the device.

---

### Post by Plasma_NZ on 2008-05-28
thanks... it was hd2,7 previously, now its apparerntly hd4,7

didnt have to edit the kernel line though... But its just stuck ont he ubuntu screen with the orange bar going back and forth
also apepars grubs installed on 2 hdd's... things are a bit messy

also since that update grub doesnt show the new kernel either..

---

### Post by Plasma_NZ on 2008-05-28
Ok.. im using the new kernel, but its not in my /boot/grub/menu.lst

I use hd4,7 and edited kernel to 17 from 16 in the line... 

how do i fix this so when i reboot i dont have issues..?

Also now when i try to dual-boot windows, i get the NTlDR missing error...

```

title		Ubuntu hardy (development branch), kernel 2.6.24-16-generic
root		(hd2,7)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=d910ab71-a3f6-4985-a42e-57a1a72dd26f ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

#title		Ubuntu hardy (development branch), kernel 2.6.24-16-generic (recovery mode)
#root		(hd2,7)
#kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=d910ab71-a3f6-4985-a42e-57a1a72dd26f ro single
#initrd		/boot/initrd.img-2.6.24-16-generic

#title		Ubuntu hardy (development branch), kernel 2.6.24-15-generic
#root		(hd2,7)
#kernel		/boot/vmlinuz-2.6.24-15-generic root=UUID=d910ab71-a3f6-4985-a42e-57a1a72dd26f ro quiet #splash
#initrd		/boot/initrd.img-2.6.24-15-generic
#quiet

#title		Ubuntu hardy (development branch), kernel 2.6.24-15-generic (recovery mode)
#root		(hd2,7)
#kernel		/boot/vmlinuz-2.6.24-15-generic root=UUID=d910ab71-a3f6-4985-a42e-57a1a72dd26f ro single
#initrd		/boot/initrd.img-2.6.24-15-generic

#title		Ubuntu hardy (development branch), kernel 2.6.24-12-generic
#root		(hd2,7)
#kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=d910ab71-a3f6-4985-a42e-57a1a72dd26f ro quiet #splash
#initrd		/boot/initrd.img-2.6.24-12-generic
#quiet

#title		Ubuntu hardy (development branch), kernel 2.6.24-12-generic (recovery mode)
#root		(hd2,7)
#kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=d910ab71-a3f6-4985-a42e-57a1a72dd26f ro single
#initrd		/boot/initrd.img-2.6.24-12-generic

#title		Ubuntu hardy (development branch), kernel 2.6.24-11-generic
#root		(hd2,7)
#kernel		/boot/vmlinuz-2.6.24-11-generic root=UUID=d910ab71-a3f6-4985-a42e-57a1a72dd26f ro quiet #splash
#initrd		/boot/initrd.img-2.6.24-11-generic
#quiet

#title		Ubuntu hardy (development branch), kernel 2.6.24-11-generic (recovery mode)
#root		(hd2,7)
#kernel		/boot/vmlinuz-2.6.24-11-generic root=UUID=d910ab71-a3f6-4985-a42e-57a1a72dd26f ro single
#initrd		/boot/initrd.img-2.6.24-11-generic

#title		Ubuntu hardy (development branch), kernel 2.6.24-8-generic
#root		(hd2,7)
#kernel		/boot/vmlinuz-2.6.24-8-generic root=UUID=d910ab71-a3f6-4985-a42e-57a1a72dd26f ro quiet #splash
#initrd		/boot/initrd.img-2.6.24-8-generic
#quiet

#title		Ubuntu hardy (development branch), kernel 2.6.24-8-generic (recovery mode)
#root		(hd2,7)
#kernel		/boot/vmlinuz-2.6.24-8-generic root=UUID=d910ab71-a3f6-4985-a42e-57a1a72dd26f ro single
#initrd		/boot/initrd.img-2.6.24-8-generic

#title		Ubuntu hardy (development branch), memtest86+
#root		(hd2,7)
#kernel		/boot/memtest86+.bin
#quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP (loader)
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

```

heres the results of fdisk -l

> Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1346f02c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           2       30401   244188000    f  W95 Ext'd (LBA)
/dev/sda5               2       30401   244187968+   7  HPFS/NTFS

Disk /dev/sdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x81521c42

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       36481   293025600    f  W95 Ext'd (LBA)
/dev/sdb5               2       36481   293025568+   7  HPFS/NTFS

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9b9d9b9d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1286    10329763+   7  HPFS/NTFS
/dev/sdc2            1287        9729    67818397+   f  W95 Ext'd (LBA)
/dev/sdc5            1287        2572    10329763+   7  HPFS/NTFS
/dev/sdc6            2573        8453    47239101    7  HPFS/NTFS
/dev/sdc7            8454        8725     2184808+  82  Linux swap / Solaris
/dev/sdc8            8726        9729     8064598+  83  Linux

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
16 heads, 63 sectors/track, 969021 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x64849989

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1      969018   488385040+   7  HPFS/NTFS


---

### Post by danwood76 on 2008-05-28
Which partitions are you trying to boot from?

HD2 (sdc) looks like it might be the one you are trying to boot from.
The only issue you will get is if you try and boot from a different drive within your BIOS the mapping will change in grub.

Which drive have you got it set to boot from within your BIOS?

---

### Post by Plasma_NZ on 2008-05-28
> **danwood76 said:**
> Which partitions are you trying to boot from?

HD2 (sdc) looks like it might be the one you are trying to boot from.
The only issue you will get is if you try and boot from a different drive within your BIOS the mapping will change in grub.

Which drive have you got it set to boot from within your BIOS?

i believe that'd be the 250gb.. which does not contain a OS, the OS's are on the 80gb, which has, winxp32, winxp64, ubuntu hardy 64bit

Which is hd4, it was hd2 for ages until the last kerel update from -16 to -17.. then all of a sudden all this happened...

---

### Post by danwood76 on 2008-05-28
The 80 GB is HD2, you count from 0 so 
HD0 = sda = 250GB 
HD1 = sdb = 300GB 
HD2 = sdc = 80GB
HD3 = sdd = 500GB
You have no HD4.

Your menu.lst looks correct but it will only be correct if your BIOS is set to boot from the first drive. (which you have said you are).

hd2,7 looks like the linux boot partition to me.
I would reinstall grub from the live CD, it may be that somethings conusing it with respect to the drive order.

Good guide to it:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

And to automatically install OS's to your grub you just do:
```

sudo update-grub

```

---

### Post by Plasma_NZ on 2008-05-28
Ok far as i know, grubs not lookin int he right place now for the windows boot.ini etc.. or the boot.ini is now incorrect due to unseen changes in the paritions.?

Dont really wanna mess with live cd again.. too much hassle..

Would like to point-out i actually reinstalled grub yesterday with the method mentioned in that howto u linked... didnt work... still spits the ntldr error.. i'm presuming the problem above i mentioned...

---

### Post by Plasma_NZ on 2008-05-28
Ok - tryed that - still gettin the same error..

Basically this is what i know...

Windows bootloader is installed on the 80gb, grub is on the 250gb..

idohavea cd here with a fix ntldr thing which bypass's all bootloaders and forces it to load winxp32, not that i wish to use that every time i ant to use windows 

I think grub is pointing to the wrong place for the windows bootloader..

fdisk -l

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1346f02c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           2       30401   244188000    f  W95 Ext'd (LBA)
/dev/sda5               2       30401   244187968+   7  HPFS/NTFS

Disk /dev/sdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x81521c42

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       36481   293025600    f  W95 Ext'd (LBA)
/dev/sdb5               2       36481   293025568+   7  HPFS/NTFS

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9b9d9b9d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1286    10329763+   7  HPFS/NTFS
/dev/sdc2            1287        9729    67818397+   f  W95 Ext'd (LBA)
/dev/sdc5            1287        2572    10329763+   7  HPFS/NTFS
/dev/sdc6            2573        8453    47239101    7  HPFS/NTFS
/dev/sdc7            8454        8725     2184808+  82  Linux swap / Solaris
/dev/sdc8            8726        9729     8064598+  83  Linux

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
16 heads, 63 sectors/track, 969021 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x64849989

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1      969018   488385040+   7  HPFS/NTFS

```

grub menu.lst

```

title		Ubuntu hardy kernel 2.6.24-17-generic
root		(hd4,7)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=d910ab71-a3f6-4985-a42e-57a1a72dd26f ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu hardy (development branch), kernel 2.6.24-16-generic
root		(hd2,7)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=d910ab71-a3f6-4985-a42e-57a1a72dd26f ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

#title		Ubuntu hardy (development branch), kernel 2.6.24-16-generic (recovery mode)
#root		(hd2,7)
#kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=d910ab71-a3f6-4985-a42e-57a1a72dd26f ro single
#initrd		/boot/initrd.img-2.6.24-16-generic

#title		Ubuntu hardy (development branch), kernel 2.6.24-15-generic
#root		(hd2,7)
#kernel		/boot/vmlinuz-2.6.24-15-generic root=UUID=d910ab71-a3f6-4985-a42e-57a1a72dd26f ro quiet #splash
#initrd		/boot/initrd.img-2.6.24-15-generic
#quiet

#title		Ubuntu hardy (development branch), kernel 2.6.24-15-generic (recovery mode)
#root		(hd2,7)
#kernel		/boot/vmlinuz-2.6.24-15-generic root=UUID=d910ab71-a3f6-4985-a42e-57a1a72dd26f ro single
#initrd		/boot/initrd.img-2.6.24-15-generic

#title		Ubuntu hardy (development branch), kernel 2.6.24-12-generic
#root		(hd2,7)
#kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=d910ab71-a3f6-4985-a42e-57a1a72dd26f ro quiet #splash
#initrd		/boot/initrd.img-2.6.24-12-generic
#quiet

#title		Ubuntu hardy (development branch), kernel 2.6.24-12-generic (recovery mode)
#root		(hd2,7)
#kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=d910ab71-a3f6-4985-a42e-57a1a72dd26f ro single
#initrd		/boot/initrd.img-2.6.24-12-generic

#title		Ubuntu hardy (development branch), kernel 2.6.24-11-generic
#root		(hd2,7)
#kernel		/boot/vmlinuz-2.6.24-11-generic root=UUID=d910ab71-a3f6-4985-a42e-57a1a72dd26f ro quiet #splash
#initrd		/boot/initrd.img-2.6.24-11-generic
#quiet

#title		Ubuntu hardy (development branch), kernel 2.6.24-11-generic (recovery mode)
#root		(hd2,7)
#kernel		/boot/vmlinuz-2.6.24-11-generic root=UUID=d910ab71-a3f6-4985-a42e-57a1a72dd26f ro single
#initrd		/boot/initrd.img-2.6.24-11-generic

#title		Ubuntu hardy (development branch), kernel 2.6.24-8-generic
#root		(hd2,7)
#kernel		/boot/vmlinuz-2.6.24-8-generic root=UUID=d910ab71-a3f6-4985-a42e-57a1a72dd26f ro quiet #splash
#initrd		/boot/initrd.img-2.6.24-8-generic
#quiet

#title		Ubuntu hardy (development branch), kernel 2.6.24-8-generic (recovery mode)
#root		(hd2,7)
#kernel		/boot/vmlinuz-2.6.24-8-generic root=UUID=d910ab71-a3f6-4985-a42e-57a1a72dd26f ro single
#initrd		/boot/initrd.img-2.6.24-8-generic

#title		Ubuntu hardy (development branch), memtest86+
#root		(hd2,7)
#kernel		/boot/memtest86+.bin
#quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP (loader)
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

```

---

### Post by xebian on 2008-05-28
> **Plasma_NZ said:**
> Ok far as i know, grubs not lookin int he right place now for the windows boot.ini etc.. or the boot.ini is now incorrect due to unseen changes in the paritions.?

Dont really wanna mess with live cd again.. too much hassle..

Would like to point-out i actually reinstalled grub yesterday with the method mentioned in that howto u linked... didnt work... still spits the ntldr error.. i'm presuming the problem above i mentioned...

Instead of looking for the stage 1 file, it looks like it's in hd2,7.  So open a terminal and then execute these

```

sudo grub   <=== this will give you a grub command prompt *grub>*

grub> root (hd2,7)
grub> setup (hd2)

( you should see some 'success' msgs )

Control + c to exit.


```

The update-grub now prompts you with several options and the default is to keep your existing menu.  Otherwise, if you are not sure, decline the change and then manually change it later by editing the file in /boot/grub/menu.lst

---

### Post by Plasma_NZ on 2008-05-28
Doest work... grub does work fine and will load ubuntu - the problem is when in grub i can either select ubuntu or "Windows Bootloader"

When i select windows bootloader it spits that error 22 ntldr not found etc..

---

### Post by meierfra. on 2008-05-28
Is this correct:

1) The grub menu appears at boot and you are able to boot into the new kernel by pressing "e"  few times, changing "root (hd2,7)" to "root (hd4,7)" and  "-16" to "-17".

2)  You have not made any changes "menu.lst"?


If this is correct, you should be able to solve your problems as follows.

Boot into Ubuntu, open a terminal and open "menu.lst" via

```
gksudo gedit /boot/grub/menu.lst
```

Look for the line

#groot (hd2,7)

and change it to

#groot (hd4,7)


Next look for

title		Windows NT/2000/XP (loader)
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)

and change all the "2"'s  to "4"'s:


title		Windows NT/2000/XP (loader)
root		(hd4,0)
savedefault
makeactive
map		(hd0) (hd4)
map		(hd4) (hd0)

Also its seems you do not want all the old kernel's listed in the Grub Menu. So change

# howmany=all

to 

# howmany=1  (or # howmany=2)


Save the file.


In the terminal type 

```
sudo update-grub
```

This should be it. Just to double check, have  another look at "menu.lst":

The new kernel should be on the list, and all "(hd2,7)" should have changed to "(hd4,7)".

---

### Post by Plasma_NZ on 2008-05-28
> **meierfra. said:**
> Is this correct:

1) The grub menu appears at boot and you are able to boot into the new kernel by pressing "e"  few times, changing "root (hd2,7)" to "root (hd4,7)" and  "-16" to "-17".

2)  You have not made any changes "menu.lst"?


If this is correct, you should be able to solve your problems as follows.

Boot into Ubuntu, open a terminal and open "menu.lst" via

```
gksudo gedit /boot/grub/menu.lst
```

Look for the line

#groot (hd2,7)

and change it to

#groot (hd4,7)


Next look for

title		Windows NT/2000/XP (loader)
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)

and change all the "2"'s  to "4"'s:


title		Windows NT/2000/XP (loader)
root		(hd4,0)
savedefault
makeactive
map		(hd0) (hd4)
map		(hd4) (hd0)

Also its seems you do not want all the old kernel's listed in the Grub Menu. So change

# howmany=all

to 

# howmany=1  (or # howmany=2)


Save the file.


In the terminal type 

```
sudo update-grub
```

This should be it. Just to double check, have  another look at "menu.lst":

The new kernel should be on the list, and all "(hd2,7)" should have changed to "(hd4,7)".

Chur, u the man, and i cant believe overlooked doing that LOL

Thanks meierfra. all workin now.. also thanks to all u others who helped trouble-shoot this..

---

### Post by inphektion on 2008-05-29
Just curious why this happened?  If he used UID's would this not have been an issue?

---

### Post by danwood76 on 2008-05-29
grub doesnt use UUID's, the UUID's are passed on to the kernel as options.
the root (hdx,x) sets the partition it boots from.

---

