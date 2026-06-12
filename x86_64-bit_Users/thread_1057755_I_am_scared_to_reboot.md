---
title: "I am scared to reboot"
date: 2009-02-02
forum: x86 64-bit Users
---

### Post by tyk on 2009-02-02
I have 
Intel Q6600 with 2GB RAM
ATI Radeon graphic card (well set up)
A psycho kind of filesystem:
```
swastik@eco:~$ mount
/dev/sdb4 on / type reiserfs (rw,relatime)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-23-generic/volatile type tmpfs (rw)
/dev/sdb2 on /boot type reiserfs (rw,relatime,notail)
/dev/sdb7 on /home type reiserfs (rw,relatime)
/dev/sdc3 on /media/Four type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sdc7 on /media/One type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sdc6 on /media/Two type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sdc5 on /media/Work type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sdb6 on /media/Three type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sdb5 on /media/Archive type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sdc1 on /media/vmware type reiserfs (rw,relatime)
/dev/sda2 on /media/Personal type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sda1 on /media/Five type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sda5 on /media/Six type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sda6 on /media/Seven type reiserfs (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
none on /proc/fs/vmblock/mountPoint type vmblock (rw)
```
```
swastik@eco:~$ sudo blkid
[sudo] password for swastik: 
/dev/sda5: UUID="5888CBBD88CB97C0" LABEL="ww" TYPE="ntfs" 
/dev/sda6: UUID="29f0f166-55fb-4dc7-b9e9-68cef5242a9a" TYPE="reiserfs" 
/dev/sdb3: TYPE="swap" UUID="8ebe8984-88ff-4137-8a49-87ef3a2cadf1" 
/dev/sdb5: UUID="F654C0AB54C07043" LABEL="Archive" TYPE="ntfs" 
/dev/sdb6: UUID="ECD8CA71D8CA3A1A" LABEL="Play" TYPE="ntfs" 
/dev/sdb7: UUID="1bff7e29-4fd7-4de5-b4e6-5e6e2888ca43" TYPE="reiserfs" 
/dev/sda1: UUID="DE60F4A460F48495" LABEL="Wok2" TYPE="ntfs" 
/dev/sdc1: UUID="5a8afd35-3124-4b97-a278-f4c0511c142d" TYPE="reiserfs" 
/dev/sdc3: UUID="0A50E3C250E3B29D" LABEL="Programs" TYPE="ntfs" 
/dev/sdc5: UUID="C8B83773B8375EDE" LABEL="Work" TYPE="ntfs" 
/dev/sdc6: UUID="806C72EA6C72D9FC" LABEL="Media" TYPE="ntfs" 
/dev/sdc7: UUID="0E78954A78953207" LABEL="New Volume" TYPE="ntfs" 
/dev/sda2: UUID="2CA495BDA4958A4A" LABEL="PIII" TYPE="ntfs" 
/dev/sdb2: UUID="8fd779b6-a9d4-44db-b345-a58ab087bc11" TYPE="reiserfs" 
/dev/sdb4: UUID="403dd87c-26cd-4b21-aa14-e747be1dbce0" TYPE="reiserfs" 
```

Normally, my computer rarely goes off. Except when there are kernel upgrades or (being in India) the electricity disappears for a few hours. Here's the problem: 9 times out of 10, boot up reaches fsck and gives an error "filesystem is not clean", asks me to 'rebuild-tree' (which does not help) and finally says just Ctrl+D to continue. On this I can log in but about 50% of my disks are not available so it is quite useless. If I mount -a, it gives me the same errors as before.
My grunt solution to this is simply to never restart, but only to hibernate and resume. But.. that too is not clean or desirable sometimes as (old problem) it resumes to Desktop directly rather than a login screen.
As you can see, I was a windows user for many years, so that's why many ntfs partitions. I don't use windows any more but simply don't have the moolah to go around buying backup disks of this scale. The mount and blkid outputs here are when all disks are properly mounted. The fstab I made myself with help from forums here. What I don't get is why fsck (usually) sticks on the ntfs drives when they are not supposed to be checked. When it happens next time, I will try to copy exactly what fsck doesn't like and post it.
I will appreciate if somebody can make useful suggestions.
Cheers.

---

