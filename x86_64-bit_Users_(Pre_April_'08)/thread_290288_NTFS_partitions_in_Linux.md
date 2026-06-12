---
title: "NTFS partitions in Linux?"
date: 2006-11-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by jjandrj6679 on 2006-11-01
Hi all 
I am a Linux newbee and I wrote in a previos thread that I could not edit my NTFS Drives in linux, I kept getting this error:-

"Error while moving items to "/media/sda1... Tv Series"."
"You do not have permissions to write to this folder."

kuja, kindly wrote back sying these two things:-

"In order to write to NTFS partitions in Linux, you must mount them in a different way. It should also be noted that it may not be 100% stable. [https://wiki.kubuntu.org/WriteSuppor...ght=%28NTFS%29](https://wiki.kubuntu.org/WriteSuppor...ght=%28NTFS%29) Use at your own risk."

Then again with this:-

"Another option is to use an ext2 partition and installing a driver in windows for it. I find ext2 to be more stable."

Humm ext2?????

I have read the links and its seems very complicated, and I got the feeling that it was not cut and dry as to whether it would work, or am I miss reading.

Would it be better if I just converted my drives/files to Fat32? or would that be the same problem? or should I convert them to something that Linux can read and get a program in windows to read/write on a linux Disk..if you see what I mean?

I am on a home network with 3 Pc's on it, soon to be 4 as I'm seting up a Media Centre, hopefully without Windows.
Mine (Linux & Xp)
My Partner's is Xp and won't change.. Im working on that.... 
The Other is also Xp but used for Outlook Express as I can not find the same features in Thunderbird. Feel free to ask.

I will need access to all Pc's as we run a lot of media between us.
I know that this is not going to be an easy fix but I'm up for it, as you have probably guessed Im new to linux but very willing to learn.

Any help would be warmly welcomed 
I hope to hear for you soon 
Yours
Josh

---

### Post by ciscosurfer on 2006-11-01
While [this thread]("http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g") (NTFS-3G) says it's still in beta testing (which apparently it is), I've been using this method for nearly 6 months without any problems.

---

### Post by Joeak on 2006-11-01
With Ubuntu you should be able to <read> your NTFS partitions in Windows, but you can't write back to them reliably even after reconfiguring the mount point.  What I do is either A) move shared data up to a Windows or Samba share on another machine, or B) install Windows XP on 1/3 of the hard drive, then create an additional FAT32 partition for the next 1/3, and then install Ubuntu on the remaining 1/3.  The FAT32 partition is read/write for both OS's.

---

### Post by ciscosurfer on 2006-11-01
> **Joeak said:**
> With Ubuntu you should be able to <read> your NTFS partitions in Windows, but you can't write back to them reliably even after reconfiguring the mount point.  What I do is either A) move shared data up to a Windows or Samba share on another machine, or B) install Windows XP on 1/3 of the hard drive, then create an additional FAT32 partition for the next 1/3, and then install Ubuntu on the remaining 1/3.  The FAT32 partition is read/write for both OS's.

Your points are all true and valid, however, I've had great experience using ntfs-3g for a very long time (I successfully backup my /home directory to my Windows backup drive all the time without a hitch).

I think it's worth exploring if you've got the time.  You can always try it out with test data and documents so you can see that everything gets written ok to the drive.

---

### Post by kuja on 2006-11-01
NTFS is not as old or well documented as FAT32. The linux drivers for it aren't perfect. Reading is generally fine, but to write to an NTFS partition can be tricky. 

There are 3 real options.
1) Set up writing to an NTFS partition with ntfs-fuse or ntfs-3g(which is currently in beta)
advantages: write to NTFS, a reasonably new filesystem
disadvantages: drivers aren't 100% stable, better keep backups
2) Use a FAT32 partition for sharing instead.
advantages: stable
disadvantages: It's fat32 - an old, slow filesystem that is subject to corruption
3) Use ext2/3(trusted linux filesystem, Ubuntu's default is ext3) and install an ext2 driver for Windows.
Advantages: modern file system, stable drivers as far as I know
Disadvantages: Not as well known, license=freeware (not OSS)

Method 1) [ntfs-fuse](https://wiki.kubuntu.org/Lkraider/NtfsFuse?highlight=%28NTFS%29) | [ntfs-3g](https://wiki.kubuntu.org/ntfs-3g?highlight=%28NTFS%29)(beta)

Method 2) Shouldn't be any extra steps for this. The linux kernel has good support for FAT32.

Method 3) [EXT2/3 Driver for windows](http://www.fs-driver.org/) - follow the steps there.

---

### Post by jjandrj6679 on 2006-11-01
Thanks to you all, for replying

Ok I'm convinced, i'll try to sort it out using NTFS-3G, on a test drive I have.
You'll all hear from me tomorrow, explaining how I've screwed it all up..lol
Again any help in getting this to work first time would be appreciated, a step by step guide wouldnt go a miss, if anyone has the time.

Yours
Josh

---

### Post by jjandrj6679 on 2006-11-01
Oh damn now Ive read what kuja has just wrote.

Im now confused as to what to do?? Which is the best way? I trust all of your advice as you are the experts. Ill sleep on it. Feel free to post advise on the suject.

Nite

Josh

---

### Post by ciscosurfer on 2006-11-01
@kuja and @jjandrj6679,

Here's my take following the 1,2,3 options listed by kuja:

1)  While NTFS-3G is new (and it uses Fuse, btw), it is stable enough for many users who have NTFS partitions to use safely.  You can read and write to your partitions.  That's a good thing.  And NTFS has been around since 1993, found in the first iteration of Windows NT (hence the 'NT'), so I would hardly call it a new filesystem.  If you are running XP, you're running NT.

2) FAT32 is established, but has a horrible track record and quite blunty, is not that great (remember MS-DOS? FAT32 was used all the way up to Windows ME, or Windows 98 on steroids, I always like to say).  It does, however, allow for reading and writing to/from a Linux-based partition, and if you have an extra FAT32 partition lying around, by all means, go ahead and use it.  If you're running XP, the only FAT32 partition you've got is your recovery partition, and won't have access to that.  So, if you feel like repartitioning your drive and creating a new FAT32 partition, that will work.  Additionally, if you've got any spare room on any of your drives, you can do this FAT32 partitioning right from Ubuntu via gparted (you shouldn't need to use a LiveCD but you can if you feel more comfortable)

3) I've had horrible luck with EXT2 IFS for Windows.  Perhaps they've improved on their code and things might be stable now, I don't know.  When I used it, basically everything on my XP box simply locked up and became unusable -- forget the ability to read/write to my Linux partition.  But, like I said, this was just my experience (coincidentally, many other users have had this same problem, just search the forums and google).  Your mileage my vary.

So, what's my suggestion?  I suggest going with what you're comfortable with.  You can read all the post on NTFS-3G on the forums here and on the Internet to get a better feel for what it entails before you try it out if you want to feel more confident.  Perhaps after reading about it, you will find that you don't want to do it.  And that's okay.  Just remember it's an option (and remember I've used it and I like it and I think it's stable -- again, YMMV.)  Another option would be to check out [Paragon NTFS for Linux]("http://www.ntfs-linux.com/"), burn it as an ISO to a disc, and load 'er up.  It allows for full read/write access from your NTFS drives/partitions to your EXT3 partitions (EXT3 is simply EXT2 with journaling).

In the end, it's up to you.  Go with your gut.  Try different options out.  I've tried all of the aforementioned options and find NTFS-3G to be what works for me the best.  You may find another option better suited to your situation. ;)

---

### Post by kuja on 2006-11-01
> **ciscosurfer said:**
> And NTFS has been around since 1993, found in the first iteration of Windows NT (hence the 'NT'), so I would hardly call it a new filesystem. 
I agree that it's not "new new", but it didn't stay the same since then either. Windows XP and 2003 use NTFS v3.1, which means that it is current as of around 2002 right? Not too old... Then again, the fundamental design is old so I wouldn't exactly call it new either, oh well. I don't use it anyway ;) Yay XFS!

