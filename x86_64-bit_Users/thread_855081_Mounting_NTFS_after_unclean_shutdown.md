---
title: "Mounting NTFS after unclean shutdown"
date: 2008-07-10
forum: x86 64-bit Users
---

### Post by Icarium on 2008-07-10
Well, hi, all, I'm new to the forum (obviously) and to Linux in general (which will become very apparent in just a few lines from now)

To get the story straight, my dad was messing around in the fuse box the other day, and ended up turning the circuit my computer was running on on and off several times. As Murphy dictates, of course my computer was not only plugged in, but grinding all gears, which came to an abrupt halt. After pulling the plug on it and letting it cool overnight, I tried booting it with no success whatsoever, this on a Windows XP system. After some despair, I decided to take the opportunity to toss the old and get something new in. I've been wanting to try Linux, and my choice fell on Ubuntu, as it seems like a pretty smooth transition from Windows.

The deal is that Windows got corrupted somehow due to the shutdown, and no longer functions. Being too lazy to take backups, I have a lot of personal files that I now need to rescue before I can wipe the drive clean. All of these are situated in two different physical harddrives, one of which is partitioned into halves, where one runs NTFS, and I assume the other FAT32, as it mounts without fuss. I have a third drive that also runs FAT32 that I can move the files to once I get access to them.

But it's never that simple, is it? Trying to mount the drives I need, I get an error message with the following key line: [I]
$LogFile indicates unclean shutdown (0, 1) Failed to mount '/dev/sda2': Operation not supported Mount denied because NTFS is marked to be in use.[/I]

Following the suggestion from the error message, I type the following into command:
*sudo mount -t ntfs-3g /dev/sda2 /media/OKW -o force*
which gives the following result:
$LogFile indicates unclean shutdown (0, 1)[I]
WARNING: Forced mount, reset $LogFile.
fuse: failed to access mountpoint /media/OKW: No such file or directory[/I]

Now, just doing that is more advanced than anything I've tried before - I'm way out of my league here. Any help on how to access my files for long enough to copy them would be greatly appreciated. For the record, the files in question is a number of digital photographs in *.jpg format, and the email directories from Thunderbird. Thanks in advance

EDIT: My sincerest apologies. Despite saying it couldn't mount, it seems that it did. Thus, feel free to delete this thread.

---

### Post by darkknight045 on 2008-07-10
Actually this could still be useful to someone who ran into your situation, so I'd say keep it up here.

Also for reference sake, What version of Ubuntu did you install?

---

### Post by Oracle_The_Blind on 2008-07-14
[FONT="Times New Roman"]Hi all.

I am having EXACTLY the same problem as described above.
Except that mine remains un-resolved.

I am running Ubuntu 8.04 LTS Desktop Edition.

Any help in accessing my old hard-drive would be very greatly appreciated.

Thanks

[/FONT]

---

### Post by ckuegel on 2008-07-20
I'm having this problem too but with a Maxtor 3200 external hard drive.

Any info would be Appriciated

---

### Post by phread59 on 2008-07-21
I'll take a whack at this one.  I bought a new Maxtor Onetouch 4 a while ago.  Hooked it up and could not get it to mount at all.  I got error messages saying Windows had an improper shut down.  I had to finally reinstall Windughs on an old drive in my machine.  I fired up Windughs and clicked on the new drive and ran the initialize proceedure and all is well.  I can access it just fine.  I'm sure you just need to open your drives with Windows and shut Windows down properly and all will be well.

BTW I have another Onetouch 4 that I had on my old Windows system.  It is attatched to the new Linux box and it has worked just fine from the get go.

As to fixing the Windows thing.  Just stuff the system disc in and reboot the machine (control-alt-delete) and it should repair the broken Windows installation.  Had to do that once when I got a corrupted bootloader.  Give the above a try and see what happens.

Mark Shuman

---

