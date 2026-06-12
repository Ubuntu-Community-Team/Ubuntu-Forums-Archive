---
title: "just installed wont let me boot up"
date: 2008-11-08
forum: x86 64-bit Users
---

### Post by psyon27 on 2008-11-08
I just installed the latest ubuntu 64-bit. I am dual booting vista and ubuntu. When I start my comp it won't let me choose which OS to boot into it just automatically boots into vista. please help

---

### Post by tvtech on 2008-11-08
okay, so the question being did grub get installed? it doesn't sound like it. is it still booting as though you had not installed anything at all?

---

### Post by psyon27 on 2008-11-08
Yes it boots up as if nothing happened. I tried easybcd to add ubuntu to my MBR but I just get errors when I try to boot into ubuntu. I just booted into ubuntu using the cd and it can see files on the harddrive its installed onto. Should i try to reinstall ubuntu?

---

### Post by cyfur01 on 2008-11-08
You could manually install grub, which is what the Ubuntu installer normally does by default. [This website]("http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm?page=6") gives a general overview of how to do this, although the parameters may change depending on where you set everything up (partition-wise). To see a list of partitions and a little bit of information, you can use "fdisk -l".

An alternative to this, if you haven't configured much with Ubuntu, is to just re-install it and make sure at the end to install grub.

---

### Post by psyon27 on 2008-11-08
Well somehow when I exited from ubuntu that I booted from the CD it didn't restart my comp it just went right back to the menu from the CD. So I went to the option to boot to first hard disk and it booted into ubuntu that is installed on my hard drive. So it works, it even said loading grub. Then booted up. Although I can't figure out how to see how much hard drive space is on the drive through ubuntu. It does see my external drive and my CD drives.

---

### Post by caljohnsmith on 2008-11-08
How about when you are in Ubuntu, open a terminal with Applications > Accessories > Terminal, and post the output of:
sudo fdisk -lu
Also, for each of the drives fdisk lists, like sda, sdb, etc, please post the output of:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
```
So replace "sda" above with each of your drives. And finally, for each command above that returns "GRUB", please post:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] bs=1 skip=1049 count=2 2>/dev/null | hexdump
```
And replace sda with the drives that previously returned "GRUB". That will greatly clarify what your setup is like.

---

### Post by psyon27 on 2008-11-08
Ok here is the output of the sudo fdisk -lu

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000dc77a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63  1941471314   970735626   83  Linux
/dev/sda2      1941471315  1953520064     6024375    5  Extended
/dev/sda5      1941471378  1953520064     6024343+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd1d4e142

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   976791535   488394744    7  HPFS/NTFS

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00006824

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63   488392064   244196001    c  W95 FAT32 (LBA)


The way i have my drives set up I have 2 250gb drives striped with vista on them, they are in sata ports 1 and 2. I also have a 1TB drive in sata port 3. That last drive is an external. 

sda returned with grub
sdb returned with missing operating system

sda returned with
0000000 ff00                                   
0000002

None of the other drives returned with anything.

---

### Post by caljohnsmith on 2008-11-08
OK, it appears Grub was correctly installed to the MBR (Master Boot Record) of the sda Ubuntu drive, so if you are booting Vista on start up, that means most likely all you have to do is just go into your BIOS and switch the boot order so that sda is first. Once you set your BIOS to boot sda, you should get the Grub menu. Let me know how it goes.

---

### Post by psyon27 on 2008-11-08
That worked. Thanks a bunch!!

---

### Post by psyon27 on 2008-11-08
New problem. so grub comes up and it doesn't list vista at all. What I did was follow this other site's instructions on adding vista to the list.

To enter the GRUB configuration mode, type in "sudo grub" and press Enter. Then type in the following commands in sequence:
- root (hd0,0)
- setup (hd0)
- quit
- exit 

Reboot the system. You'll get the GRUB bootloader but Vista won't be an option - we need to add this to the boot options.

Boot into Ubuntu and open up another Terminal session. Then, type in sudo gedit /boot/grub/menu.lst

Scroll down to the bottom of the file and type in the following text strings:

title Windows Vista
root (hd0,1)
makeactive
chainloader +1 

However, now it gives me an error 22 when I try to boot vista. I think its b/c I have the drives that vista is on striped. so where it says root (hd0,1) I should put what hard drive and partition vista is on but since it is striped I don't know what to put there.

---

### Post by psyon27 on 2008-11-08
I figure Until I get this sorted out I can just keep going into my BIOS and messing with boot priority. Temporary fix that I'm about to try. I really appreciate all your help!

---

### Post by psyon27 on 2008-11-08
Well that worked as a ghetto way of choosing my OS hah. It didn't ruin my RAID or anything they are still synced and healthy.

---

### Post by caljohnsmith on 2008-11-09
Booting Vista from a RAID setup with Grub could be a problem, but hopefully it will work for you. How about first opening your menu.lst with:
```
gksudo gedit /boot/grub/menu.lst
```
And then at the bottom add:
```
title	   Windows Vista (hd1)
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title	   Windows Vista (hd2)
root       (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1

title	   Windows Vista (hd3)
root       (hd3,0)
map        (hd0) (hd3)
map        (hd3) (hd0)
chainloader +1
```
Give that a shot, and if none of those entries work to boot Vista, let me know exactly what happens when you select each one from the Grub menu and we can work from there. :)

---

### Post by psyon27 on 2008-11-09
Oh sweet nectar!! The first one worked. Thanks so much!

---

### Post by caljohnsmith on 2008-11-09
That's great news, I'm glad booting Vista didn't turn out to be a problem with your RAID setup. Cheers and have fun. :)

---

