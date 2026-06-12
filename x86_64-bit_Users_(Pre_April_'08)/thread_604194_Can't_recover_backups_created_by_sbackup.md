---
title: "Can't recover backups created by sbackup"
date: 2007-11-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by penguin steve on 2007-11-05
hello everyone, i so far like the sbackup program very much and it works flawlessly doing backups. the problem i encounter is when i try to restore these backups, the program crashes. it creates some weirdly named folder to the place i said it to restore the files to but every time the program locks up and the contents of this mysterious folder are empty. (i have to get root privileges to view the contents). so i noticed the backup is a tar archive so i tried to open it with my archive manager. it took at least 30 minutes for it to read the contents and let me view the files alone. then i tried to extract a single 4MB file and it extracted for ages until i finally gave up. i tried to read the archive from my windows OS with WinRAR and it said the archive is corrupted and would not even let me view the files. anyone know what i can do? am I missing dependencies? I am running Ubuntu 7.04 the 64 bit version. i backup to an external USB 500GB Seagate hard drive formatted to NTFS (so i can see it in windows cause i dualboot) with the ntfs write support tool installed in ubuntu.

thanks for all your help

---

### Post by John Jason Jordan on 2007-11-06
I haven't used sbackup in ages because it was so buggy back when it first came out a year ago with Dapper. However, I note two things:

1) I also had a lot of problems using anything else to copy/transfer large amounts of data over USB. The computer would lock up and/or I'd get corrupted data three out of four tries. I don't recall where I read about it, but evidently the problem was a bug in the Linux USB protocol when writing to hard disks.

2) Being able to write to NTFS is brand new. It's been in development for a long time, but if any component in what you are doing has bugs, I'd bet on the NTFS write support. 

Having said that, I'd try cutting out sbackup first. Use straight tar from the command line to create the archive. If that works reliably, then you know the problem is in sbackup. If not, then you can blame USB transfer protocol or NTFS write support.

---

### Post by penguin steve on 2007-11-06
what do you mean by straight tar? i have had the ntfs write support work flawlessly for over 6 months (when i installed it the first time) and still works perfect copying files to and from the windows partition on the same hard drive as my linux install. The usb seems fine too cause i can copy normal files to my mp3 player and to the external hard disk without any problems with corruption. in fact i dont think i have ever had a corrupted file from simply transferring data to ntfs or through usb. i have been looking at other backup programs but most of them dont offer enough settings as i wish to backup not only my /home folder but also the my documents folders on my windows partition. this way i can run one backup program and it does my whole computer.
any other programs you can recommend? i prefer not to use the command line as i am still fairly new to linux and im not comfortable with it yet.

thanks

---

### Post by John Jason Jordan on 2007-11-06
> **penguin steve said:**
> what do you mean by straight tar? i have had the ntfs write support work flawlessly for over 6 months (when i installed it the first time) and still works perfect copying files to and from the windows partition on the same hard drive as my linux install. The usb seems fine too cause i can copy normal files to my mp3 player and to the external hard disk without any problems with corruption. in fact i dont think i have ever had a corrupted file from simply transferring data to ntfs or through usb. i have been looking at other backup programs but most of them dont offer enough settings as i wish to backup not only my /home folder but also the my documents folders on my windows partition. this way i can run one backup program and it does my whole computer.
any other programs you can recommend? i prefer not to use the command line as i am still fairly new to linux and im not comfortable with it yet.
By "straight tar" I meant doing it from the command line instead of using sbackup. Sbackup is more or less just a set of scripts that call up tar to do its work. The same thing can be done from the command line. You can read up about tar by going to a command line and typing "man tar." However, that brings up the man page, which a lot of beginners might find difficult to comprehend. Man pages are designed as a reference for someone who already understands how the program works and just needs a quick reference when they forgot how to do something. A better option would be to google for a more complete tutorial.