### Post by marcelkoopman on 2009-02-02
I think you really need to check you ntfs drives for filesystem errors. Why not try a bootable cd like this:
[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

---

### Post by kayvortex on 2009-02-02
> ...the electricity disappears for a few hours.
Yeah, tell me a about it! Damn corrupt officials.

Anyway, maybe you should post the fstab file too. If fsck is tying to check ntfs filesystems then the fstab file might be telling it to do so.

Also, it's going to be pretty bad for your disks if the power keeps getting cut when your system is on: maybe you should look at getting a UPS (uninterrupted power supply) system? I don't really know a lot about them (and especially how to use them, or even how expensive they are), but it's something that you can look at.

Edit: as marcelkoopman says, if you want to do something active now, then I'd also recommend downloading and burning SystemRescueCD. You can boot from there and check the disks manually.

---

### Post by tyk on 2009-02-02
Thanks a lot for the replies.
marcelkoopman: I will definitely check this out. Thanks for the link. 
kayvortex: I do have a ups but sometimes this happens at night or when I'm not around and the system switches off after a bit (20-30 mins). More backup than this gets into a bracket I can't afford :) If I am around I quickly 'hibernate' the system.
Am also attaching my fstab. Please tell if you see any errors. Like I said earlier, it's something I wrote myself.
Cheers.

---

### Post by tyk on 2009-02-02
Sorry but does the forum take some time to show my attachment?

```
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sdb4 :
UUID=403dd87c-26cd-4b21-aa14-e747be1dbce0 / reiserfs relatime 0 1
# Entry for /dev/sdb2 :
UUID=8fd779b6-a9d4-44db-b345-a58ab087bc11 /boot reiserfs notail,relatime 0 2
# Entry for /dev/sdb7 :
UUID=1bff7e29-4fd7-4de5-b4e6-5e6e2888ca43 /home reiserfs relatime 0 2
# Entry for /dev/sdb3 :
UUID=8ebe8984-88ff-4137-8a49-87ef3a2cadf1 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sdc3 /media/Four ntfs-3g defaults,locale=en_IN 0 0
/dev/sdc7 /media/One ntfs-3g defaults,locale=en_IN 0 0
/dev/sdc6 /media/Two ntfs-3g defaults,locale=en_IN 0 0
/dev/sdc5 /media/Work ntfs-3g defaults,locale=en_IN 0 0
/dev/sdb6 /media/Three ntfs-3g defaults,locale=en_IN 0 0
/dev/sdb5 /media/Archive ntfs-3g defaults,locale=en_IN 0 0
/dev/sdc1 /media/vmware reiserfs relatime 0 2
/dev/sda2 /media/Personal ntfs-3g defaults,locale=en_IN 0 0
/dev/sda1 /media/Five ntfs-3g defaults,locale=en_IN 0 0
/dev/sda5 /media/Six ntfs-3g defaults,locale=en_IN 0 0
/dev/sda6 /media/Seven reiserfs relatime 0 2
```

---

### Post by kayvortex on 2009-02-02
Well, your fstab file seems fine. According to that, fsck shouldn't be trying to check your ntfs partitions. Maybe you could try to somehow capture fsck's output next time this does happen. The only thing that comes to mind is that when the ntfs partitions have been scheduled to be chkdsk-ed they wont mount by default on Linux: but you haven't used Windows, and certainly couldn't have scheduled a chkdsk. Maybe you just have general disk corruption on the ntfs partitions.

In any case, burning a SystemRecueCD CD and booting from that will let you safely check your linux partitions: when the CD boots, run fsck manually on your reiserfs partitions (without mounting them, as they should not have been mounted in the first place).
*However*, I doubt that'll really fix the problem because it sounds as though the problem is with the ntfs partitions, which is what you really want to check. This can't be done using any Linux tools: you will have to "acquire" a Windows XP CD, boot into that and run chkdsk /F. It's not really all that hard at all on a XP CD and I'll help run you though it if you like (I'm sure it'll be a lot more obtuse with a Vista CD -- like everything else! -- which is why I said use an XP CD); the only "problem" is "getting" an XP CD in the first place.

---

### Post by dabl on 2009-02-02
The reiserfs filesystem has not been under active maintenance for some time (years now).  If your fsck errors are coming from the reiserfs partitions, you would be very wise to (a) back up that data, and (b) reformat the partitions to an actively supported filesystem type.