---

### Post by ciscosurfer on 2006-11-01
Most often, XP is considered NT 4.0, Server 2003 is considered 5.0 and Vista is considered 5.1, but now we're just mincing words and probably confusing the OP.  We could probably debate the efficacy of NT in general forever.  I agree with you on one point however: open source formats are much more effective and XFS is pretty cool and useful and has been around since _scratching head_ 1994 I believe created by Silicon Graphics for the IRIX OS, right?  I'm a little fuzzy on that though, you can double-check me on the facts.  XFS was intrumental in the beginning days of journaling and really pushed the limits of high-performace journaling back then.  I think EXT3 is pretty good though ;)

---

### Post by kuja on 2006-11-01
No, if you looked at the version number of Windows XP, it would say something along the lines of NT5.1, if I do recall. Personally, I don't care. I haven't used XP at home in years.

Yes, XFS was developed by Silicon Graphics Inc. for their IRIX OS. I'm not sure if it was instrumental in the beginning days or not (probably was, I'm sure wikipedia knows ;)), but even now it's arguably (and people do argue about it) the highest performance filesystem around. 
In the old days there were apparantly problems with its stability. The words "data loss from hell" come to mind. That problem seems to have been fixed. I don't see how they could afford not to fix it seeing as IRIX was a server OS.  I've had no trouble with it even during sudden powerouts &c. The only thing I don't like about XFS is that grub doesn't like to boot from it, so I have to create a separate boot partition (something like ext2)
EXT3 is pretty decent, but I wouldn't exactly call it high performance. (Even EXT2 is quite a bit faster (Thanks to the journaling, which is the only major change that I know of) EXT3 is very stable though, can't really go wrong with it.

Edit: Looked something up. It looks like XFS was in fact the first Journaling file system available for *NIX.

---

### Post by ciscosurfer on 2006-11-01
> **kuja said:**
> No, if you looked at the version number of Windows XP, it would say something along the lines of NT5.1, if I do recall. Personally, I don't care. I haven't used XP at home in years.

Aye, juna!  [According to MSDN]("http://msdn.microsoft.com/msdnmag/issues/01/12/XPKernel/"), you are correct -- 2000 was 5.0 and XP is 5.1 (at least in their first iterations).  Good one!

As for wikipedia...hmm...I only go their sometimes, but ROTFL, that's crazy what it says about XFS!  I just remember 10 or so years ago messing around with it and IRIX.  Go figure.

On a completely unrelated note: do you thing the OP is royally confused about now?  LOL.

---

### Post by jjandrj6679 on 2006-11-01
Morning all
I have read all that was written, and I thank you for that.
Couple of questions though.

Which ever I choose, do I make a partion on a drive or do I make the whole drive Ext2/Ntfs+Fuse/ntfs-3g.

Does either do Sata as I have not read anything about it anywhere, or is that another topic?

All drives were NTFSed in Partition Magic

I have a 240 Sata drive with 150 gigs used & 90 gigs spare, how would I approach that drive. Making the 90 a new partition or the whole 240?

I also have an 80 gig with 21gigs spare

I have 37gig Windows drive.

I also have this drive which contains Linux which I partitioned (In linux) to four partitions 2 of which where swap files, my reasoning was that I was also installing Sues on the second partition but it failed and in a moment of madness I installed Ubuntu 32bit instead... I wasn't rational at the time (I just wanted to get rid of Xp and all the company stands for.)
Im also trying to figure out how to sort it. I think that I am going to do a fresh install of Ubuntu 64 as I now have the confidece to re-create what I have learned so far, also sorting out many problems that I have encountered along the way.

 am I crazy or have I just miss read it?
Over to the experts and I thank you again for helping me.

Yours
Josh

---

### Post by jjandrj6679 on 2006-11-01
Morning all
I have read all that was written, and I thank you for that.
Couple of questions though.

Which ever I choose, do I make a partion on a drive or do I make the whole drive Ext2/Ntfs+Fuse/ntfs-3g.

Does either do Sata as I have not read anything about it anywhere, or is that another topic?

All drives were NTFSed in Partition Magic

I have a 240 Sata drive with 150 gigs used & 90 gigs spare, how would I approach that drive. Making the 90 a new partition or the whole 240?

I also have an 80 gig with 21gigs spare

I have 37gig Windows drive.

I also have this drive which contains Linux which I partitioned (In linux) to four partitions 2 of which where swap files, my reasoning was that I was also installing Sues on the second partition but it failed and in a moment of madness I installed Ubuntu 32bit instead... I wasn't rational at the time (I just wanted to get rid of Xp and all the company stands for.)
Im also trying to figure out how to sort it. I think that I am going to do a fresh install of Ubuntu 64 as I now have the confidece to re-create what I have learned so far, also sorting out many problems that I have encountered along the way.

am I crazy or have I just miss read it?
Over to the experts and I thank you again for helping me.

Yours
Josh

---

### Post by jjandrj6679 on 2006-11-01
Just a foot note, 
My ultimate goal is to get away from windows altogether on this machine and my networked pc, but still have access to 1 or 2 pc's on our network that would run xp, and have access to all the drives from which ever pc.

I have an Asetek cooling system that runs but is not controlable except in windows, so somehow I need to be able to run cirtain windows programs, control systems and the like in Linux.
Thats why I went to install WINE but it all went down hill from there on..
Josh

Ps sorry for the double entry

---

