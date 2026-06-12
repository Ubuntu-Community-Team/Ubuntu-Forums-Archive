---
title: "Ubuntu 8.10 instalation help needed"
date: 2009-03-01
forum: x86 64-bit Users
---

### Post by mahsoud on 2009-03-01
- please help :(

- im trying to install, or at least run ubuntu on this laptop, so what i did poped in liveCD, first runned off the live CD, and live was beautiful, then i installed ubutu ... and after restart laptop warned me that no valid operating system is found :(

i poped in the liveCD again... this time it gave me option to install or run ubuntu off the CD... i tried both.... in both cases i end up at fallowing screen:

Loading, please wait...
Linux ubuntu 2.6.27-7-generic #1 SMP Fri Oct 24 06:40:41 UTC 2008 x86_64
The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by applicable law.

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$




... if i type "sudo fdisk -l" i get this:






Disk /dev/sda (sun disk label): 255 heads, 63 sectors, 24321 cylinders
units=cylinders of 16065*512 bytes

Device    Flag  Start   End     Blocks    ID    System
/dev/sda1           0  24315  195310237+  83    Linux native
/dev/sda2   u   24315  24321       48195  82    Linux swap
/dev/sda3           0  24321  195358432+   5    Whole disk

ubuntu@ubuntu:~$



... plaese help :(

---

### Post by mahsoud on 2009-03-01
- please help, i posted it in main instalationg forum... but then noticed that there is this one... 

- im trying to install, or at least run ubuntu on this laptop, so what i did poped in liveCD, first runned off the live CD, and live was beautiful, then i installed ubutu ... and after restart laptop warned me that no valid operating system is found 

i poped in the liveCD again... this time it gave me option to install or run ubuntu off the CD... i tried both.... in both cases i end up at fallowing screen:

Loading, please wait...
Linux ubuntu 2.6.27-7-generic #1 SMP Fri Oct 24 06:40:41 UTC 2008 x86_64
The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by applicable law.

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$




... if i type "sudo fdisk -l" i get this:






Disk /dev/sda (sun disk label): 255 heads, 63 sectors, 24321 cylinders
units=cylinders of 16065*512 bytes

Device Flag Start End Blocks ID System
/dev/sda1 0 24315 195310237+ 83 Linux native
/dev/sda2 u 24315 24321 48195 82 Linux swap
/dev/sda3 0 24321 195358432+ 5 Whole disk

ubuntu@ubuntu:~$



... plaese help

---

### Post by Reeman on 2009-03-01
> **mahsoud said:**
> - please help :(

- im trying to install, or at least run ubuntu on this laptop, so what i did poped in liveCD, first runned off the live CD, and live was beautiful, then i installed ubutu ... and after restart laptop warned me that no valid operating system is found :(

i poped in the liveCD again... this time it gave me option to install or run ubuntu off the CD... i tried both.... in both cases i end up at fallowing screen:

Loading, please wait...
Linux ubuntu 2.6.27-7-generic #1 SMP Fri Oct 24 06:40:41 UTC 2008 x86_64
The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by applicable law.

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$




... if i type "sudo fdisk -l" i get this:






Disk /dev/sda (sun disk label): 255 heads, 63 sectors, 24321 cylinders
units=cylinders of 16065*512 bytes

Device    Flag  Start   End     Blocks    ID    System
/dev/sda1           0  24315  195310237+  83    Linux native
/dev/sda2   u   24315  24321       48195  82    Linux swap
/dev/sda3           0  24321  195358432+   5    Whole disk

ubuntu@ubuntu:~$



... plaese help :(

Your laptop most likely has a backup windows partition or a restore CD that came with the laptop. 

From what I am reading you did a complete install but for some reason grub botched up the boot loader. See if you can stick in the live cd then use the option "boot from harddrive" This might get you to the Ubuntu login that you created. Sounds like the install did not complete. 

If you boot into the live cd you can see if there are other partitions available and what exactly is on your harddrive. If you intended to do a dual boot with another OS you might still see the a windows partition. 

If you chose the option use entire disk then there might be no windows partition at all left to use. If you do not have a windows restore partition on the disk or a restore CD then there will be no way to get windows back if all partitions were erased during the initial phase of the Ubuntu installation.

If you do a re-install of Ubuntu make sure everything completes especially the final install of grub. You might have to enter the partition software and manually partition... it is not that hard. Auto partitioning should also work and if there is another operating system present the install will find it and adjust the boot loader so that you can select it if you wish.

Here is a cfdisk of my partition layout. The reason I have a fat32 is that I sync the partition with windows machines with samba to transfer audio files that I record. I custom partition my drives to the maximum of 4 primary partitions and use no logical partitions on my Ubuntu Studio machine. If I chose to change the fat32 to ntfs and install windows later then it is relatively simple to fix grub to do a dual boot. Windows does not like to be installed to a logical drive within a primary partition! It is possible but can be a pita unless you install windows to a primary partition.

Sounds like you used your entire drive and you have no windows partitions visible to fdisk. However if there is still other partitions they might show up running the live cd or during an Ubuntu reinstall.

---

### Post by mahsoud on 2009-03-01
Dont have back up CD anymore :(

I did do a complete install, it gave me option to keep windows patiotion but i choose to use whole hard drive for ubuntu... ( didnt think i'd use windows on laptop again )

option "boot from harddrive", makes the laptop freez at "booting from local disk..."

the problem is that i cant even boot to live cd now :(



maybe i should try one of those superboot cds?

---

### Post by 3Miro on 2009-03-01
> **mahsoud said:**
> Dont have back up CD anymore :(

I did do a complete install, it gave me option to keep windows patiotion but i choose to use whole hard drive for ubuntu... ( didnt think i'd use windows on laptop again )

option "boot from harddrive", makes the laptop freez at "booting from local disk..."

the problem is that i cant even boot to live cd now :(



maybe i should try one of those superboot cds?

If you were able to boot from the LiveCD before and not now, you might have a hardware issue (i.e. dead hard drive).

Can you enter the BIOS set up?

---

### Post by mahsoud on 2009-03-01
ok.. so far what i did is used hiren's BootCD, to delete partion table and created a new partition... 

liveCD loaded (yay!)

went through instal... and back to the same thing :(


.. yeah bios is accessble :confused: i guess... 

installation effed up my harddrive partitioning...  any advice?



Also, it doesnt matter if I use 64bit or 32bit version, both give me same result:

after install if i boot from lifeCD i get 

ubuntu@ubuntu:~$

but if boot from hard drive... i get 

my_username@my_computer_name:~$



if i use bootcd, format/repartition harddrive... liveCD work... but cant install....

????????????????????????

---

### Post by mahsoud on 2009-03-02
any ideas?

---

### Post by Ian222 on 2009-03-18
I have the same problem; I tried installing Ubuntu on a Vista box, and I thought the boot loader was screwed up. 

I ended up buying a new hard drive, installed Vista and tried again. Now, when I try to install Ubuntu it gives me the same error you mentioned. Most frustrating.

---