---

### Post by tyk on 2009-02-02
I already "have" an xp cd, if I may say so, kayvortex :) err.. my old copy from err.. my laptop (but luckily it's not OEM). Of course I'll have to dig it out. But AFAIcanremember, one couldn't boot from it, i mean, not to a prompt, can one?
But I believe your diagnosis is right, it is the ntfs partitions need chkdsk-ing. But in that case, shouldn't it want to do that every time? Like I said earlier, it's only 9 out of 10 times. Sometimes it sails through.
And though now it's been some time, I was aware of the need to shut down windows 'properly' before installing 'buntu. In fact I did defrag and chkdsk from windows before doing the install. But thereafter, newer and older HDs have come into the machine. I was dual booting for some time and I guess may have forgotten to do the defrag/chkdsk sequence later.
I am downloading the rescue disk but in fact, I logged on back here because the tools it has didn't look like they would 'proxy' chkdsk the disks. Still looks very useful though. I was using a knoppix liveCD for this sort of thing earlier.
Cheers.

---

### Post by tyk on 2009-02-02
Really, dabl? wow, I had no idea. I better do that. Thanks for the info/suggestion. I thought that there was a reiser4 or thereabouts now..
Hmm I hate to do this but I will now bravely restart and get some outputs.
Thanks and cheers.

---

### Post by tyk on 2009-02-02
Well you know about the car and the mechanic......... it booted perfectly.
Here I go again.

---

### Post by tyk on 2009-02-02
You know dabl, you may be right. fsck stuck on two reiserfs partitions. It saved the output like so:

```
swastik@eco:~$ cat /var/log/fsck/checkfs
Log of fsck -C -R -A -a 
Tue Feb  3 01:29:34 2009

fsck 1.40.8 (13-Mar-2008)
Replaying journal..

reiserfs_open: the reiserfs superblock cannot be found on /dev/sdc1.
Failed to open the filesystem.

If the partition table has not been changed, and the partition is
valid  and  it really  contains  a reiserfs  partition,  then the
superblock  is corrupted and you need to run this utility with
--rebuild-sb.

Reiserfs journal '/dev/sda2' in blocks [18..8211]: 0 transactions replayed
Checking internal tree..finished
Reiserfs super block in block 16 on 0x802 of format 3.6 with standard journal
Blocks (total/free): 62240/21288 by 4096 bytes
Filesystem is clean
Replaying journal..
Reiserfs journal '/dev/sda7' in blocks [18..8211]: 0 transactions replayed
Checking internal tree..finished
Reiserfs super block in block 16 on 0x807 of format 3.6 with standard journal
Blocks (total/free): 6480192/3087719 by 4096 bytes
Filesystem is clean

reiserfs_open: the reiserfs superblock cannot be found on /dev/sda6.
Failed to open the filesystem.

If the partition table has not been changed, and the partition is
valid  and  it really  contains  a reiserfs  partition,  then the
superblock  is corrupted and you need to run this utility with
--rebuild-sb.

Reiserfs super block in block 16 on 0x802 of format 3.6 with standard journal
Blocks (total/free): 62240/21288 by 4096 bytes
Filesystem is clean
Reiserfs super block in block 16 on 0x807 of format 3.6 with standard journal
Blocks (total/free): 6480192/3087719 by 4096 bytes
Filesystem is clean
fsck died with exit status 8

Tue Feb  3 01:29:44 2009
```

Even though it mounted my /, /boot and /home partitions alright, which are also reiserfs. Then it mucked up my fstab so that:
```
swastik@eco:~$ mount
/dev/sda4 on / type reiserfs (rw,relatime)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-23-generic/volatile type tmpfs (rw)
/dev/sda2 on /boot type reiserfs (rw,relatime,notail)
/dev/sda7 on /home type reiserfs (rw,relatime)
/dev/sdc5 on /media/Work type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sdb6 on /media/Three type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sdb5 on /media/Archive type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sda5 on /media/Six type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
none on /proc/fs/vmblock/mountPoint type vmblock (rw)
```
If you compare it to my alright mount output, you'll see the difference, it's all wrong. Further attempts to mount any other partition failed for no reason I can understand. For example:
```
swastik@eco:~$ sudo mount -a
[sudo] password for swastik: 
NTFS signature is missing.
Failed to mount '/dev/sdc3': Invalid argument
The device '/dev/sdc3' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
ntfs-3g: Failed to access volume '/dev/sdc7': No such file or directory
Please type '/sbin/mount.ntfs-3g --help' for more information.
NTFS signature is missing.
Failed to mount '/dev/sdc6': Invalid argument
The device '/dev/sdc6' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

NTFS signature is missing.
Failed to mount '/dev/sda2': Invalid argument
The device '/dev/sda2' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
mount: wrong fs type, bad option, bad superblock on /dev/sda6,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```
And this had to be interrupted coz it did not get further than this. It seems since reiserfs partitions did not show up, the order of the rest got mucked up. Oh man, does this mean I have to back up all the reiserfs partitions. Foolish me for trusting it? Thanks dabl, for pointing me in the right direction. 
In any case I can do it in some time but how about the /, /boot and /home partitions? I feel if I am going to abandon reiserfs, I might as well go the full way and reformat these 3 partitions as well. Can you also tell me a good way to do this (or a link to a tutorial/guide)?
Cheers.

---

### Post by kayvortex on 2009-02-02
Yeah, it's pretty handy for doing some recovery tasks and I like it, but again, it doesn't have what I think you really need. On that note, the XP CD that you can dig up will probably be one of two things: either it's a reinstall CD (i.e., just a program to restore a backup image that is/used to be on your system) and not really a proper XP CD, or it *is* a proper XP CD which *should* give the option to go to a dos prompt (I think you have to type 'M' at some point when it gives you the option to, *I think*), but in any case, I can just pop an XP CD that I have (also lying about somewhere) and check that up.

If you're going to reformat your Linux partitions, then SystemRescueCD can wait for another time, I suppose! Also, if reiserfs has been unsupported for some time, then maybe it's a fsck.reiserfs related bug? Maybe. I'd think that a combination of reformatting your Linux partitions, reinstalling your OS, and then trying to chkdsk your ntfs partitions is pretty likely to solve your problem at some point, though!

I'll try to find my XP CD and run through the steps you'll need to do in order to chkdsk your ntfs parts and post them up at some point.

Good luck with the reformatting/reinstalling/searching for CDs...!

---

### Post by kayvortex on 2009-02-02
Sorry, looks like I'm out of sync!
It was a good spot by dabl and I think maybe you should definitely reformat your /, /boot, and /home partitions along with the other two: it's better to be safe than sorry.

As for backing up, I personally just use tar: it's simple and I don't have to learn how to use another program. Just type:
```
sudo tar cvjf /backup/location/backup.tar.bz2 /files/to/backup...
```

I've used it many times and it's always worked fine. However, make sure you're only going to back up files that you'll actually need: i.e., don't bother trying to back up /dev or /proc or /sys or anything like that. If you want to play it ultra safe, back up /home, /boot, /etc, /usr, /opt (just to make sure you don't delete files you may want but forgot about, like your custom menu.lst or sources.list files for example).