### Post by jjandrj6679 on 2006-11-01
Hi there
I decided to try ext2/3 so I went here
[http://www.fs-driver.org/](http://www.fs-driver.org/)
downloaded and installed on my Xp drive whilst in xp.
its given me access to the Linux drives but not the other way round? Which is a start. Is it permissions or have I missed the point...again...

I am also going to do a re-boot on both Xp & Ubuntu 64
Should I install both om the 37gig or on seperate drives, alo which should I install 1st, Xp or Ubuntu?

Thanks Josh

---

### Post by ciscosurfer on 2006-11-02
The EXT2 IFS driver you added to XP gives you access to your Linux drives from XP (not the other way around).  EXT2 IFS is a way to access your Ubuntu files from XP and doesn't work "in the flip".

You should either create a FAT32 partition on your XP drive or go the NTFS-3G route on your Ubuntu drive.  Either of these two methods gives you read/write access in Ubuntu of all your Windows files.

It is ideal to install XP first, then Ubuntu.

---

### Post by jjandrj6679 on 2006-11-02
Hi there
Ooop I miss understood beforhand.
Should I unistall EXT2 IFS first.?

JJ

---

### Post by Joeak on 2006-11-02
Okay so now I've tried the [http://fs-driver.org](http://fs-driver.org) driver for Windows and it looks like it works fine.  Also, I followed this procedure I found on [http://lunapark6.com/?p=1710](http://lunapark6.com/?p=1710) (near the bottom of the comments):

> Download Fuse from here [http://prdownloads.sourceforge.net/f...ar.gz?download](http://prdownloads.sourceforge.net/f...ar.gz?download)
tar -xvf fuse-2.5.3.tar.gz
cd fuse-2.5.3.tar.gz
sudo apt-get install build-essential
sudo apt-get build-dep fuse
./configure
make
sudo make install

Then download NTFS-3G from here [http://mlf.linux.rulez.org/mlf/ezaz/...70714-BETA.tgz](http://mlf.linux.rulez.org/mlf/ezaz/...70714-BETA.tgz)
tar -xvf ntfs-3g-20070714-BETA.tgz
cd ntfs-3g-20070714-BETA
./configure
make
sudo make install

Then add it to your fstab
/dev/hda1 /mnt/windows ntfs-3g silent,umask=0 0 0

Check to see if you have write permissions
sudo modprobe fuse && sudo umount -a && sudo mount -a

Now to make fuse load at bootup
echo fuse | sudo tee -a /etc/modules

Done.

So now my Windows OS can read/write my Ubuntu partition, and vice versa!

---

### Post by jjandrj6679 on 2006-11-02
Hi there
Thanks for that

I think Ive ballzd up again
I copied this 

sudo apt-get install build-essential
sudo apt-get build-dep fuse

and got this

josh@josh-desktop64:~$ sudo apt-get install build-essential
Password:
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  binutils cpp cpp-4.0 dpkg-dev g++ g++-4.0 gcc gcc-4.0 libstdc++6-4.0-dev
  make
Suggested packages:
  binutils-doc cpp-doc gcc-4.0-locales debian-keyring gcc-4.0-doc manpages-dev
  autoconf automake1.9 libtool flex bison gcc-doc libc6-dev-i386
  libstdc++6-4.0-doc stl-manual
Recommended packages:
  libmudflap0-dev
The following NEW packages will be installed
  binutils build-essential cpp cpp-4.0 dpkg-dev g++ g++-4.0 gcc gcc-4.0
  libstdc++6-4.0-dev make
0 upgraded, 11 newly installed, 0 to remove and 0 not upgraded.
Need to get 8921kB of archives.
After unpacking 31.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main binutils 2.16.1cvs20060117-1ubuntu2 [1563kB]
Get: 2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main cpp-4.0 4.0.3-1ubuntu5 [2261kB]
Get: 3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main cpp 4:4.0.3-1 [31.0kB]
Get: 4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main gcc-4.0 4.0.3-1ubuntu5 [526kB]
Get: 5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main gcc 4:4.0.3-1 [5040B]
Get: 6 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main libstdc++6-4.0-dev 4.0.3-1ubuntu5 [1480kB]
Get: 7 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main g++-4.0 4.0.3-1ubuntu5 [2585kB]
Get: 8 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main g++ 4:4.0.3-1 [1388B]
Get: 9 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main make 3.80+3.81.b4-1 [299kB]
Get: 10 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main dpkg-dev 1.13.11ubuntu6 [163kB]
Get: 11 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main build-essential 11.1 [6672B]
Fetched 8921kB in 33s (269kB/s)
Selecting previously deselected package binutils.
(Reading database ... 110677 files and directories currently installed.)
Unpacking binutils (from .../binutils_2.16.1cvs20060117-1ubuntu2_amd64.deb) ...
Selecting previously deselected package cpp-4.0.
Unpacking cpp-4.0 (from .../cpp-4.0_4.0.3-1ubuntu5_amd64.deb) ...
Selecting previously deselected package cpp.
Unpacking cpp (from .../cpp_4%3a4.0.3-1_amd64.deb) ...
Selecting previously deselected package gcc-4.0.
Unpacking gcc-4.0 (from .../gcc-4.0_4.0.3-1ubuntu5_amd64.deb) ...
Selecting previously deselected package gcc.
Unpacking gcc (from .../gcc_4%3a4.0.3-1_amd64.deb) ...
Selecting previously deselected package libstdc++6-4.0-dev.
Unpacking libstdc++6-4.0-dev (from .../libstdc++6-4.0-dev_4.0.3-1ubuntu5_amd64.deb) ...
Selecting previously deselected package g++-4.0.
Unpacking g++-4.0 (from .../g++-4.0_4.0.3-1ubuntu5_amd64.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4%3a4.0.3-1_amd64.deb) ...
Selecting previously deselected package make.
Unpacking make (from .../make_3.80+3.81.b4-1_amd64.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.13.11ubuntu6_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.1_amd64.deb) ...
Setting up binutils (2.16.1cvs20060117-1ubuntu2) ...

Setting up cpp-4.0 (4.0.3-1ubuntu5) ...
Setting up cpp (4.0.3-1) ...

Setting up gcc-4.0 (4.0.3-1ubuntu5) ...
Setting up gcc (4.0.3-1) ...

Setting up make (3.80+3.81.b4-1) ...

Setting up dpkg-dev (1.13.11ubuntu6) ...
Setting up g++-4.0 (4.0.3-1ubuntu5) ...
Setting up libstdc++6-4.0-dev (4.0.3-1ubuntu5) ...

Setting up g++ (4.0.3-1) ...

Setting up build-essential (11.1) ...
josh@josh-desktop64:~$ sudo apt-get build-dep fuse
Reading package lists... Done
Building dependency tree... Done
E: Unable to find a source package for fuse

Has it gone wrong? 

And what do I do with this command?
./configure
make
sudo make install

Im still very new to linux so sorry for the stupid q's

I havnt done the second bit of your note as I havn't completed the first.
JJ

---

### Post by Joeak on 2006-11-02
The way I followed the fuse part of the instructions was basically click on the link to download, let it default to opening with the Archiver(?) utility (kind of like winzip).  The compressed file contains a FOLDER with contents. Right-click on the folder, pick Extract, mine defaulted to extracting to the /tmp directory.  Then open a shell (like where you did the apt-get command), type in "cd /tmp/fuse<tab>" and with the tab key it should autocomplete to the dirctory you extracted.  (I might have the directory name wrong; I'm in Windows now.)  You have to be IN that directory for the sudo apt-get build-dep fuse command and other commands to work.  You have to do basically the same thing for the second package listed in the instructions, but the tmp directory will be different.

---

### Post by kuja on 2006-11-02
As per ntfs-3g, why not use the wiki? [https://wiki.kubuntu.org/ntfs-3g](https://wiki.kubuntu.org/ntfs-3g)

---

### Post by darrenm on 2006-11-02
I found NTFS 3G a bit unstable and very CPU intensive

I use the ext2/3 driver for Windows and that works perfect

[http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)

---

### Post by givré on 2006-11-02
EDIT :hum, no more need to worry.

---

### Post by ciscosurfer on 2006-11-02
@givre,
The driver in the repos contains a bug?  What's the bug?  I'm using the driver on Edgy downloaded from the repos and all is well.  Please advise.

---

### Post by givré on 2006-11-02
> **ciscosurfer said:**
> @givre,
The driver in the repos contains a bug?  What's the bug?  I'm using the driver on Edgy downloaded from the repos and all is well.  Please advise.
Of course not, but the instructions Joeak mention installed the first version of ntfs-3g which is known to have a bug.

Anyway, szaka, decide to redirect the old link to the new main page of ntfs-3g...

---

### Post by ciscosurfer on 2006-11-02
> **givré said:**
> Of course not, but the instructions Joeak mention installed an old version of ntfs-3g.

Ah, yes.  Good to know.  As always, givré, thanks for providing the community with such awesome (ntfs-3g) drivers -- they are outstanding!

ciscosurfer

---

### Post by jjandrj6679 on 2006-11-02
Hi there Joeak

I downloaded both files to my desktop, which I assume is here, yes?
home/josh/desktop/
The unpacked files are called fuse-2.5.3 & ntfs-3g-0.20061031-BETA
I used Archive Manager to unpack them to the desktop.
I opened the Terminal and did this:-

josh@josh-desktop64:~$ cd/home/josh/desktop/fuse-2.5.3
bash: cd/home/josh/desktop/fuse-2.5.3: No such file or directory
josh@josh-desktop64:~$ cd/home/josh/desktop/fuse-2.5.3<tab>
bash: syntax error near unexpected token `newline'
josh@josh-desktop64:~$ cd/home/josh/desktop/fuse-2.5.3
bash: cd/home/josh/desktop/fuse-2.5.3: No such file or directory
josh@josh-desktop64:~$ cd/home/josh/desktop/fuse
bash: cd/home/josh/desktop/fuse: No such file or directory
josh@josh-desktop64:~$ cd/desktop/fuse2.5.3
bash: cd/desktop/fuse2.5.3: No such file or directory
josh@josh-desktop64:~$ cd/desktop/fuse-2.5.3
bash: cd/desktop/fuse-2.5.3: No such file or directory
josh@josh-desktop64:~$ cd/fuse-2.5.3
bash: cd/fuse-2.5.3: No such file or directory
josh@josh-desktop64:~$ cd/home/josh/desktop64/fuse-2.5.3
bash: cd/home/josh/desktop64/fuse-2.5.3: No such file or directory
josh@josh-desktop64:~$
bash: cd/desktop/Test1: No such file or directory
josh@josh-desktop64:~$ cd/fuse-2.5.3
bash: cd/fuse-2.5.3: No such file or directory

Being brand new to linux I havn't a clue whats going wrong, as far as I can see I've asked it to open a folder on the desktop, but as you can see it hasn't found it. Why? This isn't the first time this has happened.
I have learnt a hell of a lot in two weeks but I can't seem to get my head around some of the most basic commands. To me I have written the correct details, but as you can see I havn't.

Is there a basic (For Dummies) that I can read so that I can learn faster, I like linux but I could so easily just give up and go & buy Vista & live with its horrors.....but I do not want to do that & Im made of stronger stuff than that. 

So if you lot do not mind me pestering you a lot more, and you have the patients of a saint, then I'll feel a lot better. 

So.. onwards and upwards.
I look forward to hearing from you
Yours
Josh

---

### Post by ciscosurfer on 2006-11-02
Commands in Linux are case-sensitive.  So you can enter sudo <whatever> but not Sudo, SUDO, or SuDo <whatever>...you get the point.  Spaces are important as well.  To get to your Desktop, you need to use an uppercase "D".  So the correct syntax would be```
cd /home/josh/Desktop
```It is always a good idea, if you can, to install from pre-made packages called .deb packages (stands for Debian package...b/c, of course, Ubuntu is based on Debian).  Until you get a handle on things (don't worry, we were all beginners once), I would simply advise against trying to build and compile from source.  Once you get the hang of it, it's not that hard though.  I would also advise again the use of make install, btw.  I would use checkinstall instead (but that's for a later post/thread...just search around the forums for info on checkinstall and why you should use it)

So I would try to grab the .deb files from the repositories first before building it from source.  For more on adding repositories, click here, and look for 'adding repositories'...that page btw is a great beginners resource as well. --The links I provided in my earlier posts will get you going, too.

That said, here is my quick and dirty list of URLs to get you going:

[http://google.com/linux](http://google.com/linux)
[http://help.ubuntu.com](http://help.ubuntu.com)
[http://wiki.ubuntu.com](http://wiki.ubuntu.com)
[http://doc.gwos.org/index.php/Main_Page](http://doc.gwos.org/index.php/Main_Page)
[http://ubuntuguide.org](http://ubuntuguide.org)
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)  (highly recommended)

The Absolute Beginners section on ubuntuforums.org is excellent and will provide you with additional tips and links (check the "Sticky Threads" section at the top of Absolute Beginners page).

Good Luck!

---

### Post by jjandrj6679 on 2006-11-02
Hi there all of you

Thanks for that, sorry for being Sooooo dim.

I went to Autotatix site and did as it said...and it works, so Automatix2 is now on my sysyem.... now thats a first for this newbee...lol

Ok so I assume this will help me run WinXp progs in Linux &/or be able to access my NTFS drives thru Linux too,yes? so therefore which prog do I use to get my H2O Watercooling Control Center (H2OCC) working?
Or have I got it wrong again?

I did as explained here:-

sudo apt-get install build-essential
sudo apt-get build-dep fuse
./configure
make
sudo make install

All seemed to go well, then this

cd ntfs-3g-20070714-BETA
./configure
make
sudo make install

Tonnes of script flew by and then this was at the end:-

ln -s -f ntfs-3g.8 /usr/local/man/man8/mount.ntfs-3g.8
make[3]: Leaving directory `/home/josh/Desktop/ntfs-3g-0.20061031-BETA/src'
make[2]: Leaving directory `/home/josh/Desktop/ntfs-3g-0.20061031-BETA/src'
make[1]: Leaving directory `/home/josh/Desktop/ntfs-3g-0.20061031-BETA/src'
make[1]: Entering directory `/home/josh/Desktop/ntfs-3g-0.20061031-BETA'
make[2]: Entering directory `/home/josh/Desktop/ntfs-3g-0.20061031-BETA'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/josh/Desktop/ntfs-3g-0.20061031-BETA'
make[1]: Leaving directory `/home/josh/Desktop/ntfs-3g-0.20061031-BETA'
josh@josh-desktop64:~/Desktop/ntfs-3g-0.20061031-BETA$

Then I tried this: 
josh@josh-desktop64:~/Desktop/ntfs-3g-0.20061031-BETA$ /dev/hda1 /mnt/windows ntfs-3g silent,umask=0 0 0

got this: 
bash: /dev/hda1: Permission denied

so I did this: 
josh@josh-desktop64:~/Desktop/ntfs-3g-0.20061031-BETA$ sudo modprobe fuse && sudo umount -a && sudo mount -a

got this:
umount: /dev: device is busy
umount: /var/run: device is busy
umount: /: device is busy

so I did this:
josh@josh-desktop64:~/Desktop/ntfs-3g-0.20061031-BETA$ echo fuse | sudo tee -a /etc/modules

got this:
fuse
josh@josh-desktop64:~/Desktop/ntfs-3g-0.20061031-BETA$


Now I do not have any drives in my Places Menu, I assume that they have been unmounted?

Where did I go wrong with this? I have kept the terminal open just in case?

I also have a copy of most of what the teminal spewed out but not my initial instructions that I wrote, I assume it has a maximum lineage?

Any more help on this one?

Greatfully Yours
Josh

---

### Post by Cynical on 2006-11-02
I've found it interesting how many people say ntfs-3g is unstable or point out that it is beta software. I've used it for months now copying files of all sizes (like 4GB DVD iso's) without any trouble. It could be faster, but it seems to be as stable as it can get to me.



You need to edit your fstab and change ntfs to ntfs-3g, then run umount -a and mount -a. After that it should be done.

---

### Post by pony-tail on 2006-11-02
ntfs-3g - works OK on Win2k partitions , I have only ever wound up with one corrupted file . I cant use Fat32 because the files are over 4gig . I also use Explore2fs a freeware (not gnu) ext2/3 partition reader for Windoze no issues yet . It is old (came off a magazine CD )but there may be a current version available

---

### Post by ciscosurfer on 2006-11-02
@jjandrj6679,

Follow [the directions here]("http://www.ntfs-3g.org/") to setup your /etc/fstab and how to mount your drives for access.

---

### Post by jjandrj6679 on 2006-11-02
Humm some worked some didn't..

I did this
 ./configure
  make
  sudo make install

& got this (Copied just the end bit for you)
make[3]: Leaving directory `/home/josh/Desktop/ntfs-3g-0.20061031-BETA/src'
test -z "/usr/local/man/man8" || mkdir -p -- "/usr/local/man/man8"
 /usr/bin/install -c -m 644 './ntfs-3g.8' '/usr/local/man/man8/ntfs-3g.8'
make  install-data-hook
make[3]: Entering directory `/home/josh/Desktop/ntfs-3g-0.20061031-BETA/src'
/usr/bin/install -c -d /usr/local/man/man8
ln -s -f ntfs-3g.8 /usr/local/man/man8/mount.ntfs-3g.8
make[3]: Leaving directory `/home/josh/Desktop/ntfs-3g-0.20061031-BETA/src'
make[2]: Leaving directory `/home/josh/Desktop/ntfs-3g-0.20061031-BETA/src'
make[1]: Leaving directory `/home/josh/Desktop/ntfs-3g-0.20061031-BETA/src'
make[1]: Entering directory `/home/josh/Desktop/ntfs-3g-0.20061031-BETA'
make[2]: Entering directory `/home/josh/Desktop/ntfs-3g-0.20061031-BETA'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/josh/Desktop/ntfs-3g-0.20061031-BETA'
make[1]: Leaving directory `/home/josh/Desktop/ntfs-3g-0.20061031-BETA'
josh@josh-desktop64:~/Desktop/ntfs-3g-0.20061031-BETA$

So as there were no errors so I moved onto the Installation section. Am I in the wrong folder? is that why this didn't work?

I did as copied & pasted as directed
josh@josh-desktop64:~/Desktop/ntfs-3g-0.20061031-BETA$ ntfs-3g /dev/hda1 /mnt/windows

but I got this
Error opening partition device: Permission denied
Failed to startup volume: Permission denied
Failed to mount '/dev/hda1': Permission denied
josh@josh-desktop64:~/Desktop/ntfs-3g-0.20061031-BETA$

A quick look to see if any drives had appered, all but my linux drive are in the Places menu of which I got Permission denied.
"The folder contents could not be displayed."
"You do not have the permissions necessary to view the contents of "disks-conf-hda1"."
Now there is nothing on them, I assume that I have not lost my data, just not being shown it?  I hope! In Syst/Amin/Disks they are there as they were some enabled some not. I'm not panicing yet.
JJ

---

### Post by ciscosurfer on 2006-11-02
Please post the output from the following commands```
sudo fdisk -l
```...that's dash lowercase "L" not the number "1".

And```
cat /etc/fstab
```The point here is that if you have your /etc/fstab file setup correctly, there is no need to manually mount your drive, the OS will do so at boot time.

Please also post the output of this command to make sure the word "fuse" has been added to your /etc/modules file...if not, open 'er up and add the word "fuse" after the last word in the list```
echo fuse | sudo tee -a /etc/modules
```And yes, you compile all source from within the same directory -- all steps to compile should be performed in the same directory because each subsequent command depends on the command issued before it.

When you issue any sort of mount command (ntfs-3g acts as a mount command), you need to use sudo to do it.  After you've posted the above outputs, try the command you issued last preceded with sudo.  So```
sudo ntfs-3g /dev/hda1 /mnt/windows
```This assumes that you've created a directory (sudo mkdir /mnt/windows and that your device file for the Windows partition is /dev/hda1 -- the output from **sudo fdisk -l** will confirm this).  As a side note, only items located in /media will/should show up in your places menu and likewise on your Desktop if you set the correct options to make them visible in your Configuration Editor under apps > nautilus > desktop > place a checkmark in the 'volumes_visible' box.

So really, we want to create a directory in the /media directory, call it /media/windows and have the appropriate line in our /etc/fstab file to mount it at boot time.  

We'll get you there! ;)

And no, you haven't lost your data, you just can't see it yet 8)

---

### Post by jjandrj6679 on 2006-11-02
Hi
Ok here is the fdisk -l readout:-

josh@josh-desktop64:~$ sudo fdisk -l
Password:

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30515   245111706    7  HPFS/NTFS

Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4998    40146403+   7  HPFS/NTFS

Disk /dev/hdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9964    80035798+   7  HPFS/NTFS

Disk /dev/hdc: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1        1020     8193118+  83  Linux
/dev/hdc2            1085        3583    20073217+  83  Linux
/dev/hdc3            1021        1084      514080   82  Linux swap / Solaris
/dev/hdc4            3584        3649      530145   82  Linux swap / Solaris

Partition table entries are not in disk order
josh@josh-desktop64:~$


Here is the cat /etc/fstab Readout:-

josh@josh-desktop64:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
/dev/hdb1       /media/hdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
/dev/hdc1       /media/hdc1     ext3    defaults        0       2
/dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
/dev/hdc4       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
josh@josh-desktop64:~$


Here is the echo fuse | sudo tee -a /etc/modules readout:-

josh@josh-desktop64:~$ echo fuse | sudo tee -a /etc/modules
Password:
fuse
josh@josh-desktop64:~$

I hope this is what you need, meanwhile I'm still digesting what you wrote and the causes of my actions.

I have opened all of these is separate Terminals, is that ok to do so, they are all still open while I read & digest.
I tryed this sudo ntfs-3g /dev/hda1 /mnt/windows in the same terminal as before but got this error:-

josh@josh-desktop64:~/Desktop/ntfs-3g-0.20061031-BETA$ sudo ntfs-3g /dev/hda1 /mnt/windows
Password:
Error opening partition device: Device or resource busy
Failed to startup volume: Device or resource busy
Failed to mount '/dev/hda1': Device or resource busy
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.
josh@josh-desktop64:~/Desktop/ntfs-3g-0.20061031-BETA$

Is this coz I have too many terminals open?
JJ

---

### Post by jjandrj6679 on 2006-11-02
"if you set the correct options to make them visible in your Configuration Editor under apps > nautilus > desktop > place a checkmark in the 'volumes_visible' box."

I do not have that on my system, I also searched for it thru Plases/search but nout. Although nautilus installed in the Synaptic P/M..Hummm 

But I do have gconf-editor 2.14.0 Being let loose here at this early stage of my linux lifecycle could be explosive for the pc & my brain...lol... I've just learnt to crawl with linux....Just looking for the chair to help me stand up on me own two feet... lol
Thanks for the confidence boost though..
JJ.

---

### Post by ciscosurfer on 2006-11-02
Okay, this is what we'll do.  Follow these steps and reboot your computer.  Once your up again, all 3 NTFS drives should appear in your Places menu and you should have full read/write access to them.  To test this, you can create a file in Ubuntu, right-click copy it, and paste it on or in your Windows partition that you'll have open.  If it pastes, you're good to go.

Here are the steps (you can copy/paste these into a terminal):

1) Go to your /media directory.  If the **hda1**, **hdb1**, and **sda1** are already there, then skip this step.  Otherwise, create the following directories```
sudo mkdir /media/sda1 && sudo mkdir /media/hda1 && sudo mkdir /media/hdb1
```2) Copy your old /etc/fstab to a backup and then modify your current /etc/fstab file```
sudo cp /etc/fstab /etc/fstab.backup
sudo gedit /etc/fstab
```Once you have your /etc/fstab file open, make the following changes to the lines I have bolded for you.  I will do a before and after shot so you understand:
[B]
_Your current /etc/fstab file_[/B]_:_
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc2       /               ext3    defaults,errors=remount-ro 0       1
** /dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0    1**
** /dev/hdb1       /media/hdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0    1**
/dev/hdc1       /media/hdc1     ext3    defaults        0       2
** /dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0    1**
/dev/hdc4       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0


[U][B]What we want /etc/fstab to look like instead (this is what I do, you might find others do it slightly differently, but this works for me just fine):
[/B][/U] # /etc/fstab: static file system information.
 #
 # <file system> <mount point>   <type>  <options>       <dump>  <pass>
 proc            /proc           proc    defaults        0       0
 /dev/hdc2       /               ext3    defaults,errors=remount-ro 0       1
** /dev/hda1       /media/hda1  ntfs-3g     silent,no_def_opts,locale=en_US.utf8,umask=0,allow_other 0       0**
** /dev/hdb1       /media/hdb1  ntfs-3g     silent,no_def_opts,locale=en_US.utf8,umask=0,allow_other 0       0**
 /dev/hdc1       /media/hdc1     ext3    defaults        0       2
** /dev/sda1       /media/sda1  ntfs-3g     silent,no_def_opts,locale=en_US.utf8,umask=0,allow_other 0       0**
 /dev/hdc4       none            swap    sw              0       0
 /dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0


Save the file, exit, reboot.

---

### Post by ciscosurfer on 2006-11-02
You have to make the Configuration Editor visible on your menu (although you can also go straight to it in a terminal with what said before: **gconf-editor**)

In a terminal, type in [B]alacarte

[/B]Go to System Tools, click it (located just below Sound & Video)

Place a checkmark in the box next to "Configuration Editor", save/close alacarte.

Go to your Applications menu in the upper left corner, click it, drill down to System Tools, and there you will find Configuration Editor.

---

### Post by jjandrj6679 on 2006-11-02
Hi there
Just a point, the File System tree file has a Red No Entry on it at the mo.
In media I have 
hda1, hdb1, hdc1, sda1, cdrom0

So I didn't do the 1st bit. But did this
josh@josh-desktop64:~$ sudo cp /etc/fstab /etc/fstab.backup (this is an auto backup said file command??)
Password:
josh@josh-desktop64:~$ sudo gedit /etc/fstab
GTK Accessibility Module initialized

& it produced the fstab list.
Now I have done as you explained and copied it over, although I lined everything up with the origional?
heres what it looked like before rebooting. This post is sent before reboot

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs-3g silent,no_def_opts,locale=en_US.utf8,umask=0,allow _other 0 0
/dev/hdb1       /media/hdb1     ntfs-3g silent,no_def_opts,locale=en_US.utf8,umask=0,allow _other 0 0
/dev/hdc1       /media/hdc1     ext3    defaults        0       2
/dev/sda1       /media/sda1     ntfs-3g silent,no_def_opts,locale=en_US.utf8,umask=0,allow _other 0 0
/dev/hdc4       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0


As to Config editor I typed alacarte, got this
josh@josh-desktop64:~$ alacarte
GTK Accessibility Module initialized
Bonobo accessibility support initialized

(alacarte:23041): GnomeUI-CRITICAL **: gnome_icon_selection_clear: assertion `gis != NULL' failed

(alacarte:23041): GnomeUI-CRITICAL **: gnome_icon_selection_add_directory: assertion `gis != NULL' failed

(alacarte:23041): GnomeUI-CRITICAL **: gnome_icon_selection_show_icons: assertion `gis != NULL' failed

but the Alacarte Menu Editor came up, drilled down to System Tools, there is  a checkmark already in the box next to "Configuration Editor", the icon is a car with its hood/bonnet up & a spanner. "gconf-editor" not "nautilus"???

Now a reboot. Gulp
JJ

---

### Post by jjandrj6679 on 2006-11-02
Now rebooted
In Places I only have hdc1 & Cd/dvdrom?
Less than I started with..Humm
They are still in my media file
What have I done wrong this time?
I cant even get a simple copy n paste right, perhaps this is the penance for my past and I will be exiled to VistaHell from here on...... Nope Ill stick it out here  if your willing..??
JJ

---

### Post by ciscosurfer on 2006-11-02
Did you exit your last session from Windows cleanly?  Sometimes this will affect whether or not the drives show up b/c to Ubuntu they will look 'dirty' if you don't shutdown clean.  

Try booting in Windows, all the way up, and then shutdown normally.  

Try booting to Ubuntu and see what happens after that.  

Other that what we've discussed in the last few posts, I would suggest you try to follow one of the guides that tells you how to download ntfs-3g as a package (instead of building it the way you did).  

Post back here when you've at least done the Windows part I mentioned above.

---

### Post by jjandrj6679 on 2006-11-03
Hi there
Nope still the same as before...Grrr
Ok  I went to [http://www.ntfs-3g.org/](http://www.ntfs-3g.org/) 
& D/l the latest NTFS-3G driver is ntfs-3g-0.20061031-BETA.tgz
and then what do i do?
I tryed "sudo ./configure" but got "command not found"
soo I went to the FUSE ([http://fuse.sourceforge.net/](http://fuse.sourceforge.net/)) link and typed this in "sudo mkdir /tmp/fuse" & got "File exists" So I checked and there it was, empty.
So I typed in the next line "sudo ./hello /tmp/fuse" & got this "./hello: command not found"

I know that I hav'nt put something here but what? What do i not get? I can't even change directory without having a problem, will i ever understand, this is sending me bonkers/nuts 
Sorry needed to vent some steam..

So I,m deeper in the brown stuff!! What do I do now?

I can see why most people stck with windows now, I knew it was going to be a learning curve but I was'nt expecting it to be this steep...lol
JJ

---

### Post by jjandrj6679 on 2006-11-03
I dont know if this helps and may be where some of my problems lie, 
2 weeks ago when I had 40 fits over windows and said f### it to Microsoft, I installed Ubuntu32 onto a seperate drive.
Upon completion I saw that there was a 64 bit version too, so I installed that on a separate partition(4 Partitions, 2 hdc1(ext3) & 2 swaps hdc3 & 4)
So I have one drive with U32 on hdc1 (I kthink its 32bit as the desktop has just one file on it, 64bit that Im using has loads) with that knowledge I belive the U64 is installed on hda2.
Secondly just hours before I fled Xp I installed Vista RC1 on this very drive.

so my boot up is thus foe windows
first the grub, drill down to windows
it will auto Vista (No longer Installed) if I dont change it to Xp
then into Xp

For U64
switch on pc and leave it to auto boot to the desktop which is the U64 version.

The Grub has about 11/12 lines 
Top of the list is 
Ubuntu,kernel 2.6.15-27-AMD64-Generic
Under the windows bit is
Ubuntu,kernel 2.6.15-27-386 (On dev hdc1)

So here is a question or two
Should I re-install Xp and then U64 or should I go back to U32 as I am a learner?
Secondly they are on separate drives, at the mo, is that best or does it no differance?
Or should we carry on as we ar and none of the above makes a differance?

Your call, your the guy that knows best.
JJ

---

### Post by ciscosurfer on 2006-11-03
Let's carry on for the time being.  Before you begin reinstalling things, [try out this thread]("http://ubuntuforums.org/showthread.php?t=217009") that is a HOWTO for NTFS-3G.

It describes how to modify your sources.list to update/grab NTFS-3G through his repository.

When you do go to reinstall your systems, ***this is the order I would install the operating systems***:[LIST=1]
[*]Vista (if you want it)
[*]XP (cuz ya need it?)
[*]Dapper or Edgy -- 32 or 64 bit (download fresh ISOs and install clean from the CD/DVD)[/LIST][LIST]
[*]Install whichever optimized or architecture specific kernel you like (in Edgy, however, they've done away with providing arch-specific kernels right of out the box...but you can always add your own from the repositories...I would just stick with the 2.6.17 kernel they provide, it's called 'generic' and I find that it works the best, and makes use of my dual core)[/LIST]

---

### Post by jjandrj6679 on 2006-11-03
Morning ciscosurfer

Thank you for sticking with me on this one but it didnt work same as yesterday, nothingother than hdc1 & cd in places, they are in my media fils though, but empty.

I followed the instructions letter by letter Jumped to the 64 bit section (new page) then back to section 3 & 4.
Im depressed now. Why doesnt this damn thing wanna play ball?
JJ

---

### Post by jjandrj6679 on 2006-11-03
When doing the whole process again I noticed this on the AMD64 link

"build & install ntfs-3g for amd64"
Code:
cd ntfs-3g-* 
dpkg-buildpackage -rfakeroot 
cd ../ 
sudo dpkg -i libntfs-3g_*.deb ntfs-3g*.deb
------------------------------------------------------------------
josh@josh-desktop64:~$ sudo dpkg -i libntfs-3g_*.deb ntfs-3g*.deb
dpkg: error processing libntfs-3g_*.deb (--install):
 cannot access archive: No such file or directory
(Reading database ... 119857 files and directories currently installed.)
Preparing to replace ntfs-3g 1:0.20061031-BETA-1 (using ntfs-3g_0.20061031-BETA-1_amd64.deb) ...
Unpacking replacement ntfs-3g ...
dpkg: dependency problems prevent configuration of ntfs-3g:
 ntfs-3g depends on libntfs-3g0; however:
  Package libntfs-3g0 is not installed.
dpkg: error processing ntfs-3g (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libntfs-3g_*.deb
 ntfs-3g
------------------------------------------------------------------

I tryed to copy what was going on in the terminal once it had finished each part.
So I did a search for "libntfs-3g" to see if there was anything amiss, it seems to an untrained eye that this libary/lib didnt install?

Let me know what to do 
JJ

---

### Post by jjandrj6679 on 2006-11-03
I also found this lot: I don't know if it makes any sence or matters?

Bareing in mind I have only done stages 1 & 2 here of the added AMD64 link.

josh@josh-desktop64:~/fuse-2.5.3$ dpkg-buildpackage -rfakeroot
(TOP BITS MISSING )
dpkg-source: warning: ignoring deletion of file config.guess
dpkg-source: warning: ignoring deletion of file config.sub

checking for x86_64-linux-gnu-ar... no
checking for ar... ar
checking for x86_64-linux-gnu-strip... no
checking for strip... strip
checking for x86_64-linux-gnu-ranlib... no

checking if x86_64-linux-gnu-gcc supports -fno-rtti -fno-exceptions... no

dpkg-deb: building package `fuse-source' in `../fuse-source_2.5.3-1_all.deb'.
make[1]: Leaving directory `/home/josh/fuse-2.5.3'
 signfile fuse_2.5.3-1.dsc
gpg: skipped "Florent Mertens <flomertens@yahoo.fr>": secret key not available
gpg: [stdin]: clearsign failed: secret key not available
josh@josh-desktop64:~/fuse-2.5.3$

To me there is someting wrong with the fuse install???

If I ignore it and carry on with ntss-3g there are loads of warnings (Off the top of the page) & no sectret key

dpkg-deb: building package `libntfs-3g-dev' in `../libntfs-3g-dev_0.20061031-BETA-1_amd64.deb'.
 signfile ntfs-3g_0.20061031-BETA-1.dsc
gpg: skipped "Florent Mertens <flomertens@gmail.com>": secret key not available
gpg: [stdin]: clearsign failed: secret key not available
josh@josh-desktop64:~/ntfs-3g-0.20061031-BETA$

Again if I ignore and do the next 2 lines I get these warnings

josh@josh-desktop64:~/ntfs-3g-0.20061031-BETA$ cd ../
josh@josh-desktop64:~$ sudo dpkg -i libntfs-3g_*.deb ntfs-3g*.deb
dpkg: error processing libntfs-3g_*.deb (--install):
 cannot access archive: No such file or directory
(Reading database ... 119857 files and directories currently installed.)
Preparing to replace ntfs-3g 1:0.20061031-BETA-1 (using ntfs-3g_0.20061031-BETA-1_amd64.deb) ...
Unpacking replacement ntfs-3g ...
dpkg: dependency problems prevent configuration of ntfs-3g:
 ntfs-3g depends on libntfs-3g0; however:
  Package libntfs-3g0 is not installed.
dpkg: error processing ntfs-3g (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libntfs-3g_*.deb
 ntfs-3g


How can I get the termial to increase its viewable linage?

I hope you can make sence of this.

JJ

---

### Post by givré on 2006-11-03
Stop the flow :cool: 

There were a little change in ntfs-3g package just few minutes ago, now call ntfs-3g0.

I just change the instructions for amd64, redo them from the start, and that should work.
And if it don't work, could you please write the flow in [CODE] balise, this is so much readable, thanks ;)

---

### Post by jjandrj6679 on 2006-11-03
Hi ther
Just to let you know that I have a dual boot of U32 & U64
Just tryed it on U32 and all the drives work

Als you have used phrases that I do not understand. I have been with linux for 2 weeks and so far its 2 weeks of hell...

here were a little change in ntfs-3g package just few minutes ago, 
?????now call ntfs-3g0.?????
I even shouted at the pc and nout happened.. sorry letting off some steam..

I just change the 
?????instructions for amd64?????, 
redo them from the start, and that should work.
And if it don't work, 
?????could you please write the flow in [code] balise,????? 
this is so much readable,

Any help would realy be appreciated 
Id like to smile once this week at least
Greafully yours
Josh

---

### Post by givré on 2006-11-03
jjandrj6679, where did it don't work ?
Also, what i call flow, is the output of command.
You should use the ```
 balise to write them. 
[CODE]Just like that ;) 
```
To do so, just click on the # icone when you write a post.

Thanks.

---

### Post by jjandrj6679 on 2006-11-03
Hi there again
You asked where it didnt work? for me I think it is here-

josh@josh-desktop64:~/fuse-2.5.3$ dpkg-buildpackage -rfakeroot
at the end of it it says
"dpkg-deb: building package `fuse-source' in `../fuse-source_2.5.3-1_all.deb'.
make[1]: Leaving directory `/home/josh/fuse-2.5.3'
 signfile fuse_2.5.3-1.dsc
gpg: skipped "Florent Mertens <flomertens@yahoo.fr>": secret key not available
gpg: [stdin]: clearsign failed: secret key not available
josh@josh-desktop64:~/fuse-2.5.3$"

So I contuued as instucted:-

josh@josh-desktop64:~/fuse-2.5.3$ cd ../
josh@josh-desktop64:~$ sudo dpkg -i libntfs-3g*.deb ntfs-3g*.deb
Selecting previously deselected package libntfs-3g0.
(Reading database ... 119857 files and directories currently installed.)
Unpacking libntfs-3g0 (from libntfs-3g0_0.20061031-BETA-1_amd64.deb) ...
Selecting previously deselected package libntfs-3g-dev.
Unpacking libntfs-3g-dev (from libntfs-3g-dev_0.20061031-BETA-1_amd64.deb) ...
Preparing to replace ntfs-3g 1:0.20061031-BETA-1 (using ntfs-3g_0.20061031-BETA- 1_amd64.deb) ...
Unpacking replacement ntfs-3g ...
Setting up libntfs-3g0 (0.20061031-BETA-1) ...

Setting up libntfs-3g-dev (0.20061031-BETA-1) ...
Setting up ntfs-3g (0.20061031-BETA-1) ...
=================

So has the AMD64 bit worked?
Now I go back to the Previous post and continue with section 3 & 4.

3. Configuration :
Origional FSTAB file which seems to be correct, so no editing... This didnt happen before??

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs-3g defaults,locale=en_US.utf8   0    0
/dev/hdb1       /media/hdb1     ntfs-3g defaults,locale=en_US.utf8   0    0
/dev/hdc1       /media/hdc1     ext3    defaults        0       2
/dev/sda1       /media/sda1     ntfs-3g defaults,locale=en_US.utf8   0    0
/dev/hdc4       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0

So there you have it
I am going to do a restart to see what happens, 1st boot to Xp then to U64

BTW I now have a complete 515 lines of the terminal readout if youd like me to post it or cirtain parts?

Just so I get this into my head, 
"Also, what i call flow, is the output of command." This means the details that follow evry time I write a command like "josh@josh-desktop64:~/fuse-2.5.3$ dpkg-buildpackage -rfakeroot" this is what you call the FLOW yes?

But this bit
"You should use the [code] ???balise???? to write them" 
"Code: Just like that ;)" ???
What's "them?"? The Codes?

Again Im not trying to be a pain its just I dont understand everything, so much to learn is such a small amount of time

Greatfully yours J
JJ

---

### Post by givré on 2006-11-03
```
signfile fuse_2.5.3-1.dsc
gpg: skipped "Florent Mertens <flomertens@yahoo.fr>": secret key not available
gpg: [stdin]: clearsign failed: secret key not available
```
This is ok. You can't sign your packages with my key, but that's ok.

For the installation, it seams to be ok. Tell me it it worked or not.

For the balise stuff, it's just that :

Hi there again
You asked where it didnt work? for me I think it is here-

```
josh@josh-desktop64:~/fuse-2.5.3$ dpkg-buildpackage -rfakeroot
at the end of it it says
"dpkg-deb: building package `fuse-source' in `../fuse-source_2.5.3-1_all.deb'.
make[1]: Leaving directory `/home/josh/fuse-2.5.3'
signfile fuse_2.5.3-1.dsc
gpg: skipped "Florent Mertens <flomertens@yahoo.fr>": secret key not available
gpg: [stdin]: clearsign failed: secret key not available
josh@josh-desktop64:~/fuse-2.5.3$"
```

So I contuued as instucted:-
```

josh@josh-desktop64:~/fuse-2.5.3$ cd ../
josh@josh-desktop64:~$ sudo dpkg -i libntfs-3g*.deb ntfs-3g*.deb
Selecting previously deselected package libntfs-3g0.
(Reading database ... 119857 files and directories currently installed.)
Unpacking libntfs-3g0 (from libntfs-3g0_0.20061031-BETA-1_amd64.deb) ...
Selecting previously deselected package libntfs-3g-dev.
Unpacking libntfs-3g-dev (from libntfs-3g-dev_0.20061031-BETA-1_amd64.deb) ...
Preparing to replace ntfs-3g 1:0.20061031-BETA-1 (using ntfs-3g_0.20061031-BETA- 1_amd64.deb) ...
Unpacking replacement ntfs-3g ...
Setting up libntfs-3g0 (0.20061031-BETA-1) ...

Setting up libntfs-3g-dev (0.20061031-BETA-1) ...
Setting up ntfs-3g (0.20061031-BETA-1) ...
```
=================

So has the AMD64 bit worked?
Now I go back to the Previous post and continue with section 3 & 4.

3. Configuration :
Origional FSTAB file which seems to be correct, so no editing... This didnt happen before??

```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hdc2 / ext3 defaults,errors=remount-ro 0 1
/dev/hda1 /media/hda1 ntfs-3g defaults,locale=en_US.utf8 0 0
/dev/hdb1 /media/hdb1 ntfs-3g defaults,locale=en_US.utf8 0 0
/dev/hdc1 /media/hdc1 ext3 defaults 0 2
/dev/sda1 /media/sda1 ntfs-3g defaults,locale=en_US.utf8 0 0
/dev/hdc4 none swap sw 0 0
/dev/hdd /media/cdrom0 udf,iso9660 user,noauto 0 0
```

than that :
> Hi there again
You asked where it didnt work? for me I think it is here-

josh@josh-desktop64:~/fuse-2.5.3$ dpkg-buildpackage -rfakeroot
at the end of it it says
"dpkg-deb: building package `fuse-source' in `../fuse-source_2.5.3-1_all.deb'.
make[1]: Leaving directory `/home/josh/fuse-2.5.3'
signfile fuse_2.5.3-1.dsc
gpg: skipped "Florent Mertens <flomertens@yahoo.fr>": secret key not available
gpg: [stdin]: clearsign failed: secret key not available
josh@josh-desktop64:~/fuse-2.5.3$"

So I contuued as instucted:-

josh@josh-desktop64:~/fuse-2.5.3$ cd ../
josh@josh-desktop64:~$ sudo dpkg -i libntfs-3g*.deb ntfs-3g*.deb
Selecting previously deselected package libntfs-3g0.
(Reading database ... 119857 files and directories currently installed.)
Unpacking libntfs-3g0 (from libntfs-3g0_0.20061031-BETA-1_amd64.deb) ...
Selecting previously deselected package libntfs-3g-dev.
Unpacking libntfs-3g-dev (from libntfs-3g-dev_0.20061031-BETA-1_amd64.deb) ...
Preparing to replace ntfs-3g 1:0.20061031-BETA-1 (using ntfs-3g_0.20061031-BETA- 1_amd64.deb) ...
Unpacking replacement ntfs-3g ...
Setting up libntfs-3g0 (0.20061031-BETA-1) ...

Setting up libntfs-3g-dev (0.20061031-BETA-1) ...
Setting up ntfs-3g (0.20061031-BETA-1) ...
=================

So has the AMD64 bit worked?
Now I go back to the Previous post and continue with section 3 & 4.

3. Configuration :
Origional FSTAB file which seems to be correct, so no editing... This didnt happen before??

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hdc2 / ext3 defaults,errors=remount-ro 0 1
/dev/hda1 /media/hda1 ntfs-3g defaults,locale=en_US.utf8 0 0
/dev/hdb1 /media/hdb1 ntfs-3g defaults,locale=en_US.utf8 0 0
/dev/hdc1 /media/hdc1 ext3 defaults 0 2
/dev/sda1 /media/sda1 ntfs-3g defaults,locale=en_US.utf8 0 0
/dev/hdc4 none swap sw 0 0
/dev/hdd /media/cdrom0 udf,iso9660 user,noauto 0 0

IMO. To use it just click on # and write your code between the 2 [CODE]

---

### Post by jjandrj6679 on 2006-11-03
It worked this time

If I drill down my FILE SYSTEM into MEDIA they are all there and have all 9 permissions checked and I'm able to edit them as well. Cool at last... But wait whats this?
Now how do I get them to show up in my PLACES MENU &/or my Desktop? As I still only have hdc1 & DVD listed

If I click PLACES/COMPUTER and they are there too. But I'm unable to open them from there? Now thats confusing to the untrained eye, that being mine???

I get this error message

"Unable to mount the selected volume.
mount: according to mtab, /dev/sda1 is already mounted on /media/sda1

mount failed"

So to me there is a light at last after a week of hell.
Love to hear what suggestions that you have

Yours
JJ

---

### Post by jjandrj6679 on 2006-11-03
Oh Ive just got what you mean...lol... about time....lol

"You should use the ```
 balise to write them"

I have to click on the # icon 
("icone" as you spelt it, I thought was a special linux term?? not a mistake, searched all over the net 4 it...lol ](*,) 
Click # and it puts a box round the code I've copied. 
[CODE]
just like this?

```
Ill do that from now on.
Until my eureka this made no sence either
"IMO. To use it just click on # and write your code between the 2 [code]"
So IYO what is the min IQ someone hase to have to worrk with linux, mines over 126 & I have dystlexia & litteracy probs...lol.. more than 126 then.

Now weve sorted that out did you read my last posts about not seeing drives in Places?
Yours
JJ

---

### Post by givré on 2006-11-04
Hi jjandrj6679,

This is a known issue. To resolve the problem, you'll have to install an other package of my repo.

Ok, so here we go :
1. Create a build directory, and work on it :
```
mkdir build
cd build
```
2. Install the needed package :
```
sudo apt-get install debhelper cdbs python python2.4 python2.4-dbus libdbus-glib-1-dev libglib2.0-dev libsysfs-dev libexpat1-dev libpopt-dev pkg-config pciutils libcap-dev doxygen intltool libusb-dev sharutils
```
3. Download the source and build it:
```
fakeroot apt-get source -b hal
```
4. Install everything :
```
sudo dpkg -i *.deb
```

And that's all.

---

### Post by jjandrj6679 on 2006-11-04
Your amazing and I thank you for sticking with me on this one

I am going to reboot my pc on monday so hopefully I can get all we have done up and running without any problems.
But knowing me you will hear from me during the week to let you know if I was successfull or not.
Just one thing, whilst I still need xp for a few things is it IYO best to have xp & linux installed on the same drive or separate drives like they are at the mo, is the a performance gain/decrease..
I wasn't sure so I thought i'd ask you. 
ILFTHFUS
Josh
Ps Thanks again

---

### Post by Sef on 2006-11-04
Be Aware that NTFS-3G is Beta software, so be sure and keep **backing up** your files.  Beta software is still in testing stage, so it may work fine, or it may crash your system.

---

### Post by ciscosurfer on 2006-11-05
@jjandrj6679,

Wow.  Seems like you got some stuff worked out and I'm glad [givré]("http://ubuntuforums.org/member.php?u=85100") was able to help you out (with the AMD64 issues).

I would suggest you reboot now and see if they show up in your Places menu -- they should, but since I don't have or work with AMD or 64 bit, I can't be certain.

@Sef (and potentially, @[givré]("http://ubuntuforums.org/member.php?u=85100") as well),

True, the software is beta, but it keeps getting better and better all the time -- each new iteration building upon itself and gettting more and more solid every time.  And yes, I would agree with you that backing up one's files is important and even more so when you work with beta software...that's a good point for everyone to heed.  While everyone has different hardware and potentially software and versions they are using, and of course, YMMV, I have had wonderful results with NTFS-3G so far -- zero hiccups whatsoever.  Does this mean everyone should use it?  Probably not.  But I've had great success with it and will continue to use it as I consider it a fabulous piece of software for writing to NTFS partitions.  Just my personal thoughts. ;)

---

### Post by jjandrj6679 on 2006-11-06
To all of you that have helped me I am truley thankfull.
Everything is where it should be and that is good. I will reboot my Pc on monday and I will report back with all my successes.
As to the reboot put Xp on one drive and Ubuntu on another or dual boot from one drive
Also Im still new at this do you think that I should start with U32 untill Ive learnt a lot mor about Linux, or does it not realy matter?
I value all of you oppinions, so give it to me straight.

LFTHFUS
Josh

---

