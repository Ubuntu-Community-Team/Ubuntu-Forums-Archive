---
title: "adding ext4 module and initramfs-tools"
date: 2008-11-21
forum: x86 64-bit Users
---

### Post by denisius on 2008-11-21
I compiled and use 2.6.28-rc5 kernel with ext4 fs, also I enabled ext4dev compatibility. Than I convert my /home partition to ext4 extents and it works perfectly, than I converted root to ext4 extents and moved /boot to separate partition witch has ext2 fs ... and I have busybox during startup... I tried put  MODULES=list to initramfs.cfg and added ext4 to /etc/initramfs-tools/modules and updated/created new initrd image - still same result... So kernel works perfectly with ext4... I can mount ext4 from busybox... Also I tried to compile kernel where ext4 is as part of kernel, not a module - same result... then I set debug flag due to debugfs -w /dev/sda5

set_super_value s_flags 4
quit

and changed in fstab ext4 to ext4dev for /
and after that I can load my system.

but after each startup I have to set that flag again otherwise I canot load...

So, I have conclusion that initramfs-tools doesnt support ext4, just ext4dev, and I think that it easy to fix somewhere in scripts, but I  don´t know where...
  

Also I tried yaird as alternative of iniramfs-tools but it doesn´t work:

# yaird --test 2.6.28-rc5-x64.3
Entries in fstab:
	/etc/fstab:4: /proc at proc (proc) with defaults=-
		
	/etc/fstab:5: . at /dev/sda5 (ext4dev) with rw=-
		-o 'rw'
	/etc/fstab:6: /boot at /dev/sda8 (ext2) with relatime=-
		-o 'relatime'
	/etc/fstab:7: /home at /dev/sda6 (ext4) with rw=-
		-o 'rw'
	/etc/fstab:8: none at /dev/sda7 (swap) with sw=-
		-o 'sw'
	/etc/fstab:9: /media/cdrom0 at /dev/scd0 (udf,iso9660) with exec=-,noauto=-,user=-,utf8=-
		-o 'exec,utf8'
	/etc/fstab:11: /proc/bus/usb at none (usbfs) with devgid=123,devmode=664
		-o 'devgid=123,devmode=664'
Block special files /dev:
	11:0: /dev/scd0
	1:0: /dev/.static/dev/ram0, /dev/ram0
	1:1: /dev/.static/dev/ram1, /dev/ram1
	1:10: /dev/.static/dev/ram10, /dev/ram10
	1:11: /dev/.static/dev/ram11, /dev/ram11
	1:12: /dev/.static/dev/ram12, /dev/ram12
	1:13: /dev/.static/dev/ram13, /dev/ram13
	1:14: /dev/.static/dev/ram14, /dev/ram14
	1:15: /dev/.static/dev/ram15, /dev/ram15
	1:16: /dev/.static/dev/ram16
	1:2: /dev/.static/dev/ram2, /dev/ram2
	1:3: /dev/.static/dev/ram3, /dev/ram3
	1:4: /dev/.static/dev/ram4, /dev/ram4
	1:5: /dev/.static/dev/ram5, /dev/ram5
	1:6: /dev/.static/dev/ram6, /dev/ram6
	1:7: /dev/.static/dev/ram7, /dev/ram7
	1:8: /dev/.static/dev/ram8, /dev/ram8
	1:9: /dev/.static/dev/ram9, /dev/ram9
	7:0: /dev/loop0, /dev/.static/dev/loop0
	7:1: /dev/.static/dev/loop1
	7:2: /dev/.static/dev/loop2
	7:3: /dev/.static/dev/loop3
	7:4: /dev/.static/dev/loop4
	7:5: /dev/.static/dev/loop5
	7:6: /dev/.static/dev/loop6
	7:7: /dev/.static/dev/loop7
	8:0: /dev/sda
	8:3: /dev/sda3
	8:5: /dev/sda5
	8:6: /dev/sda6
	8:7: /dev/sda7
	8:8: /dev/sda8
Labeled partitions detected:
yaird error: bad device link in /sys/block/sda (fatal)



So if anybody can help me or anybody has interest to ext4 I will be so happy:)

---

### Post by livello on 2008-12-05
I use 2.6.27-4 with ext4 as *. 
I put > tune2fs -E test_fs /dev/sda1
into /etc/init.d/rc.local file. 
So no need to do it manually.

---

### Post by livello on 2009-01-09
rootfstype=ext4 in grub

It works on linux kernel 2.6.28-4.9.

---

### Post by overflow_ on 2009-03-19
> **denisius said:**
> I compiled and use 2.6.28-rc5 kernel with ext4 fs, also I enabled ext4dev compatibility. Than I convert my /home partition to ext4 extents and it works perfectly, than I converted root to ext4 extents and moved /boot to separate partition witch has ext2 fs ... and I have busybox during startup... I tried put  MODULES=list to initramfs.cfg and added ext4 to /etc/initramfs-tools/modules and updated/created new initrd image - still same result... So kernel works perfectly with ext4... I can mount ext4 from busybox... Also I tried to compile kernel where ext4 is as part of kernel, not a module - same result... then I set debug flag due to debugfs -w /dev/sda5

set_super_value s_flags 4
quit

and changed in fstab ext4 to ext4dev for /
and after that I can load my system.

