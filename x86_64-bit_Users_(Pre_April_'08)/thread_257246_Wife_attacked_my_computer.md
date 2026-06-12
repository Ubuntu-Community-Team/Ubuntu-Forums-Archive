---
title: "Wife attacked my computer"
date: 2006-09-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by morequarky on 2006-09-14
My families computer has Ubuntu64 running almost all the time.  Recently my wife's laptop got formated do to a husband, namely me, who was trying to fix some viruses.

Now my wife is booting into WindowsXP64 on my computer.  XP64 doesn't have flash and some websites she wanted forced the use of 32bit windows.  She installed XP Home 32bit along side(in the same partition) as XP64.

All well and good.

Except she wrote over my MBR.  Now I can't access my Ubuntu :(

I followed the directions on this thread [http://ubuntuforums.org/showthread.php?t=256246&highlight=grub+install]("http://ubuntuforums.org/showthread.php?t=256246&highlight=grub+install")

The Master Boot Record is back and working great...my problem is I somehow set grub up wrong.

I installed everything on ext3 partitions, but my kernel boots and says something about filesystems couldn't load ext2fx and crashes to a prompt and bash doesn't work.  Another strange thing.  Gparted doesn't show anything on my harddrive at all.  It always did before.  Must be because of some grub issue.

Please ask me some questions and I will clearify where needed.

HELP PLEASE.

Thanks bunches.

---

### Post by morequarky on 2006-09-14
My fdisk -lu looks like this

Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63    12289724     6144831    7  HPFS/NTFS
/dev/hda2        12289725    14249654      979965   83  Linux
/dev/hda3        14249655   156360644    71055495    5  Extended
/dev/hda4       138191193   156360644     9084726    b  W95 FAT32
/dev/hda5        14249781    16209584      979902   83  Linux
/dev/hda6        16209648    35744624     9767488+  83  Linux
/dev/hda7        35744688    55279664     9767488+  83  Linux
/dev/hda8        55279728    59183459     1951866   82  Linux swap/Solaris
/dev/hda9        59183523    98253539    19535008+  83  Linux
/dev/hda10       98253603   138191129    19968763+  83  Linux

---

### Post by Kilz on 2006-09-14
> **morequarky said:**
> My fdisk -lu looks like this

Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63    12289724     6144831    7  HPFS/NTFS
/dev/hda2        12289725    14249654      979965   83  Linux
/dev/hda3        14249655   156360644    71055495    5  Extended
/dev/hda4       138191193   156360644     9084726    b  W95 FAT32
/dev/hda5        14249781    16209584      979902   83  Linux
/dev/hda6        16209648    35744624     9767488+  83  Linux
/dev/hda7        35744688    55279664     9767488+  83  Linux
/dev/hda8        55279728    59183459     1951866   82  Linux swap/Solaris
/dev/hda9        59183523    98253539    19535008+  83  Linux
/dev/hda10       98253603   138191129    19968763+  83  Linux
Welcome to the Linux users who's wife "must" use Windows support group. \\:D/  Mine has her own pc on my home network. Last time a virus got it(what in this world made you clikck on that email attachment?), I handed her the resore disk. :D  It was worth the 3 days of her being a pain to teach the "windows is garbage lesson" Since I dont have any windows on my PC she is sol as she "wont use that Linux stuff, its to confusing"
But back to the problem. Looks like you have more than one linux install. This may make this harder. Have you tried poping the Ubuntu cd in and selecting rescue a installed system, letting it run untill it comes to a screen that offers "reinstall Grub" in the menu and let it install it to the mbr?

---

### Post by morequarky on 2006-09-15
Kilz thanks for the response.

My original post was written in haste as will this message.

I tried what you suggested and that doesn't fix my problem.

I followed the howto listed in the first post.  Grub has been reinstalled. Grub works as told.  It ask me if I want to run linux and which kernel even.  If I choose windows it gives me the options to run WinXP home or WinXP64.  All great.

Now let me explain where my problem lies.

When I choose a linux kernel to boot, Ubuntu attempts to load. ALL THE ext3(or ext2fx) PARTITIONS YOU SEE ARE SEPARATE PARTS OF THE LINUX FILESYSTEM.  AKA one partition is for /home and another for /var.

The linux kernel crashes when it tries to "load filesystems".  The linux kernel is not properly mounting the needed partitions.

HELP!!!

---

### Post by MetalMusicAddict on 2006-09-15
> **Kilz said:**
> Welcome to the Linux users who's wife "must" use Windows support group.
That almost made me spit what I was drinking. :) I *MADE* my wife switch on her PC. She doesnt do anything that needs windows so I just did it. No questions asked. She bitched for a bit but she got over it and seems to get along fine now. :)

---

### Post by onlyoneskwalla on 2006-09-15
Quick question. Do you use a separate partition for /boot? Could you open your /boot/grub/menu.lst and post it for closer inspection, and also give me a blow by blow of exactly what each /dev/hda partiton is, so i can tell you what to edit your menu.lst to.

---

### Post by morequarky on 2006-09-15
thanks onlyoneskwalla for your help.  sorry for my delayed response, i am really busy these days.

I don't know how to open "/boot/grub/menu.lst" from my dapper liveCD.

I can mount each partition with my liveCD.  I am not sure how to recognize which partition is which, but I will try.

thanks again

---

### Post by Maylar on 2006-09-15
looks like hda1 is flagged as the bootable partition. The way I would mount the partitions is to

