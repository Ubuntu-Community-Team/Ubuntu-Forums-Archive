---
title: "PROBLEM : insmod: can't read, no such file or directory"
date: 2006-03-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by PsychoSync on 2006-03-16
This is what appears in console when i try to start GDM.

More precisely : 

insmod : can't read '/lib/modules ... /video/console/bitblit.ko ': no such file or directory

and these other files too : 

font.ko
tileblit.ko
fbcon.ko
cfbcopyarea.ko
cfbfillrect.ko
cfbimgblt.ko
softcursor.ko
vgastate.ko
vga16fb.ko

How do i repair this?

---

### Post by mtlhead on 2006-03-16
I get taht too...any help would be greatly appreciated

---

### Post by ssam on 2006-03-16
how are you starting GDM? has it ever worked? is this in breezy?

---

### Post by mtlhead on 2006-03-16
I'm using open firmware to boot (hold option and select os), mine has never worked.  Yes, this is breezy (version 5.10...right?)

---

### Post by mtlhead on 2006-03-16
Name : 	disk0s5
	Type : 	Volume

	Disk Identifier : 	disk0s5
	Mount Point : 	Not mounted
	Connection Bus : 	ATA
	Partition Type : 	Apple_UNIX_SVR2
	Device Tree : 	first-boot/@0:5
	Writable : 	Yes
	Capacity : 	59.2 GB (63,533,686,272 Bytes)
	Owners Enabled : 	No
	Can Turn Owners Off : 	No
	Can Be Formatted : 	No
	Bootable : 	No
	Supports Journaling : 	No
	Journaled : 	No
	S.M.A.R.T. Status : 	Verified
	Disk Number : 	0
	Partition Number : 	5


Thats the partition info if it helps

---

### Post by tidris on 2006-03-16
[QUOTE=PsychoSync]This is what appears in console when i try to start GDM.

More precisely : 

insmod : can't read '/lib/modules ... /video/console/bitblit.ko ': no such file or directory

and these other files too : 

font.ko
tileblit.ko
fbcon.ko
cfbcopyarea.ko
cfbfillrect.ko
cfbimgblt.ko
softcursor.ko
vgastate.ko
vga16fb.ko

How do i repair this?[/QUOTE]
I don't know if this will help you, but on my G3 PowerBook that is running ubuntu 5.10 most of those files do not exist. Based on the error message you posted it is obvious they don't exist on your installation either. I have no idea why ubuntu would be trying to access non-existing files on your installation.

---

### Post by mtlhead on 2006-03-16
Well i got mine working now, i repartitioned and let ubuntu take care of it, and it worked right.

---

### Post by PsychoSync on 2006-03-17
Well the problem is solved now... I just reinstalled Ubuntu and it worked! But with 64m RaM, it's really slow:-|  

When i rebooted the first time while installing, i looked at the console and the same errors showed but it worked.

Ubuntu or YellowDog 4.1 are too heavy to run on an old iMac 233 with only 64m RAM, today i ordered 128m for the mac so i will make 192m, it will help a lot but i don't think thats enough to make Ubuntu run smoothly on a rev-B iMac... So i have a question : If i install an old version of Yellow Dog Linux (wich is more targeted at PPC machines so i think it would run well (please correct me if i'm wrong)) can i compile the latest firefox to run on my iMac?

What i WANT IS to install an os that has an up to date browser, good mp3 player and that runs really smooth on an iMac 233 with 192m RAM, please help!

---

