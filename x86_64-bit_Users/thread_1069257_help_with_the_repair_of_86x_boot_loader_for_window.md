---
title: "help with the repair of 86x boot loader for windows"
date: 2009-02-13
forum: x86 64-bit Users
---

### Post by nate11120 on 2009-02-13
Uh hello I am having like huge problems with Windows XP right now and well anyway i decided that ms sys was the right way to fix it since i do not have access to a windows XP cd i do however have access to a Ubuntu 8.04 boot disk well anyway i was using ms sys (i managed to get it)  and it says 
```
ubuntu@ubuntu:~$ sudo ms-sys -f /dev/sdd1
/dev/sdd1 has an x86 boot sector,
it is an unknown boot record
```
Like what is going on and how can i fix windows
every day i grow to hate windows more and more and more

---

### Post by caljohnsmith on 2009-02-13
So what exactly is wrong with Windows? Can you mount the partition and access it from your Ubuntu Live CD? How about posting the output of:
```
sudo mount /dev/sdd1 /mnt && ls -l /mnt
```

---

### Post by nate11120 on 2009-02-13
```
mount: special device /dev/sdd1 does not exist
```

I started running into problems when i tried out a new antivirus and i accidentally deleted or renamed some files that i should not have renamed some of them are either in the boot or sys 32. I got a new MBR and stuck it to what apears to be my windows partition but i got a CMOS screen with an MBR 123FA message

---

### Post by caljohnsmith on 2009-02-13
How about posting:
```
sudo fdisk -lu
```
And if you can, please identify which is the Windows partition.

---

### Post by nate11120 on 2009-02-13
```
Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8c718c71

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   234420479   117210208+   7  HPFS/NTFS

```

I think that the HPFS/NTFS partition is my windows partition but I am only running Ubuntu of of the boot disk

---

### Post by caljohnsmith on 2009-02-13
OK, how about posting:
```
sudo mount -t ntfs-3g -o force /dev/sdc1 /mnt && ls -l /mnt
```

---

### Post by nate11120 on 2009-02-13
```
Failed to mount '/dev/sdc1': Invalid argument
The device '/dev/sdc1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
```

what is the command that allows you to determine the outcome of all your partitions would you be able to determine the correct one from that

---

### Post by caljohnsmith on 2009-02-13
OK, how about first making sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk, choose "No log", choose the correct HDD and "Proceed", choose "Intel", choose "Advanced", select the Windows sdc1 partition, choose "Boot", then choose "Rebuild BS"; if testdisk gives you a warning that the "Extrapolated boot sector and current boot sector are different", then choose "Write". After you are done doing the "Rebuild BS" in testdisk, try again the command from my previous post and please post the output.

---

### Post by nate11120 on 2009-02-14
The testdisk utility says
```
Disk /dev/sdc - 120 GB / 111 GiB - CHS 14593 255 63
     Partition                  Start        End    Size in sectors
 1 * HPFS - NTFS              0   1  1 14591 254 63  234420417

filesystem size           234420417
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               14651276
clusters_per_mft_record   -10
clusters_per_index_record 1
Extrapolated boot sector and current boot sector are identical.

```
But when I typed in the command it still said 
```
NTFS signature is missing.
Failed to mount '/dev/sdc1': Invalid argument
The device '/dev/sdc1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
```
BTW is SUDO short for superuser? I am a Linux noob although i know a bit more about UNIX

---