Regarding NTFS, I realize it has been in development for a long time, but Gutsy is the first Ubuntu distribution where NTFS *write* support has been enabled. Being able to write to NTFS has been the last thing that the developers of NTFS access have accomplished successfully. Supposedly it has been thoroughly tested and all the final bugs were resolved before Ubuntu included it in Gutsy. But you and I both know that when software is new there is a greater likelihood of an unforeseen problem. I am not saying for a fact that your problems are due to bugs in NTFS write support. I'm only saying it's near the top of my suspect list. If I were you I would google to see if there are any reports of problems similar to yours. Just remember that NTFS is a proprietary file system and Microsoft does its best to keep people like the open source community from figuring it out. In order to be able to read and write to NTFS partitions the Linux development team had to reverse engineer it. 

Regarding USB, I know for a fact that there were problems in the past when doing large amounts of data transfer to other partitions. I could transfer a couple gigabytes of files without a problem, then suddenly the computer would lock up. Sometimes it would lock up after only a few hundred megabytes of data, but usually it would lock up after an hour or two, when 10-20 GB had been transferred. At the same time I absolutely never had a problem transferring just a few files, nor was there ever a problem with other USB devices like my mouse or my scanner. I mention this because I know the problem existed. What I don't know is if the bug has been fixed. I suggest this only because your symptoms seem to match what happened to me.

---

### Post by penguin steve on 2007-11-06
ok thanks for your help i will try to backup and recover a backup saved on the same hard drive but on a fat 32 partition. if i can recover the backup, it is the NTFS or USB causing me the problem, if i cant recover the backup it is the program. i will therefor be looking for a different program.

i will post my results shortly.

---

### Post by penguin steve on 2007-11-06
thank you for helping me out, i successfully recovered my backups from my fat 32 partition. just to test if it really worked i recovered a 1GB directory no problem. now i just have to figure out how to get it on my external drive without getting it corrupted. 
do you know ways i could test to see if its the usb or the ntfs the problem? if its the ntfs i could format my external drive to fat 32 but i dont really want to do that as it fragments easily. any other filesystem you can suggest that linux and windows can read and write to natively?

thanks again

EDIT: i am currently doing a backup to my windows partition. if i can recover it the problem is with the usb.

EDIT 2: the problem is USB. now to fix it.....is another story. i will see if i can find patches.

EDIT 3: ok now for some unknown reason, the backups on my external USB Hard drive formatted to NTFS are now recoverable. as i click the button to initiate the process, the program fades to gray meaning its unresponsive but my system monitor shows there is activity going on. so i let it go and then the activity ended and the program came back to normal. then i checked the folder with the recovered data and it was all there and functional. I appreciate your help very much and it now seems the problem is fixed. i dont know what i did really so i cant comment on what to do for others who may have the same problem. i am now really glad this program works because its exactly what i needed.

---

### Post by sawjew on 2007-11-08
Just a suggestion for you.  Check out pybackpack as a backup tool, it's available in the repositories for Gutsy.  It has several advantages over sbackup;
[LIST]
[*]It can backup to removable drives such as cdrs or dvdrs
[*]It uses a standard tar.gz format for its backups so you can access your archives without having it installed
[*]I have found it to be considerably faster than sbackup
[/LIST]

Just check it out.  If you are not using Gutsy it is available from [here]("http://projects.sucs.org/projects/pybackpack/")

---

### Post by penguin steve on 2007-11-08
thankyou, i have downloaded the tar but i dont really know how to install it. do you know what commands i can use to add the repositories and then do a apt-get install? im not sure the tar i downloaded from the web site is 64 bit compatible either.

EDIT: i noticed this tarball i downloaded is the source code only and it says i the program is available from my favorite gutsy mirror. im not using gutsy so a link for the repository is appreciated.

---

### Post by sawjew on 2007-11-08
You should be able to compile the source code for 64 bit and use checkinstall to install it and it will create a deb package but an easier way may be to go [here]("http://linuxappfinder.com/package/pybackpack") and try the debian package.  It will probably work alright.  Sorry I thought they would have debs available and I didn't realise it would be such an issue to obtain debs for earlier versions of ubuntu.