but after each startup I have to set that flag again otherwise I canot load...

So, I have conclusion that initramfs-tools doesnt support ext4, just ext4dev, and I think that it easy to fix somewhere in scripts, but I  don´t know where...
  

Also I tried yaird as alternative of iniramfs-tools but it doesn´t work:

# yaird --test 2.6.28-rc5-x64.3
Entries in fstab:
	/etc/fstab:4: /proc at proc (proc) with defaults=-
		
	/etc/fstab:5: . at /dev/sda5 (ext4dev) with rw=-
		-o 'rw'
	/etc/fstab:6: /boot at /dev/sda8 (ext2) with relatime=-
		-o 'relatime'
	/etc/fstab:7: /home at /dev/sda6 (ext4) with rw=-
		-o 'rw'
	/etc/fstab:8: none at /dev/sda7 (swap) with sw=-
		-o 'sw'
	/etc/fstab:9: /media/cdrom0 at /dev/scd0 (udf,iso9660) with exec=-,noauto=-,user=-,utf8=-
		-o 'exec,utf8'
	/etc/fstab:11: /proc/bus/usb at none (usbfs) with devgid=123,devmode=664
		-o 'devgid=123,devmode=664'
Block special files /dev:
	11:0: /dev/scd0
	1:0: /dev/.static/dev/ram0, /dev/ram0
	1:1: /dev/.static/dev/ram1, /dev/ram1
	1:10: /dev/.static/dev/ram10, /dev/ram10
	1:11: /dev/.static/dev/ram11, /dev/ram11
	1:12: /dev/.static/dev/ram12, /dev/ram12
	1:13: /dev/.static/dev/ram13, /dev/ram13
	1:14: /dev/.static/dev/ram14, /dev/ram14
	1:15: /dev/.static/dev/ram15, /dev/ram15
	1:16: /dev/.static/dev/ram16
	1:2: /dev/.static/dev/ram2, /dev/ram2
	1:3: /dev/.static/dev/ram3, /dev/ram3
	1:4: /dev/.static/dev/ram4, /dev/ram4
	1:5: /dev/.static/dev/ram5, /dev/ram5
	1:6: /dev/.static/dev/ram6, /dev/ram6
	1:7: /dev/.static/dev/ram7, /dev/ram7
	1:8: /dev/.static/dev/ram8, /dev/ram8
	1:9: /dev/.static/dev/ram9, /dev/ram9
	7:0: /dev/loop0, /dev/.static/dev/loop0
	7:1: /dev/.static/dev/loop1
	7:2: /dev/.static/dev/loop2
	7:3: /dev/.static/dev/loop3
	7:4: /dev/.static/dev/loop4
	7:5: /dev/.static/dev/loop5
	7:6: /dev/.static/dev/loop6
	7:7: /dev/.static/dev/loop7
	8:0: /dev/sda
	8:3: /dev/sda3
	8:5: /dev/sda5
	8:6: /dev/sda6
	8:7: /dev/sda7
	8:8: /dev/sda8
Labeled partitions detected:
yaird error: bad device link in /sys/block/sda (fatal)



So if anybody can help me or anybody has interest to ext4 I will be so happy:)

I have the same problem!!! How did you fix it?
Is there someone that can give me some tips?

---

### Post by loomsen on 2009-03-19
Install a master boot record on your desired boot partition.

```
sudo apt-get update && sudo apt-get install mbr
```

It will install a cpl of docs, a manual(8) and a binary named install-mbr.

First I'd  want to do this:
```

man 8 install-mbr
```

and make sure I know what I want to do.

Then, after you gathered some information, open up a terminal, become root and install MBR:

```

sudo su -
install-mbr [options] <your_designated_boot_device>
exit

```

Note: you can specify the device to install to whichever way you want, just notice grubs annotation.

The first partition of your primary harddisk equals to:
hd(0,0) BUT /dev/[h|s]d[color=red]a1[/color]

hd(0,3) would equal /dev/hd[color=red]a4[/color]

and 

hd(1,2) equals /dev/hd[color=red]b3[/color]

---

### Post by overflow_ on 2009-03-20
Thank you for the quick answer.

but why there where this error?
> 
yaird error: bad device link in /sys/block/sda (fatal)

Is it because it doesn't know in which partition it has to install the image?


So in my case I have Ubuntu in /dev/sda5 .... so I have to type

install-mbr /dev/sda5

are there some dangerous mistakes in what I am going to do?


Thank you very much



> **loomsen said:**
> Install a master boot record on your desired boot partition.

```
sudo apt-get update && sudo apt-get install mbr
```

It will install a cpl of docs, a manual(8) and a binary named install-mbr.

First I'd  want to do this:
```

man 8 install-mbr
```

and make sure I know what I want to do.

Then, after you gathered some information, open up a terminal, become root and install MBR:

```

sudo su -
install-mbr [options] <your_designated_boot_device>
exit

```

Note: you can specify the device to install to whichever way you want, just notice grubs annotation.

The first partition of your primary harddisk equals to:
hd(0,0) BUT /dev/[h|s]d[color=red]a1[/color]

hd(0,3) would equal /dev/hd[color=red]a4[/color]

and 

hd(1,2) equals /dev/hd[color=red]b3[/color]

---