cd /mnt

and do alot of

mkdir par1
mkdir par2

and so on. once you have those done. then do 

sudo mount /dev/hda2 /mnt/par1

cd /mnt/par1
ls

this will show you what is in that partition.

you wont have to worry about the new directories in /mnt as they are in the livecd enviroment. once you reboot out of it, they will not be on your system.

hope that was helpful

---

### Post by morequarky on 2006-09-16
ok.  I tried posting this before, but had trouble.

hda1 is NTFS
hda4 is FAT32 misc files
hda2 is / (I do not have a separate boot partition)
hda5 AND hda10 are unknown to me and hold nothing but a "lost+found" file.
hda10 is 18gigs and I wonder if it is 'extended' for logical partitions.
hda6 is surely /usr
hda7 is /var
hda9 is /home

---

### Post by morequarky on 2006-09-16
First let me say that my wife goes to Korean banking websites and a few others that don't work in firefox.

My wife also surfs the web with abandon, meaning she invites viruses like a bee seeks honey.

My wife bought a Mac a while back due to the hatred for viruses.  She quit using it because of two reasons. First reason is she couldn't get into those banking websites and the second reason is that i deleted what I thought was a "link" but turned out to be part of the system utilities which caused the computer to run slow.  I tried re-installing but didn't have the CD's I needed.

My wife now has a XP laptop.  Breezy didn't have the wifi drivers for it.  Dapper does.  Anyway, she bought it used and with no backup CD.  So I formated it last week because of all the viruses she had collected.  Well, I think she only had a couple viruses but all the adware was slowing the computer down and driver her crazy.  She tried installing XP Home on it, but couldn't get the wifi to work.  I don't even know off the top of my head how to do get the wifi to work.  So...she installed XP home edition on my desktop inside the XP64 partition wiping my MBR.

I have reinstalled grub on the MBR, but again the kernel fails because it doesn't know to mount the other partitions.

FYI: I THINK you would be hard pressed to find a 32bit processor being sold in Korea.  But only a select few install XP64 on it.  I would say that 99% of the processors sold in Korea are 64bit, but only 1% have 64bitXP.

---

### Post by _simon_ on 2006-09-16
If it was me in this situation I would get the wifi working on the laptop so that you can get your wife back on that. I know what it's like having a partner pestering you or trying to take over your pc! ;)

Then I would start from scratch on the desktop, format all partitions and reinstall Dapper.

---

### Post by morequarky on 2006-09-16
I have too much information on the Linux partitions to do that.  I also don't want to and don't have the time to reinstall apache and the like.

There has got to be a way to fix this that doesn't take weeks.  Someone has to know how to modify one lousy file verses reinstalling and losing everything.  Yes lose... I don't have any external harddrive laying around to back up this kind of stuff.

---

### Post by Kilz on 2006-09-16
> **morequarky said:**
> I have reinstalled grub on the MBR, but again the kernel fails because it doesn't know to mount the other partitions.

The mounting is done by your fstab file, not grub. If you havent messed with it, it should still be working. What is the exact error message you are getting now.
If in the end you have to reinstall you may not lose much. Having all the extra partitions means you will only have to replace the / root install then edit the fstab file to tell the install what partitions to load into the file system.

---

### Post by morequarky on 2006-09-16
Ok, sure.  I wouldn't have to format /home or /var, just the other partitions.

I am guessing the problem is that my wife formated hda5 and hda10 messing up my install.  I'll have to re-install leaving /var /home and /usr alone.  I don't remember what hda5 and hda10 were.  Maybe hda10 is like the extended partition for the other logical drives.

After loading the linux kernel it gets to a point where it loads "filesysterms" and just crashes out.  Probably because there is nothing in hda5 and hda10.

Is there some special command to re-install only part of the OS?

---

### Post by Kilz on 2006-09-16
> **morequarky said:**
> Ok, sure.  I wouldn't have to format /home or /var, just the other partitions.

I am guessing the problem is that my wife formated hda5 and hda10 messing up my install.  I'll have to re-install leaving /var /home and /usr alone.  I don't remember what hda5 and hda10 were.  Maybe hda10 is like the extended partition for the other logical drives.

After loading the linux kernel it gets to a point where it loads "filesysterms" and just crashes out.  Probably because there is nothing in hda5 and hda10.

Is there some special command to re-install only part of the OS?

Not that I know of. I only know that its possible to do it, not how its done.

---

### Post by juicemansam on 2006-09-19
I'd try this: [LIST=1]
[*]Find the partition with grub/menu.lst and the stage{1,2} files.
[*]Grab a floppy disk (that's if you have a floppy drive, which is iffy with new PC's) and ```
dd if=stage1 of=/dev/fd0 bs=512 count=1
dd if=stage2 of=/dev/fd0 bs=512 seek=1
```, and boot to the floppy.
[*]Remembering which partition the grub files where found, in the grub command prompt enter ```
grub> root (hd0,1)
```, taking into consideration the grub naming standard. That will set the root partition for grub to look for it's files. And from what you've stated, the correct partition would be hd0,1.
[*]Then enter ```
grub> setup (hd0)
```. That will read the grub files and install itself into the MBR of hd0. 
[/LIST]
I know I'm not really clear on the steps, but it should be roughly similar. Also, you could always reinstall Window's MBR with install CD should the system become unbootable. Good luck!

---