There is another option and that is to backport it from the gutsy repositories yourself using prevu.  If you search the forums you should find some help on prevu but in short here is how it goes.

[LIST=1]
[*]sudo apt-get install prevu
[*]in a terminal type "prevu" and it will set itself up
[*]then enter "prevu pybackpack" and it will download the sourcecode from the gutsy repository and compile it for you distribution
[/LIST]

This is a great tool.  It doesn't work for everything but I backported quite a few things to Feisty before Gutsy was released.

Just search the forums for "prevu" for some more info.  I had better get back to work now, good luck.

---

### Post by sawjew on 2007-11-08
Here is a link with how to use prevu to backport newer packages [http://ubuntuforums.org/showthread.php?t=268687&highlight=prevu]("http://ubuntuforums.org/showthread.php?t=268687&highlight=prevu")

---

### Post by penguin steve on 2007-11-08
thanks for the link, i installed prevu no problem but when i type "prevu pybackpack" it searches and then asks me if im sure the package exists (cant find it). what commands can i type to compile the source code i downloaded? i looked but i dont know how to do it. while searching i found NSsbackup ("not so simple backup" which is a fork of sbackup) and also TimeVault. these look like some nice alternatives. i will give TimeVault a try as i like the snapshot idea and the nautilus integration.

---

### Post by John Jason Jordan on 2007-11-09
> **penguin steve said:**
> thanks for the link, i installed prevu no problem but when i type "prevu pybackpack" it searches and then asks me if im sure the package exists (cant find it). what commands can i type to compile the source code i downloaded? i looked but i dont know how to do it. while searching i found NSsbackup ("not so simple backup" which is a fork of sbackup) and also TimeVault. these look like some nice alternatives. i will give TimeVault a try as i like the snapshot idea and the nautilus integration.
For a long time I have been searching for a good backup solution. Simple backup is too buggy. I recently tried pybackup and home user backup, but neither could write to my dual layer DVD drive. I can't find nssbackup, and TimeVault seems to be available only in a 32-bit version. And both seem to be in beta testing still. All the rest of the backup solutions I have found are designed for backing up thousands of Windows machines to a central server. Isn't there something that actually works for a home user to back up their computer? Is it not time for Linux on the desktop to come up with a backup solution?

Edit: I also just tried Keep, a KDE backup manager that describes itself as for the simple user. When I tried to back up to my DVD drive it said "Fatal Error: Destination /media/cdrom exists and is not a directory." Well, duh! I uninstalled it.

---

### Post by sawjew on 2007-11-09
**penguin steve**
There is one step I omitted to tell you to use prevu, you need to add the gutsy source repositories and it will download the gutsy source and compile it for your running system.  If you go to the link I posted on how to use prevu it should help.  Otherwise try the debian packages in my previous post.  So far I haven't found anything easier to use than pybackpack so give it  whirl if you can.

If you want to compile the source code you downloaded first you need the tools for compiling code;
```
sudo apt-get install build-essential linux-headers-`uname -r` checkinstall
```

Then you can right click on the source archive and extract it.

You then need to enter the extracted directory and open a terminal in that directory.

you should then be able to run these commands;
```
./configure
make
sudo checkinstall
```

this should compile the code into a binary, install it and create a debian package.

You should have a deb package in this directory which you can keep to reuse if you ever need to reinstall the application and you can now remove it using apt-get or synaptic if you need to.

Sorry if this sounds too complicated but you should be able to cope if you have used slackware before.

**John Jason Jordan**
I agree, linux is in desperate need of a reasonable backup solution but it will come.  At the moment I have found pybackpack to be one of the best but it doesn't write to dual layer dvds.  I don't know of any backup solution that can write to dual layer dvds.  One excellent backup solution I used to use regularly was backup-manager.  This is a command line backup tool that you just set up your configuration file, which is well documented, then forget about it.  It was great when I was using a desktop computer with a second hard drive for backup but it is nowhere near as useful on my laptop where I need removable drives to backup too.  There are commercial backup tools for linux that you have to pay for if you really want something better.  Keep searching, let us know if you find anything decent.

---

### Post by John Jason Jordan on 2007-11-10
> **sawjew said:**
> **John Jason Jordan**I agree, linux is in desperate need of a reasonable backup solution but it will come.
And what can I do in the meantime? My new laptop has a dual layer DVD. It is working fine. But I can't find any backup utility that recognizes it. I have tried backup2l, backup-manager, cdbackup, cedarbackup2, hubackup, keep, multicd, pybackpack, sbackup and simplebackup. I'm on 64-bit Gutsy, but I could figure out how to compile from source if necessary. The programs I have tried don't just fail to write dual layer, they don't see the drive at all. They all fail when it comes time to start writing the DVD. And some of them are so buggy I can barely launch them.

So far I am using a 1 GB USB flash drive to copy files to another computer. My ~/ folder has 16 GB of files. This just sucks. I'd pay money for a commercial solution, but there are none. All the commercial backup utilities are designed to back up hundreds of Windows clients to a Linux server.

Ubuntu has a great motive: Get Linux on the desktop. But lack of a backup solution that works may drive me back to Windows. <Gag>

---

### Post by penguin steve on 2007-11-10
John Jason Jordan
i think that backing up to DVDs automatically will take some time before being supported. why dont you just create backups and save them to your hard drive then burn them manually. there has to be human intervention to insert the DVD-R anyway so i dont see how this process will become automated anytime soon. the only automated part would be notifying you that it is time to do a backup and tell you to insert writable optical media. if you understand what i mean, backing up to dvds would be just like doing a manual backup anyway.

Sawjew
thanks for the code, its not intimidating at all to me. i have come to know a little what im doing in the terminal and i know what some basic commands mean and do. i also realize i need the gutsy repositories for pybackup but i do not know where to find the link to it so i can add it. can someone running gutsy post the link to their main Ubuntu repository please?
____

NSsbackup --> [https://launchpad.net/nssbackup/](https://launchpad.net/nssbackup/)
___

I installed TimeVault and so far i dont like it. its buggy and the nautilus integration is broken. maybe it only works on 32 bit. I also found a similar program to TimeVault called Flyback. i have installed it but have not had the chance to test it yet. i will post my thoughts soon.

keep the input coming!

---

### Post by sawjew on 2007-11-11
penguin steve

You should be able to use this for your gutsy repository to use with prevu

```
deb-src http://archive.ubuntu.com/ubuntu gutsy main restricted universe multiverse
```

Maybe we need to start a thread discussing backup software available and get contributions regarding their effectiveness or otherwise.  I think it could be very useful for a lot of people.  maybe a wiki page would be better still.

---

### Post by John Jason Jordan on 2007-11-11
> **sawjew said:**
> Maybe we need to start a thread discussing backup software available and get contributions regarding their effectiveness or otherwise.  I think it could be very useful for a lot of people.  maybe a wiki page would be better still.
I think that's an excellent idea. There are tons of web resources relating to backing up Linux and using Linux for backups. Almost all of them are geared to people administering huge networks where they need to back up workstations to a central server. That's wonderful, but Ubuntu is all about the desktop. (And my hat is off to Ubuntu for it!) Therefore, an Ubuntu wiki about how to back up a single user machine would be a great tool and save a lot of forum bandwidth.

---

### Post by sawjew on 2007-11-14
Just thought I'd let you know that there is a wiki page on backup solutions [here]("https://help.ubuntu.com/community/BackupYourSystem") but it is not particularly complete.  If you know of any other solutions you could maybe add them here or at least link to them here.

---

### Post by John Jason Jordan on 2007-11-15
> **sawjew said:**
> Just thought I'd let you know that there is a wiki page on backup solutions [here]("https://help.ubuntu.com/community/BackupYourSystem") but it is not particularly complete.  If you know of any other solutions you could maybe add them here or at least link to them here.
I don't know of any beyond what has  been described here or on the web site you quoted. However, there is a local friend of mine who has sort of taken over dirvish, since the author drowned in a California lake a couple of years ago. The friend is going to help me get dirvish working. It's command line only and runs from a config file, so I need help getting it set up. It's based on rsync.

I tried simple backup and not so simple backup, but they fail when trying to back up to a network share. For that matter, they fail when trying to back up to a DVD. Pretty useless, if you ask me.

---

### Post by Cariboo1938 on 2007-12-01
> **penguin steve said:**
> hello everyone, i so far like the sbackup program very much and it works flawlessly doing backups. the problem i encounter is when i try to restore these backups......
Hello penguine steve,
you marked this thread as [SOLVED] and I can't figure out how you did it. I read through all the posts but, maybe because I'm a bit slow today, I could not find the solution for the 'Simple backup Restore' issue. In my case the backed up file, which is located in /var/backup does not even show up in the restore menu (see attachment). It seems to me that you SOLVED the issue by not using the SBackup Restore program at all, am I right?
Otherwise maybe you or someone who reads this can give further details.
Thanks

---

### Post by penguin steve on 2007-12-01
im sorry, the reason i marked it solved is because sbackup started working all of a sudden. i think i was a little impatient with the program. i waited longer for it to do the job and it started to work. i still use sbackup but there is definitely a need for improvement. i have tried several other programs and they just dont seem to do enough or they are more buggy than sbackup.

should I remove the mark as solved?

---

### Post by Cariboo1938 on 2007-12-01
> **penguin steve said:**
> I'm sorry, the reason i marked it solved is because sbackup started working all of a sudden. i think i was a little impatient with the program. i waited longer for it to do the job and it started to work. i still use sbackup but there is definitely a need for improvement. i have tried several other programs and they just dont seem to do enough or they are more buggy than sbackup.
should I remove the mark as solved?Hi penguin steve,
Thanks for the response...I wonder if the restore part is working for you? 
If you look at my screenshots you can see that the restore part of the program does not recognize the location /var/backup with the backup file in it. 
What is wrong? Do I need to change some settings? I have no clue!

> **penguin steve said:**
> should I remove the mark as solved?
If it works for you can leave it [solved] as long as you are happy with it. 
For me it is not solved and I need certainly some help here. 
Maybe I should open another thread?:confused:

---

### Post by penguin steve on 2007-12-01
try to use "use custom location" and navigate to /var/backup. maybe its just a bug but i don't know cause i never used the default location.
if that does not work, i will remove the solved mark for you because it is indeed part of this subject "Can't recover backups created by sbackup"

---

### Post by Cariboo1938 on 2007-12-02
Thanks penguin steve for the reply...
I reported a bug, because it just doesn't work. Maybe it's not a bug but a question of setting...
I don't know yet...It's not solved for me...

---

### Post by penguin steve on 2007-12-02
I removed the Solved mark.

maybe if you do backups in a different location such as on a separate partition or drive and tried to recover them from there. you might then have success. for me, i have to click on the drop down menu to see the available backups i can recover in the location i specified. otherwise, nothing shows.
thats about all i can help you with. maybe someone else knows how to fix that.

---

### Post by Cariboo1938 on 2007-12-02
> **penguin steve said:**
> I removed the Solved mark...........

Thanks penguin steve....I keep this thread alive until I find a solution. I keep you posted.
Cariboo:popcorn:

EDIT:
Hello penguin steve
Sorry for bothering you with this...You can put back the SOLVED mark again. 
Restore works here too. 
I didn't realize that I have to click twice at the arrow right of the empty field by the text line "Available backups:" to see the backup files.
I'm so sorry for being so stupid.
Thanks again for you patience and help and 
Merry Christmas:lolflag:

---