---

### Post by tyk on 2009-02-03
Hi kayvortex,
thanks for the replies. Am off for some work right now but will get back and start this backing up. Yeah, I think dabl has got it right too. Quick question: If I backup my /, and just untar it back to the newly formatted partition, will it just work? How about grub and other links to it? As long as I retain the nomenclature of the partition and it's mount point, it will just come back to my original system? It's a bit difficult to believe, but then again I've never done this sort of thing before.
And how's the weather? You guys snowed in as well?
Cheers :)

---

### Post by kayvortex on 2009-02-03
The snow was phenomenal! It hasn't really snowed like that since I was a kid! I'm in London right now, and, of course, I woke up and found out that there were no buses and that getting into central London was going to be a nightmare. Things are back to "normal" again now: there was hardly any snow last night and things are up and running again. Were you snowed in too?!

Anyway, in theory, it will work because everything is just represented as a file in Linux; *but*, if you're talking about making an image of your system (so that you don't have to reinstall your OS), then there are some subtleties: basically you'll have to exclude the /proc directory, and your /mnt and /media directories and maybe a few more too. Also, you'll have to watch out that the files don't grow too large for your file system that you're keeping the backup on.
Take a look at these (since they'll do a better job of explaining it than me):
[https://help.ubuntu.com/community/BackupYourSystem/TAR]("https://help.ubuntu.com/community/BackupYourSystem/TAR")
[http://ubuntuforums.org/showthread.php?t=35087]("http://ubuntuforums.org/showthread.php?t=35087")

**However**, having said that, maybe it's not best to make an image of your system if you're going to format the disks under a different file system. It's probably best to do a clean OS reinstall. In this case, I'd just tar up the different directories that you'll need separately and then put back the files that you want.
So, tar up /home and /root for your docs etc. and then just rely on your reinstalled OS for all your system files. Maybe tar up /etc if you later want a custom modified configuration file. Maybe also /usr if you later find that you deleted a something else that you want (like fonts, maybe), and /boot (although all you'll really need here is menu.lst). But, only put back an odd file or two, not the whole directory!

---

### Post by tyk on 2009-02-03
Kayvortex, thanks for the links. Am going through them right now. Yeah, basically am not veryyyy keen on reinstalling coz I've got a pretty nifty setup on 8.04 running and a thousand programs installed which I might not use all the time but am sort of pleased to know I have. Besides there is an xorg which I managed to tweak together, and finally a fantastically working vmware player and virtualbox which I am not even sure will survive being moved around. Yes, the virtual machines are on a reiserfs partition.
So, basically I am borked a bit. I never had any problems with my hardy install except the one on this thread; in a new install I know I'll be tempted to try Ibex and that'll mean much research and many nights... lemme see lemme see.
Oh where I am the temperature at night is a balmy 20deg C and clothes dry in an hour hanging outside :) Of course there are corrupt officials and there is sometimes no electricity.
Cheers and sunshine.

---

### Post by dabl on 2009-02-03
Reiser4 is (a) experimental, (b) not backward compatible, and (c) very close to unsupported.

[http://en.wikipedia.org/wiki/Reiser4](http://en.wikipedia.org/wiki/Reiser4)

Reiser3, aka reiserfs, is unsupported for some time now (over one year according to the quote in the linked wiki).  So, if you value your data, I would make a quick transition to ext3 for now.

I've run XFS and JFS with *buntu systems -- my Kubuntu 8.10 system has been happy on a JFS filesystem for about 5 months now (since Alpha 5), and I see no signs of trouble.  XFS did not hold up well as a root filesystem -- I got off it after 6 months because it started behaving very flaky with my big Win XP VM.  But I have a couple of large XFS data partitions, where the data is more or less static, and it seems OK that way.

Ext4 will be available in *buntu 9.04 -- I'm going to install it when the Beta version is released in March, and see how it holds up.  Until then, the _safe_ bet is ext3, IMO, especially if you are experiencing power outages, caused by bureaucrats running their margarita blenders.  :)

---

### Post by tyk on 2009-02-03
Hi dabl,
I solved the major part of my problem. Thanks to you for your suggestions. My /, /boot and /home are still reiserfs but they have never given problems so I ain't touching them right now.
But the two other reiserfs partitions have now been backed up and reformatted to ext3... And now I have confidently rebooted 2 times :)
Yay and thanks again.

ps on a different note, is the reiserfs situation due to the unfortunate personal life of Mr. Reiser. Something about a year ago in a paper caught my eye.

And now how do I mark this thread as solved?

---

### Post by dabl on 2009-02-03
Yes, I have the impression that Hans Reiser ran his company as a "one man show", so when he became, errr ... unavailable to render his services, that pretty much ended the effectiveness of Namesys.

Good -- your data should be safe now.  You can run the OS on a reiserfs filesystem for as long as it holds together -- then if you have to reinstall it you can also reformat the partition(s).

If you edit your original post, just insert "SOLVED" into the title, and save it, and you're done.
 

:)

---

### Post by kayvortex on 2009-02-03
Glad to see that you can now reboot like there's no tomorrow, although I can't say that I was all that helpful!

Enjoy the Sun!

---

### Post by tyk on 2009-02-04
Thanks dabl. I will wish Hans Reiser the very best with his problems coz he sure did some interesting work.
Thanks kayvortex, you gave me confidence :)
Cheers.

---