### Post by junglejuice on 2008-08-11
hi there
i'm also having the same problem as discribed above, can any one advise.
this is my situation
i have two harddrives one in ext3 with ubuntu the other NTFS. the NTFS drive does not mount properly. i used to have windoze XP working on that drive but the installation became corrupt and i decided to throw in the towel and switched over to ubuntu. i subsequently installed ubuntu 7.10 and was able to access my NTFS drive (read and write). this took a bit of configuration to set up properly, but i managed to get it working. only thing is that was about 6 months ago and i can't remember what i did to get it to work.
throughout the past couple of months that i've had ubuntu installed i've had absolutely no reason to switch back to windoze until recently i recieved a demo of an adobe cs3 production premium for windoze installation on DVD. having no luck with installing the software under ubuntu with wine. i decided to boot into my old windoze drive because throughout this whole period of about 6 months or so it remained on the grub boot loader screen. however thats when things started going horribly wrong. 
windoze seemed to boot correctly but then just blanked out and i couldn't get into it to shut it down. so i had to reset my computer manually. next time i tried to boot into ubuntu i could not see the NTFS drive (the one with windoze on it).
i subsequently installed ubuntu 8.04 hoping things might work out a bit better, but still i have the same problem. i can't see my NTFS drive and grub no longer shows the option to boot into windoze.
i don't really care about booting into windoze, infact i'd like to completely remove it from my system, but in order to do that i'd first need to see my NTFS drive mounted in ubuntu. 
can any one advise me on how to get my NTFS drive to show up in ubuntu again without having to format it?
any help is greatly appreciated.
thanks

---

### Post by cariboo on 2008-08-11
Use the what the os suggests, I had to use:

```
sudo mount -t ntfs-3g /dev/sdd1 /media/disk -o force
```

To mount one of my esata drives as I got tired of waiting for Vista to shut down and hit the reset button. Everything is as it should be on the drive that I force mounted.

As noted above linux will give you the command needed to mount your drive.

Note: this must be done in a terminal.

Jim

---

### Post by junglejuice on 2008-08-12
hi jim
the command i tried is
```
sudo mount -t ntfs-3g /dev/hda1 /media/Chubby -o force
```
my NTFS drive is IDE not SATA this is what ubuntu told me to try when it gave me the unclean shutdown message when i upgraded from 7.10 to 8.04
however the message i get in terminal when i try this is
```
ntfs-3g: Failed to access volume '/dev/hda1': No such file or directory
Please type '/sbin/mount.ntfs-3g --help' for more information.
```
so i try the help command but it's not really much help to me.
am i refering to my harddrive incorrectly and if so how do i find out what ubuntu refers to it as?
thanks for the help i do sincerely appreciate it :-)

---

### Post by jerome1232 on 2008-08-13
post the output of this command, it'll tell us what your hard drives are named so you can adjust the command
```
sudo fdisk -l
```

---

### Post by junglejuice on 2008-08-13
hi jerome1232
after running the command i get this
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd042a967

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19457   156288321    7  HPFS/NTFS

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x68dfeb9f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14380   115507318+  83  Linux
/dev/sdb2           14381       14946     4546395    5  Extended
/dev/sdb5           14381       14946     4546363+  82  Linux swap / Solaris

Disk /dev/sdc: 514 MB, 514849792 bytes
33 heads, 63 sectors/track, 483 cylinders
Units = cylinders of 2079 * 512 = 1064448 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         484      502767    b  W95 FAT32
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 1, 1) logical=(0, 0, 33)
Partition 1 has different physical/logical endings:
     phys=(242, 32, 63) logical=(483, 22, 23)
```
so i tried this variant of the command you mentioned earlier
```
sudo mount -t ntfs-3g /dev/sda1 /media/Chubby -o force
```
and i get this response
```
NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
```
so i try another variant
```
sudo mount -t ntfs-3g /dev/sda /media/Chubby -o force
```
and i get the same message with the exception of /dev/sda1 being /dev/sda
so i try yet another variant substituting /dev/sda with /dev/sdb and continue this pointless activity with /sdb1, then 2, then 5 the only one i didn't bother trying was sdc which i'm guessing is my USB memory stick.
i know my methods are rather crass and i apologize for subjecting you to that, but i just really would absolutely love to get my harddrive back with all the data on it intact.
thanks once again in advance

---

### Post by jerome1232 on 2008-08-13
ok I stumbled on this [http://www.mail-archive.com/ntfs-3g-devel@lists.sourceforge.net/msg00048.html](http://www.mail-archive.com/ntfs-3g-devel@lists.sourceforge.net/msg00048.html)

It seems to me these are the steps required (I haven't tested as I don't have a NTFS drive)

ntfsfix will clear the log file that indicates an unclean shutdown ntfsprogs provides a suite of utilties for working with ntfs

```
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sda1
sudo mount -t ntfs-3g /dev/sda1 /media/Chubby
```

apperantly mounting as readonly unmounting then remounting as read/write might solve this as well, man ntfs-3g has lots of good info on this

```
sudo mount -t ntfs-3g /dev/sda1 /media/Chubby -o ro
sudo umount /dev/sda1
sudo mount -t ntfs-3g /dev/sda1 /media/Chubby
```

---

### Post by junglejuice on 2008-08-14
hi
i already have ntfsprogs installed and already tried the commands you mentioned
```
sudo ntfsfix /dev/sda1
```
none the less i ran them again and got this message
```
Mounting volume... Failed to startup volume: Invalid argument.
FAILED
Attempting to correct errors... FAILED
Failed to startup volume: Invalid argument.
Volume is corrupt. You should run chkdsk.