### Post by nate11120 on 2009-02-14
HOLY CRAP, nvm my second part of last statement something new came up when i typed it again and some of it is green 
```
total 1603222
drwxrwxrwx 1 root root          0 2006-11-17 15:11 91d628459edd19914b1e
drwxrwxrwx 1 root root      16384 2009-01-28 23:13 a09e1b730300649713
drwxrwxrwx 1 root root      16384 2009-01-09 21:06 a18f63d117cd590cc7e4
-rwxrwxrwx 1 root root          0 2005-03-11 18:21 AUTOEXEC.BAT
drwxrwxrwx 1 root root      16384 2009-01-03 15:59 $AVG8.VAULT$
-rwxrwxrwx 1 root root    6154240 2005-04-04 19:56 avwinsfx.exe
drwxrwxrwx 1 root root          0 2007-04-11 20:26 Binaries
-rwxrwxrwx 1 root root        211 2006-02-10 16:52 BOOT.BKK
-rwxrwxrwx 1 root root        211 2006-02-10 16:52 boot.ini
drwxrwxrwx 1 root root      16384 2009-01-08 02:05 c0dbc54ae2f5f7a5fa
drwxrwxrwx 1 root root     385024 2009-01-24 23:52 Config.Msi
-rwxrwxrwx 1 root root          0 2005-03-11 18:21 CONFIG.SYS
-rwxrwxrwx 1 root root        230 2008-05-28 18:22 config.xml
-rwxrwxrwx 1 root root          0 2008-08-01 03:30 conmgr.log
-rwxrwxrwx 2 root root         22 2005-05-19 19:02 CRJ_AOM_Vol2Amend2.zip
drwxrwxrwx 1 root root       4096 2005-06-19 04:24 csscod
-rwxrwxrwx 2 root root        281 2005-04-10 13:35 debugInstaller.txt
-rwxrwxrwx 1 root root          8 2005-03-11 19:30 DFIMB.DAT
drwxrwxrwx 1 root root       4096 2008-11-27 19:53 Documents and Settings
drwxrwxrwx 1 root root       4096 2008-05-17 20:20 Downloads
-rwxrwxrwx 1 root root          0 2005-03-11 18:21 IO.SYS
-rwxrwxrwx 1 root root    7183768 2005-04-16 01:44 IP5_2Eng.exe
-rwxrwxrwx 2 root root    7639176 2005-04-16 01:23 ITP5_2Eng.exe
drwxrwxrwx 1 root root          0 2008-11-05 20:54 Logs
-rwxrwxrwx 1 root root         14 2006-02-02 00:01 movebody.txt
-rwxrwxrwx 1 root root          0 2005-03-11 18:21 MSDOS.SYS
drwxrwxrwx 1 root root          0 2007-04-11 20:26 MSSoap
drwxrwxrwx 1 root root          0 2006-12-18 18:58 MyWorks
drwxrwxrwx 1 root root          0 2008-06-10 01:01 Nexon
-rwxrwxrwx 1 root root        514 2008-08-01 03:30 NServer.log
-rwxrwxrwx 1 root root      47564 2004-08-04 01:07 NTDETECT.COM
-rwxrwxrwx 1 root root     250048 2008-11-27 13:20 ntldr
drwxrwxrwx 1 root root       4096 2005-04-04 19:45 OfficesXp
-rwxrwxrwx 1 root root    1065696 2005-03-11 19:35 p95v238.exe
-rwxrwxrwx 1 root root 1610612736 2009-01-24 23:16 pagefile.sys
-rwxrwxrwx 2 root root     102486 2008-08-31 18:14 playground.log
drwxrwxrwx 1 root root          0 2008-09-18 19:51 ProgramData
drwxrwxrwx 1 root root      32768 2009-01-23 19:34 Program Files
drwxrwxrwx 1 root root       4096 2009-01-23 03:01 Python26
drwxrwxrwx 1 root root       4096 2009-01-06 00:24 RECYCLER
-rwxrwxrwx 2 root root    6905704 2005-04-04 19:46 sdinstall.exe
-rwxrwxrwx 1 root root        168 2005-04-08 21:59 setupfax.log
-rwxrwxrwx 1 root root     304136 2008-01-02 14:53 SNPP106.RAW
-rwxrwxrwx 2 root root        268 2008-10-15 19:07 sqmdata00.sqm
-rwxrwxrwx 2 root root        268 2008-10-16 18:55 sqmdata01.sqm
-rwxrwxrwx 2 root root        268 2008-10-17 18:46 sqmdata02.sqm
-rwxrwxrwx 2 root root        268 2008-10-18 14:49 sqmdata03.sqm
-rwxrwxrwx 2 root root        268 2008-10-19 17:12 sqmdata04.sqm
-rwxrwxrwx 2 root root        268 2008-10-20 00:59 sqmdata05.sqm
-rwxrwxrwx 2 root root        268 2008-10-20 01:05 sqmdata06.sqm
-rwxrwxrwx 2 root root        268 2008-10-20 21:18 sqmdata07.sqm
-rwxrwxrwx 2 root root        268 2008-10-21 11:22 sqmdata08.sqm
-rwxrwxrwx 2 root root        268 2008-10-21 19:46 sqmdata09.sqm
-rwxrwxrwx 2 root root        268 2008-10-21 19:57 sqmdata10.sqm
-rwxrwxrwx 2 root root        268 2008-10-21 21:18 sqmdata11.sqm
-rwxrwxrwx 2 root root        268 2008-10-22 02:16 sqmdata12.sqm
-rwxrwxrwx 2 root root        268 2008-10-22 19:06 sqmdata13.sqm
-rwxrwxrwx 2 root root        268 2008-10-23 01:32 sqmdata14.sqm
-rwxrwxrwx 2 root root        268 2008-10-23 02:35 sqmdata15.sqm
-rwxrwxrwx 2 root root        268 2008-09-27 14:32 sqmdata16.sqm
-rwxrwxrwx 2 root root        268 2008-10-13 02:20 sqmdata17.sqm
-rwxrwxrwx 2 root root        268 2008-12-16 00:59 sqmdata18.sqm
-rwxrwxrwx 2 root root        268 2008-10-13 22:06 sqmdata19.sqm
-rwxrwxrwx 2 root root        244 2008-10-15 19:07 sqmnoopt00.sqm
-rwxrwxrwx 2 root root        244 2008-10-16 18:55 sqmnoopt01.sqm
-rwxrwxrwx 2 root root        244 2008-10-17 18:46 sqmnoopt02.sqm
-rwxrwxrwx 2 root root        244 2008-10-18 14:49 sqmnoopt03.sqm
-rwxrwxrwx 2 root root        244 2008-10-19 17:12 sqmnoopt04.sqm
-rwxrwxrwx 2 root root        244 2008-10-20 00:59 sqmnoopt05.sqm
-rwxrwxrwx 2 root root        244 2008-10-20 01:05 sqmnoopt06.sqm
-rwxrwxrwx 2 root root        244 2008-10-20 21:18 sqmnoopt07.sqm
-rwxrwxrwx 2 root root        244 2008-10-21 11:22 sqmnoopt08.sqm
-rwxrwxrwx 2 root root        244 2008-10-21 19:46 sqmnoopt09.sqm
-rwxrwxrwx 2 root root        244 2008-10-21 19:57 sqmnoopt10.sqm
-rwxrwxrwx 2 root root        244 2008-10-21 21:18 sqmnoopt11.sqm
-rwxrwxrwx 2 root root        244 2008-10-22 02:16 sqmnoopt12.sqm
-rwxrwxrwx 2 root root        244 2008-10-22 19:06 sqmnoopt13.sqm
-rwxrwxrwx 2 root root        244 2008-10-23 01:32 sqmnoopt14.sqm
-rwxrwxrwx 2 root root        244 2008-10-23 02:35 sqmnoopt15.sqm
-rwxrwxrwx 2 root root        244 2008-09-27 14:32 sqmnoopt16.sqm
-rwxrwxrwx 2 root root        244 2008-10-13 02:20 sqmnoopt17.sqm
-rwxrwxrwx 2 root root        244 2008-12-16 00:59 sqmnoopt18.sqm
-rwxrwxrwx 2 root root        244 2008-10-13 22:06 sqmnoopt19.sqm
drwxrwxrwx 1 root root       4096 2009-01-07 01:28 strawberry
-rwxrwxrwx 2 root root     700416 2005-10-31 15:56 StubInstaller.exe
drwxrwxrwx 1 root root       4096 2005-03-11 18:24 System Volume Information
drwxrwxrwx 1 root root          0 2008-05-25 15:25 temp
drwxrwxrwx 1 root root     167936 2009-01-22 01:50 WINDOWS
-rwxrwxrwx 1 root root         28 2006-03-23 13:57 wizard.txt
```

