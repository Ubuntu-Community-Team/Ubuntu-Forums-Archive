---
title: "Strange 'bug' with SATA drive and grub."
date: 2005-06-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by alep on 2005-06-23
I've got and ASUS A8V Deluxe motherboard, it's got two drives, 
a sata drive (/dev/sda1) and 'a normal' one (/dev/hda).

Drive information follows:

```

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         608     4883728+  83  Linux
/dev/sda2             609        3040    19535040   83  Linux
/dev/sda3            3041        3222     1461915   82  Linux swap / Solaris
/dev/sda4            3223       10011    54532642+   5  Extended
/dev/sda5            3223       10011    54532611   83  Linux

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1776    14265688+  83  Linux
/dev/hda4            1777        9729    63882472+   f  W95 Ext'd (LBA)
/dev/hda5            1777        9729    63882441   83  Linux

``` 

/dev/hda has data from a previous linux instal which is not to be touched.

and /dev/sda1 is an untouched (hidden) partition left for future use... windows maybe :P

Ubuntu exists in /dev/sda. Grub is installed in the master boot record of /dev/sda
grub's device map.

```

(hd0)   /dev/hda
(hd1)   /dev/sda

``` 

Now clearly root should be root(hd1,1) where /boot lies, the trouble is when grub
start it shows error 15 (file doesn't exist I think)
<edit>
actully it's error 27 no such partion
</edit>

I found a solution by setting root(hd0,1).

I find this very wierd, and personally a bit scary... ¿Could I lose data?

Could any body gimme some pointers, links info? Is this suppose to behave like this?

Thanks in advance.

<edit>
Basicly, what is happening is that when the computer boots, and the bios passes control to grub, grub thinks that /dev/sda is hd0 (that's what I set in the boot sequence). After grub boots, during normal operation, grub, or what ever piece of software (kernel, etc), thinks that the /dev/sda is hd1. 

I truly don't understand why? 
</edit>

--Ale

---

### Post by tonym on 2005-06-24
I may be missing the point but you seem to have answered your own question.

During boot grub is given info about drives by BIOS.  As you have /dev/sda set as the boot device this is the first in the list and so is (hd0).  Once you have booted software uses /boot/grub/device.map (or whatever it is called ) to identify devices and there you have defined /dev/sda as (hd1).

---

### Post by alep on 2005-06-25
Thanks for your reply...

Yes, I'm answering my own question, but, I change my device.map

so I looks like this:
```

(hd1)   /dev/hda
(hd0)   /dev/sda

``` 

Yet it still doesn't work. I think I'll try map (hd1) (hd0)... and so on. Still I find the whole subject a bit wierd, and I don't know if it's because I have some wierd setting, or if its the way grub works in these SATA devices. In other words, I need someone to punch me in the face, and yell in a loud and angry voice, "Yes you! That's (not) the way is suppose to be".  :grin:

---

### Post by Fator dee on 2006-01-07
[QUOTE=alep]
Yet it still doesn't work. I think I'll try map (hd1) (hd0)... and so on. Still I find the whole subject a bit wierd, and I don't know if it's because I have some wierd setting, or if its the way grub works in these SATA devices. In other words, I need someone to punch me in the face, and yell in a loud and angry voice, "Yes you! That's (not) the way is suppose to be".  :grin:[/QUOTE]

Sorry to push up such an old thread, but I have a situation just like you. So have you found a solution to this problem?

---