```
what is chkdsk is that not the check disk utility that comes with windoze and has an ugly interface (kind of dos looking)? cause if that is what ubuntu is suggesting, it's not such a great suggestion to assume that i have a working installation of windoze on my computer cause i don't.
anywayz so i ran the other commands eventhough i wasn't really confident they were going to work, but who knows...
```
NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
```
is the message i got after running this command
```
 sudo mount -t ntfs-3g /dev/sda1 /media/Chubby
```
and this one
```
sudo mount -t ntfs-3g /dev/sda1 /media/Chubby -o ro
```
```
umount: /dev/sda1: not mounted
```
is the message i got after running this command
```
 sudo umount /dev/sda1
```
and once again i got the message
```
NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
```
after running the final command you mentioned, jerome1232
i seem to be going around in circles here. please could you advise me where to go from here.
thanks

---

### Post by jerome1232 on 2008-08-14
man, I'm out of suggestions here, looks like the disk is dutifully corrupted it's not just the standard log file unclean (as you did indicate earlier)

The first thing I would want to try is somehow get that drive into a computer with Windows and run chkdsk!

Now I know you said that's not possible so maybe try taking a look at things such as testdisk and dd, take note and be VERY careful these programs are powerful! I've heard of dd referred to as destroy disk because if you make a typo or use it wrong it can wipe disks out.

I'll look around see if there are some good links maybe somebody else better with data recovery can help you from here. Start researching testdisk/dd but don't screw with them unless you are sure what you are about to do isn't going to destroy everything.

---

### Post by junglejuice on 2008-08-15
hi jerome1232
i know what you mean, i will proceed with caution. i do hope that the disc is not corrupted. that would be rather unfortunate. none the less thanks very much for your help. it is greatly appreciated :-)
i'll continue to post here until i can find a solution to this problem.

---

### Post by junglejuice on 2008-08-16
i have had still no luck with getting my drive back. when i try to enable it through system settings this is the message i get
```
An error occurred while enabling /media/Chubby.
The system reported: NTFS signature is missing.
Failed to mount '/dev/sda': Invalid argument
The device '/dev/sda' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
```
and when i click details this is what i get
```
Return code from mount was 12.
"internal mount bug or missing nfs support in mount"
"user interrupt"
```
can anyone advise me what to do i have testdisk installed but i'm not sure how to use it?

---

### Post by jerome1232 on 2008-08-19
Hey I know this is kinda late but testdisk is very good, It comes with photorec this is what you want. 

It scans and recovers jpgs, giffs, mpegs (that would include mp3) txt and alot more.

Just run sudo photorec /d <place to put recovered files> and select the hard drive you want to recover watch it work it's magic.

(30 mins in and I've recovered 400 pictures from a drive I've formated AND reinstalled ubuntu 3 times on, I'm impressed)

Foremost is another data recovery program you might look at, I haven't ran it yet but I'm sure it's just as easy to use. It seems like it can recover even more types of files.

---

### Post by caljohnsmith on 2008-08-19
I hope you don't mind me jumping in, but I wanted to add emphasis to what Jerome1232 said earlier; I think you should run chkdsk on that Windows partition, junglejuice, before completely giving up on it. If you don't have a Windows Install CD you can use to run that program, can you borrow one from a friend? Or do you have a floppy drive? If you do, then you could make a DOS bootable floppy, and I could just send you that chkdsk program.

---

### Post by junglejuice on 2008-08-20
hi there
thanks for the comments and help.
hi jerome1232 it's not too late at all as i still have not fixed the problem as of yet. thanks for your suggestion about teskdisk recovery option i'll have a look at it as a last resort as i'd still like to keep data from my ntfs drive that is not of a standard multimedia format such as .mb (maya files) and .blend (blender files) amongst others.
as a backup in the mean time for atleast some of my data it's a great suggestion

back to the issue at hand it's been a while since i posted here because i ran testdisk but was obviously not cautious enough. testdisk kept telling me that the ntfs drive needs to be bootable even if it is not the drive i boot my os from. so i remember reading he mbr having something to do with booting and chose the option in testdisk to rewrite the mbr. this completely stopped me from booting into any os.
i managed to get an ubuntu liveCD and boot from it once there i was able to follow this thread
 [http://ubuntuforums.org/showthread.php?t=859101]("http://ubuntuforums.org/showthread.php?t=859101")
to rectify the problem so my os (ubuntu 8.04) is atleast up and running again! shew, as i was getting a bit worried there.

hi there caljohnsmith
don't mind you jumping in at all as anyhelp is appreciated, however un/fortunately i don't have access to a windoze computer at all. i'm sure booting under this os and running chkdsk will cretainly solve the problem, but like i said in my previous post my windoze installation is totally broken and i don't really wish to restore it (not that i have that option anyways). 

so i'm back where i was i can see the drive under system settings in kde 3.5.9
but it is marked as dissabled and when i go into administrator mode and try to enable it i get the error message as stated before
```
An error occurred while enabling /media/Chubby.
The system reported: NTFS signature is missing.
Failed to mount '/dev/sda': Invalid argument
The device '/dev/sda' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
```
are there any settings i can change under the modify option to fix this problem?
thanks again for the help
sincerely

---

### Post by caljohnsmith on 2008-08-20
> **junglejuice said:**
> 
```
An error occurred while enabling /media/Chubby.
The system reported: NTFS signature is missing.
Failed to mount '/dev/sda': Invalid argument
The device '/dev/sda' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
```

I've seen that exact error when the boot sector of the Windows partition gets corrupted. To fix the Windows boot sector (and not the MBR), you would need a Windows Install CD where you could run "fixboot" in the recovery console. Any way you can borrow a friend's Windows CD? 

If not I think your best bet is going with Jerome1232's suggestion and using "photorec", which given your circumstances will probably be able to recover almost all or at least most of your files. Herman's website has a short [guide of how to use photorec]("http://www.google.com/url?sa=t&ct=res&cd=1&url=http%3A%2F%2Fwww.users.bigpond.net.au%2Fhermanzone%2Fp21.html&ei=fh2sSPrZLILwsAPmtMzmDg&usg=AFQjCNGcHjQMwCtG2uSlI4hu49igNJT23w&sig2=033dS1pMGWKzv5d5-gzDMQ").

---

### Post by Jouke74 on 2008-08-20
Unfortunately, the best way to recover from a bad NTFS partition is to use Windows software. I suggest as well to make a bootable floppy and start from there. If you don't have a floppy use an XP CD and use recovery mode. Then run chkdsk. Make sure chkdsk is pointing to the right drive partition, because it does not like the fact that Ubuntu has altered the MBR. Note that when you run fixboot, you will probably loose your Grub, so make sure you have the Ubuntu CD as well to restore Grub afterwards. 

Read all messages of the programs carefully, because you may likely mess up more if things don't work out.

Otherwise look for data recovery tools like Sleuthkit. This can be useful as well when you have erased your USB stick or SD cards. Note that these tools require a good deal of knowledge so, if you have important data, try them out on something less important first! (like some dummy files on a USB stick)

---

### Post by junglejuice on 2008-08-20
thanks for the suggestions, but is it just not possible to fix this problem without using windoze? 
since i moved over to ubuntu i trashed my windoze xp disk! i found an old windoze me disk which i never installed (i won it in some competition years ago). will that work? can i use that cd to boot to a dos prompt and run chkdsk? if this is possible should i first dissconnect my linux disk (physically) so as to avoid windoze interfearing with it?
thanks for the help

---

### Post by jerome1232 on 2008-08-20
Although I'm more familiar with 98 than me :) it will have chkdsk, physically disconnecting the linux drive isn't a bad idea.

---

### Post by pdiddypaul on 2008-08-20
I have used the method in this [http://ubuntuforums.org/showthread.php?t=890452&highlight=unable+mount+ntfs]("http://ubuntuforums.org/showthread.php?t=890452&highlight=unable+mount+ntfs")
It worked for me when i cound not mount a working external hard drive formatted NTFS.  Look at post #6 for the exact details.
I was able to do this without using windows

---

### Post by junglejuice on 2008-08-21
hi pdiddypaul
thanks for the suggestion but i have already tried that, this is why i am currently exploring the chkdsk suggestion. as this is what ubuntu suggests i use to rectify the problem. not that i agree with the idea of having another os's tools to fix the problem, but it does seem to be a last measure situation at this point.

jjerome1232
i know that win me is fat32, the dirve i'm trying to mount is ntfs... are you certain (to some to some degree of a "reasonable" doubt) using chkdsk on the win me installation cd is a good idea?
thanks for your help

---

### Post by jerome1232 on 2008-08-21
Ok there is a reasonable doubt, I thought ME had ntfs support.

Here's a thought, if you have broadband, perhaps Bittorrent a good Windows XP iso, boot off of the cd and get into a recovery console, it has the command chkdsk, run it from there.  chkdsk has the syntax of chckdsk <drive> [/p] [/r]

/p does an exaushtive check
/r locates and recovers bad sectors, /p is implied with /r

edit: recovery console also has fixboot and fixmbr

---

### Post by junglejuice on 2008-08-21
hi
i don't know if i fully understand what you are suggesting, but it does not sound like the sort of thing i would do. thanks for the help thus far. but that is not an option for me.
i will have to resolve this matter in another way.

---

### Post by Yellow Pasque on 2008-08-21
> **junglejuice said:**
> thanks for the suggestions, but is it just not possible to fix this problem without using windoze? i found an old windoze me disk.

"NTFS? WTF?" - Windows Me 

My heart goes out to you, but once you are free of the Microsoft chains, it is glorious indeed.

---

### Post by jerome1232 on 2008-08-21
> **junglejuice said:**
> hi
i don't know if i fully understand what you are suggesting, but it does not sound like the sort of thing i would do. thanks for the help thus far. but that is not an option for me.
i will have to resolve this matter in another way.

I don't understand, I'm not in anyway saying pirate a copy of windows, I'm saying obtain a Windows XP cd just for the purpose of running chkdsk on your poor ntfs drive. If I thought it was illegal I wouldn't be posting it here. By all means if that IS illegal I'll remove that suggestion from my post. <waits for a mod to indicate so>

If you don't know someone willing to let you run chkdsk from their xp cd, The only options are torrent an iso, file carving your data out, which is messy and not perfect, or hiring a tech to bring his Windows cd over and run chkdsk on it/perform data recovery.

---

### Post by dalsoth on 2008-10-04
Hi guys, similar story.

I was using an Ubuntu live CD as my XP install was freezing on boot up even with safe mode, last known config etc and came across this post as i had the same error mounting my hdd in ubuntu. I literally had the exact same errors and reply messages as i tried everything the poster tried. 

I went back to the ubuntu places menu and tried my drive again and voila it let me access it. 

Not sure why but im glad to be able to backup my stuff before a reinstall and possibly a dual ubuntu boot :} thanks everyone. :KS :popcorn: :guitar:

---

### Post by junglejuice on 2008-10-05
hi dalsoth
thats great news to hear you got your drive working again :-) i still have not got ubuntu to recognise my ntfs drive after an unclean shutdown. i find it very interesting that ubuntu allowed you to access your drive after what sounds like a simmilar problem. 
where you eventually able to get windoze working and do a proper shutdown? as this i'm sure would have resolved the situation. i'd really appreciate knowing what you did just before the drive started working in ubuntu :-)
jj

---

### Post by gwenn on 2008-10-06
simple!
You must use a weindoze cd .Must go to the weindoze recovery console ,then shutdown the pc.When it starts again hit del then eject weindoz cd and insert ubuntu one.Restart and you just have a clean shutdown!

---

### Post by junglejuice on 2008-10-07
hi gwenn
yes indeed that is the simple way :-) amusing one has a windoze CD.. the problem is i need to have a clean shutdown without a windoze CD or even a working windoze installation.
but thanks for the reply anyway :-)
jj

---

### Post by Jerubaal on 2008-10-07
I have this problem, too. I need to get rid of C:\windows\system32\sptd.sys, but can't boot from my windows cd. I know the cd works, as I intalled from it in the first place.

Summary:
**sda **has several ext3 partitions for linux
**sdb **has several ntfs partitions for XP (one is My Documents, so linux can share it)
**hda **is fat32

XP is on /dev/sdb1 but won't mount for the same reasons as the original post.
The XP cd won't boot, even though it is first in the boot order in BIOS. 

It looks like I will have to unplug my sata drives and see if I can boot from CD with just my hda present. If so, I'll install XP on there, in order to chkdsk my sata drive.

Oh joy! Why don't I just bite the bullet and teach my wife Ubuntu?

---

### Post by gwenn on 2008-10-07
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

---

### Post by jerome1232 on 2008-10-07
Nice link, I've been thinking about calling hp and requesting installation media, I hate those god awful, half-useless recovery partitions that they've switched to.

---

### Post by gwenn on 2008-10-07
[http://www.download3000.com/download-xp-recovery-cd-maker-count-reg-17676.html](http://www.download3000.com/download-xp-recovery-cd-maker-count-reg-17676.html)
the second I'm not sure if is good...

---

### Post by gwenn on 2008-10-07
This is not the OS is just a recovery console...You can make some things but isn't quite powerful...

---

### Post by jerome1232 on 2008-10-07
It should have the chkdsk utility, along with things such as fixboot and fixmbr.

That's half the reason I want installation dvd's.

---

### Post by gwenn on 2008-10-07
I'm using it only for clean shutdown when... you know the vista story...

---

### Post by Joeb454 on 2008-10-07
What's wrong with ```
sudo ntfs-3g -o force /dev/sda* /mnt/NTFS
``` where "sda*" is the NTFS partition to mount, and "/mnt/NTFS" is the directory you want to mount it to.

I frequently use this when my brother has used my laptop and been too lazy to shutdown Windows. As yet - it's caused no ill effects whatsoever :)

---

### Post by smarks on 2008-10-07
I had that same problem with windows and unclean shutdown. Mine was cus of a virus but i eventually was able to luckly shutdown cleanly and then i transfered data from ntfs to ext3. I guess i got lucky

---

### Post by gwenn on 2008-10-07
force  Force the mounting even if the NTFS logfile is unclean. The log&#8208;
              file  will be unconditionally cleared. Use this option with cau&#8208;
              tion and for your own responsibility.

---

### Post by junglejuice on 2008-10-08
hi there joeb454
in gparted /dev/sdb1 is marked as extended under filesystem and /dev/sdb5 is listed as ntfs
when i run the command in terminal based on what gparted refers to these partitions as..
```
sudo ntfs-3g -o force /dev/sdb5 /mnt/NTFS
```
i get the following message
```
$MFT has invalid magic.
Failed to load $MFT: Input/output error
Failed to mount '/dev/sdb5': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.
```
when i try to mount the extended partition on the same physial drive 
```
sudo ntfs-3g -o force /dev/sdb1 /mnt/NTFS
```
i get the following message
```
NTFS signature is missing.
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
```
as can be expected. 
the problem is i no longer have a working windoze installation or a bootable windoze cd anymore, and since i live in south africa downloading a 120MB recovery iso is going to be costly for me as a home internet user.
...any suggestions would be greatly appreciated, as i have tried just about everything (certainly within my limited knowledge) and more!
jj

---

### Post by xjgnsdof on 2008-10-21
> **jerome1232 said:**
> ok I stumbled on this [http://www.mail-archive.com/ntfs-3g-devel@lists.sourceforge.net/msg00048.html](http://www.mail-archive.com/ntfs-3g-devel@lists.sourceforge.net/msg00048.html)

It seems to me these are the steps required (I haven't tested as I don't have a NTFS drive)

ntfsfix will clear the log file that indicates an unclean shutdown ntfsprogs provides a suite of utilties for working with ntfs

```
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sda1
sudo mount -t ntfs-3g /dev/sda1 /media/Chubby
```

apperantly mounting as readonly unmounting then remounting as read/write might solve this as well, man ntfs-3g has lots of good info on this

```
sudo mount -t ntfs-3g /dev/sda1 /media/Chubby -o ro
sudo umount /dev/sda1
sudo mount -t ntfs-3g /dev/sda1 /media/Chubby
```

Installing nftsprogs and running the two commands after it (though I had to input sdb1) worked for me where chkdsk didn't. Thanks a lot.

---

### Post by jerome1232 on 2008-10-21
> **Joeb454 said:**
> What's wrong with ```
sudo ntfs-3g -o force /dev/sda* /mnt/NTFS
``` where "sda*" is the NTFS partition to mount, and "/mnt/NTFS" is the directory you want to mount it to.

I frequently use this when my brother has used my laptop and been too lazy to shutdown Windows. As yet - it's caused no ill effects whatsoever :)

Nothing wrong with it per se but from my understanding (improved much since this thread has started) is that if there were things that needed to be replayed by the log/journal, it won't be done and you'll end up with an inconsistent file system.

Where as ntfsfix fixes a few common problems with nt files systems, resets the log and schedules the disk to have chkdsk run on it next time windows boots. So I just think ntfsfix is the better, more apt to work solution.

---

### Post by Jerubaal on 2008-10-24
I'm guessing the 'chkdsk' solution would have worked for me, had I been able to get chkdsk to see the sata drive.

Eventually I used a friends CD that had lots of different resuce tools on & "HDD Regeneration" did the same sort of thing as chkdsk.
I left it running over night & it repaired **513 bad sectors**!
XP now boots properly.

*The best thing about this experience is that my wife now wants to use Ubuntu instead of XP!*

---

### Post by junglejuice on 2008-10-24
hi there
a few months into the problem of not being able to get my ntfs drive to mount properly in ubuntu and i'd just about had. since i could not get a response that helped resolve the problem, but thanks for all the help sincerely to the community... i decided to throw in the towl and format the drive just so that i was not sitting with a useless drive that i COULD have used.
i used a command line tool called photorec to recover whatever data i could worked pretty well, turned up some garbage (like a quater of a million .txt files). but got most of my images, my .blend files, .fla files, .PSD files (not that i use photoshop anymore), and a whole bunch of random movie files from yesteryears. 
still quite a thorough little tool, apparently there are even better ones. unfortunately it was not able to recover any of my .mb files (maya binary files) or .obj (wavefront 3D object files), but at this point i'll pretty much just take whatever i can get.
so i basically did a recovery using photorec, salvaged what i can then proceeded to format the drive to EXT3. after a bit of trial and error, and this part i think was a bit unnecessary, i finaly figured out how to make the drive available for read and write for someone that is not root. why is there not a simple way of doing this, anyway? it took me at least several hours to figure it out, and i had to do it through KDE instead of GNOME which is what i usually use.
anyway so i got the drive back and now i've got a couple days worth of trying to sort through the million plus files photorec recovered...
wish me luck

---

### Post by jerome1232 on 2008-10-24
As for setting up permissions the gui way to do it under gnome is run nautilus as root, then change the permissions up.
Alt+F2, gksu nautilus, browse to your mount point, right click it, permissions tab, make it readable/writable by everybody or  give yourself ownership, click apply to enclosed files, close it, close nautilus, now you should be able to read and write as a normal user.

the cli way to do this is easier: Just change the mount point to the actual mount point.
```
# to change owner
sudo chown $USER:$USER /mnt/mountpoint
# to just give everybody read/write permission
sudo chmod 777 /mnt/mountpoint
```

---

### Post by werk on 2009-05-06
wow ! Thanks for all the help to all of you.Reading step by step worked somehow!
I extra registerd to the forum to say thanks ! ...___:)
Well then..ubuntu..

---

### Post by sandyd on 2009-08-24
i know this is an old thread, but in the future, this link
[http://www.freewarefiles.com/program_9_90_11100.html](http://www.freewarefiles.com/program_9_90_11100.html)
is to a boot disk taht contains chkdisk.

pretty usefull.

---

### Post by apb2390 on 2009-09-01
Old thread, useful info.

Maxtor one touch (don't know what model) worked perfectly after plugging into windoze, using "Safely remove hardware" (which in reality is really just unmounting it), and plugging it into Ubuntu 8.04 LTS.

---