---

### Post by caljohnsmith on 2009-02-14
Great, you at least mounted the partition, so you can access all the files in the partition with:
```
nautilus /mnt &
```
And yes, sudo means execute the command as superuser. To see if we can more fully repair Windows, how about first unmounting the partition:
```
sudo umount /mnt
```
You'll need to make sure you don't have the nautilus browser open to that directory when you unmount it. Then how about repeating the testdisk procedure, but this time when you get to the "Boot" screen, select "Backup BS" if it will let you. Also repeat and choose "Repair MFT". Let me know the results, and also again mount the partition with the previous commands.

---

### Post by nate11120 on 2009-02-14
```
TestDisk 6.8, Data Recovery Utility, August 2007
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sdc - 120 GB / 111 GiB - CHS 14593 255 63
     Partition                  Start        End    Size in sectors
 1 * HPFS - NTFS              0   1  1 14591 254 63  234420417

Boot sector
Status: OK

Backup boot sector
Status: OK

Sectors are identical.

A valid NTFS Boot sector must be present in order to access
any data; even if the partition is not bootable.





[  Quit  ]  [  List  ]  [Rebuild BS][Repair MFT][  Dump  ]
                                   Check MFT

```

I think this means that my backup boot is okay

```
Check MFTSegmentation fault
```

I think all the rest have returned teh same do you think it is safe to try to boot up windows now, eh btw thanks man i owe u

---

### Post by caljohnsmith on 2009-02-14
Before you try to boot Windows yet, I would recommend booting your Windows Install CD, go to the "recovery console" and run:
```
chkdsk /r
```
And run it as many times as it takes until it reports no errors. Then try booting Windows and let me know how it goes.

---

### Post by nate11120 on 2009-02-14
uhmm man thats my biggest problem 
I do not have my windows disk like i mean i don't have pirated windows or anything cuz i do not like to deprive programmers of money even if they work for Microsoft. Well anyway we had our computer custom made and it did not come with a disk! although all the updates have worked till now. COuld i get a disk off of one of my friends?

---

### Post by caljohnsmith on 2009-02-14
Before I forget to ask, what did you do in testdisk to cause the "Check MFTSegmentation fault" error? Did you try using the "repair MFT" option? If so, what happened? Since you don't have a Windows Install CD, you can instead download and use a Windows Repair CD from [here]("http://www.webtree.ca/windowsxp/tools/bootdiscs/xp_rec_con.zip"). Let me know how that goes.

---

### Post by nate11120 on 2009-02-14
when i hit enter on repair mft it made a beeping sound and then gave me that message so do i write the chkdsk image top a disk. Eh could i yank out the disk drive from my old cpu and attach it to my new one so i can run 2 disks at once because one of them is being used for ubuntu and i need to burn something on the new one?

---

### Post by caljohnsmith on 2009-02-14
Yes, you will need to burn that Windows Repair ISO file to a CD. But before you do that, how about trying to boot Windows and let me know how far you get.

---

### Post by nate11120 on 2009-02-14
ok

---

### Post by nate11120 on 2009-02-14
yeah that was what happened when i booted from windows.
Uhmm if i get my boot to work i should get the windows xp loading screen right or will that only come with uncorrupted system files

---

### Post by caljohnsmith on 2009-02-14
Once you get some sort of Windows CD, I think it would be a good idea to also run:
```
fixmbr 
fixboot
```
In addition to the chkdsk. And yes, you probably won't get as far as the Windows splash screen if Windows has corrupted files.

---

### Post by nate11120 on 2009-02-24
John I am still having trouble my friend lent me a disk which supposedly had chkdsk on it, it worked the first time but now when i put it in and boot from it says press any key to boot from disk and when i press a key it just takes out the word press and goes into the ... sequence. Is there a way of doing a scan of teh windows disk from Ubuntu

---

### Post by caljohnsmith on 2009-02-24
> **nate11120 said:**
>  Is there a way of doing a scan of teh windows disk from Ubuntu
To my knowledge there is no equivalent of "chkdsk" in linux. You'll need to get the Windows CD booting in order to use chkdsk.

---

### Post by shadowhacker on 2009-02-25
> **nate11120 said:**
> John I am still having trouble my friend lent me a disk which supposedly had chkdsk on it, it worked the first time but now when i put it in and boot from it says press any key to boot from disk and when i press a key it just takes out the word press and goes into the ... sequence. Is there a way of doing a scan of teh windows disk from Ubuntu

Are you by chance using a USB keyboard? If so to make the Windows XP CD recognize your keystroke you need to enable legacy USB support in your system's CMOS (BIOS) settings.

---

### Post by nate11120 on 2009-02-26
I  got the disk running what do i do now? i do not know how to use one of these when i opened it up and selected the windows partition and selected the no changes thing it brought me to an install screen god do i ever hate windows

---

### Post by caljohnsmith on 2009-02-27
> **nate11120 said:**
> I  got the disk running what do i do now? i do not know how to use one of these when i opened it up and selected the windows partition and selected the no changes thing it brought me to an install screen god do i ever hate windows
When you boot the CD, at the first main menu press "r" to get the recovery console. From there you should be able to run "chkdsk".

---

### Post by nate11120 on 2009-02-27
ok ty John I will tell you how it goes

---

### Post by nate11120 on 2009-02-28
I cannot access the recovery council when i load from the disk of of the MBR it goes to a blue screen that says windows is loading and then it gives me an install option for drivers f6 and an automated recovery process f2 which i need a cd for after that it directs me to a partition page and I swear i pressed r for the whole time

---

### Post by nate11120 on 2009-03-02
Sory about that, I got teh isk to run the recovery consul using f10 and then well i ran chkdsk a few times and then when i reboot my computer low and behold theres a windows vista chkdsk thing and i would no touch vista with a ten foot pole aparently the disk i have is service pack three and when i tried to run chkdsk again i got this weird thing with three diferent ve3rsions of the windows c drive to try to login as

---

### Post by Michelangelo1973 on 2009-03-03
No, sudo is just a command to "act as" superuser for the command running or for the session open try sudo -i for as long as you have the terminal open if you are going to run several commands and don't want to be typing your PWD forever
I'm A newbie too But have to learn to survive L:O:L

---

### Post by nate11120 on 2009-03-03
I was always told that it was similar to the root comand in Unix?

---

