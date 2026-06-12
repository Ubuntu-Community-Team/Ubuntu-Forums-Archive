---
title: "are there any good ubuntu backup programes"
date: 2006-04-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by cosmoshell on 2006-04-22
are there any good ubuntu backup programes. so if i realy screw up my machine i wont have to re configure the whole thing.

---

### Post by bryanl on 2006-04-22
there are, as always, a ton of options and choices. I have problems trying to keep things simple and trying to keep archive file sizes within reason. And there are the usual problems of backup media and scheduling and backup set aging. It can get complicated.

What I did was to add a second hard drive on a different controller to keep it as independent and separate from the primary drive as I could but still be on the same machine. It was the backup drive. I then used rsnapshot - I still need to automate its scheduling via cron.

rsnapshot uses rsync and cp and the fact that cp can create hard links to make a series of backup images without taking up a whole lot more room than just the current backup. Here's a howto
[http://rsnapshot.org/howto/1.2/rsnapshot-HOWTO.en.html](http://rsnapshot.org/howto/1.2/rsnapshot-HOWTO.en.html)
It will also backup over a network using SSH. The basic one machine setup is a matter of editing a config file and turning it loose. 

Some also recommend Simple Backup. I haven't installed that to see what it takes but initial overview makes me think rsnapshot is simpler.

I have also used partimage as that is on a lot of live CD's. It is a good way to get a partition image backup for either linux or windows boot partitions.

All of these are readily available from the usual suspects.

---

### Post by John Jason Jordan on 2006-04-22
[QUOTE=cosmoshell]are there any good ubuntu backup programes. so if i realy screw up my machine i wont have to re configure the whole thing.[/QUOTE]
I keep looking, but backup solutions for single users with standalone machines on Linux pretty much suck. I know all the Linuxoids are going to jump all over me for that statement, but it's true. Linux has awesome utilities for backing up hundreds of user workstations in a huge organization, but for those of us using Linux on the desktop, backups are an afterthought for the Linux coders.

Someone at a local Linux group taught me how to use dump from the command line. I used it for quite a while until one day it totally screwed me up. During the backup something locked up gnome and I had to hit the power button to get out. When I restarted I couldn't log in because the hard disk was full -- and the error message was correct -- dump had restarted itself on rebooting, but since the external hard disk it had been backing up to before was no longer available, it went about its merry way backing the entire hard disk up to the hard disk. I had to boot to a live CD, then go in and delete the backup files before I was finally able to get my computer back. That was the end of dump for me.

I've also been told by many people to use rsync. Every time someone tells me to use rsync I ask them to explain what syntax I should use to make the backup to my external USB drive on an as-needed basis. That is always the end of the conversation. They recommend it, but cannot explain how to use it.

I tried Simple Backup, but it has too many bugs and doesn't work most of the time.

Finally I hit on Kdar, part of the KDE suite. It works just great -- exactly what I need for now and again backups on an as-needed basis. Unfortunately, on my 64-bit Breezy laptop it locks up the machine about one backup out of three. I have no idea why. I've started it from the command line to see if it would generate an error message when it locks up the computer, but no error messages are generated. I've asked here and on KDE forums and never had a response. I still use it in spite of its bad behavior, just because there is nothing else.

One thing I did learn in all this is that with Linux, as long as you follow the standard procedure of storing your data files in your home folder, that is all you need to back up. Programs that you have installed place their config files in your home folder as well. So if you have a backup of everything (including hidden files) in your home folder, and disaster strikes, you can reinstall Linux and all your programs, then restore your home folder from your backup, and things should be exactly as they were. Theoretically. Or so everyone tells me. (Knocking on wood, throwing salt over shoulder, crossing fingers, etc.)

---

### Post by nwillis on 2006-04-24
I recommend sbackup (simple backup) -- [sbackup.sf.net]("http://sbackup.sf.net")

It is very straighforward, and despite being dismissed (without details...) by previous posters you will find it far easier to use than 70's-era Unix command line tools.  It has an easy to use GUI, it runs without interference, and is much simpler to configure, and will work three times out of three (unlike KDar).  Another advantage is that the backups it creates are easier to browse and extract data from.  Plus you don't have to install KDE.

[http://www.linux.com/article.pl?sid=05/11/22/2110251]("http://www.linux.com/article.pl?sid=05/11/22/2110251")

---

### Post by John Jason Jordan on 2006-04-24
[QUOTE=nwillis]I recommend sbackup (simple backup) -- [sbackup.sf.net]("http://sbackup.sf.net")

It is very straighforward, and despite being dismissed (without details...) by previous posters you will find it far easier to use than 70's-era Unix command line tools.  It has an easy to use GUI, it runs without interference, and is much simpler to configure, and will work three times out of three (unlike KDar).  Another advantage is that the backups it creates are easier to browse and extract data from.  Plus you don't have to install KDE.[/QUOTE]
But it won't make a backup to an external USB drive. In fact, it's default location for the backup is on the same disk that you are backing up! How useful is that? Like what if your disk is getting kind of full? Plus, even if you have space, then you have to take the extra step to move the backup file to your external drive or burn it to DVDs. 

And if that is not enough, it also fails to run most of the time. I tell it to make the backup and it sits there and does nothing at all. No error messages, no way to figure out what is wrong. Did I put some wrong entry in one of the boxes? Is it a bug? Who knows?

It's a good idea, but it needs lots of work. Maybe there will be a better version when Dapper comes out.

---

### Post by skylark on 2006-04-24
I have to admit I don't have a proper backup solution either. I do try to use version control for many files and my HDDs are setup on different controllers using software RAID-1. So except for some files I backup to CD/USB drive every now and then I don't really have much protection against an "rm -rf *.*", but at least I have some protection against a HDD failure.

I've heard rdiff-backup is good for backing up to external USB HDDs [http://www.nongnu.org/rdiff-backup/](http://www.nongnu.org/rdiff-backup/) but I haven't looked into it.

For awhile I've been considering setting up a file server and using a proper backup solution like Bacula [http://www.bacula.org/](http://www.bacula.org/) , Amanda [http://www.amanda.org/](http://www.amanda.org/) or Backup PC [http://backuppc.sourceforge.net/](http://backuppc.sourceforge.net/) I'm sure I'll get around to it one day!

---

### Post by nwillis on 2006-04-25
> **John Jason Jordan]But it won't make a backup to an external USB drive. In fact, it's default location for the backup is on the same disk that you are backing up! How useful is that? Like what if your disk is getting kind of full? Plus, even if you have space, then you have to take the extra step to move the backup file to your external drive or burn it to DVDs. [/QUOTE]

This is just not true.  The default location is on the same *filesystem* as the *filesystem* you are backing up, and that is because it is designed for single-machine usage (hence the name).  How useful is that?  That's real useful.  Besides, /var should not be on the same partition (or even disk, if you can afford it) as / or /home anyway, and "what if your disk is getting full" is a problem not specific to your backup software.

And one of the things that makes sbackup useful is that it is so straightforward to change the defaults.  The preference pane has three choices: use default backup directory (/var/backup), use custom local backup directory, and use a remote directory (ssh or ftp).  How much simpler could it get?

And duplicating/burning to external storage is a necessary part of every good backup strategy.  Depending on a magnetic storage device only (USB or otherwise, and I don't use a USB drive for my backups, but I have searched the bug tracker and I don't see any evidence from users having problems with external storage devices as their target) is not recommended because power problems can still kill your device.  You need at least one optical copy as well.

[QUOTE=John Jason Jordan]And if that is not enough, it also fails to run most of the time. I tell it to make the backup and it sits there and does nothing at all. No error messages, no way to figure out what is wrong. Did I put some wrong entry in one of the boxes? Is it a bug? Who knows?[/QUOTE]

Not to put too fine a point on it, but this is what the excellent support forums and mailing lists are for!!!  Is it a bug?  You can find out if you ask the people who develop the program.  The short answer is well, yeah, I guess if you are having problems with it, then it sounds like you have found a bug.

But that's no reason to act like one user's bug outweighs the program's usefulness for all of the users who are *not* experiencing your bug said:**
> It's a good idea, but it needs lots of work. Maybe there will be a better version when Dapper comes out.

I think we can all agree about that last one.

---

### Post by rplantz on 2006-04-26
[QUOTE=John Jason Jordan]I
I've also been told by many people to use rsync. Every time someone tells me to use rsync I ask them to explain what syntax I should use to make the backup to my external USB drive on an as-needed basis. That is always the end of the conversation. They recommend it, but cannot explain how to use it.
[/QUOTE]

There's a pretty good discussion of using rsync here:
[http://www.mikerubel.org/computers/rsync_snapshots/](http://www.mikerubel.org/computers/rsync_snapshots/)

Following his suggestions, I came up with the following script to make rotating snapshots:```

#!/bin/bash

unset PATH      # suggestion from H. Milz: avoid accidental use of $PATH

# ------------- system commands used by this script --------------------
ID=/usr/bin/id
ECHO=/bin/echo

RM=/bin/rm
MV=/bin/mv
TOUCH=/bin/touch

RSYNC=/usr/bin/rsync

# ------------- file locations -----------------------------------------

SNAPSHOT_DISK=/media/usbdisk
EXCLUDES=backup_exclude


# ------------- the script itself --------------------------------------

if [ -d $SNAPSHOT_DISK/ubun.3 ] ; then
   /usr/bin/sudo $MV $SNAPSHOT_DISK/ubun.2 $SNAPSHOT_DISK/ubun.tmp
   echo "Created ubun.tmp"
fi
 
# step 2: shift the remaining snapshots(s) back by one, if they exist
if [ -d $SNAPSHOT_DISK/ubun.2 ] ; then
   /usr/bin/sudo $MV $SNAPSHOT_DISK/ubun.2 $SNAPSHOT_DISK/ubun.3
   echo "Created ubun.3"
fi

if [ -d $SNAPSHOT_DISK/ubun.1 ] ; then
   /usr/bin/sudo $MV $SNAPSHOT_DISK/ubun.1 $SNAPSHOT_DISK/ubun.2
   echo "Created ubun.2"
fi

if [ -d $SNAPSHOT_DISK/ubun.0 ] ; then
   /usr/bin/sudo $MV $SNAPSHOT_DISK/ubun.0 $SNAPSHOT_DISK/ubun.1
   echo "Created ubun.1"
fi

# step 4: rsync from the system into the latest snapshot (notice that
# rsync behaves like cp --remove-destination by default, so the destination
# is unlinked first.  If it were not so, this would copy over the other
# snapshot(s) too!
if [ -d $SNAPSHOT_DISK/ubun.1 ] ; then
   echo "Creating ubun.0 based on ubun.1 on $SNAPSHOT_DISK"
   /usr/bin/sudo /usr/bin/time $RSYNC         \
        -v -a --delete  \
        --link-dest=$SNAPSHOT_DISK/ubun.1    \
        /home/bob/ $SNAPSHOT_DISK/ubun.0/
else
   echo "Creating a new ubun.0 on $SNAPSHOT_DISK"
   /usr/bin/sudo /usr/bin/time $RSYNC         \
        -v -a --delete             \
        /home/bob/ $SNAPSHOT_DISK/ubun.0/
fi
$ECHO "rsync exit code is "$?
# step 5: update the mtime of ubun.0 to reflect the snapshot time
$TOUCH $SNAPSHOT_DISK/ubun.0 ;

```

I'm sure it can be improved, but it has worked well for me.

---

### Post by paritybit on 2006-04-26
sbackup is pretty bad but has a lot of potential.
No progess meter, doesn't do half the things it says (can't save to ssh, ftp anything like that) only local backup. 
Hopfully they make this tool really good for the final dapper release.

---

### Post by new2ub on 2006-04-26
[QUOTE=cosmoshell]are there any good ubuntu backup programes. so if i realy screw up my machine i wont have to re configure the whole thing.[/QUOTE]
Yes there are and most of them are free. On the upper right hand corner of your Mozilla Firefox Browser is Google. Type in "Linux Backups" and hit enter. The result will be enough to satisfy any geek.
Specifically it all depends on what kind of dependability you need.
For bare metal (start at zero) restoring I have found "partimage" to be very good. However this Linux program will ultimately takes up a lot of room on your backup disk. For Incremental backups "rsync" and "DAR" (or "KDAR") may be for you. Rsync is already installed on Ubuntu 5.10 but DAR or KDAR you have to download with apt-get.
I am from the old school that says NEVER backup a Live System.
Partition Image is found on 2 different rescue CDs: System Rescue CD and the other is R.I.P. (recovery is possible). You have to download "systemrescuecd" and "R.I.P." from a internet site and burn them. You then run "partimage" from them. Partition Image is a hard disk partition Imager just like what Norton Ghost does to Winblows partitions. It works on any Linux, FAT32, FAT file system and 32 or 64 bit system. It also restores all above.
Both "rsync" and "kdar" (dar) failed the "bare metal" test on my system but it might work for yours.
As usual before backing up run Linux commands "fsck /dev/sda#"
or "dosfsck /dev/sda#" (where "#"= partition number) BEFORE mounting. The following commands should be done right now :
     1. Save mbr.
     2. Save partition table.
Read the documentation for System Rescue CD for both save and restoration of mbr and partition table.
:mrgreen:

---

### Post by John Jason Jordan on 2006-04-27
[QUOTE=new2ub]I am from the old school that says NEVER backup a Live System.[/QUOTE]
I understood little of what you said, but that's OK. I understand that I should not be allowed to run Linux, because I am a n00bie and I am running it just on one standalone computer. Worse, I have no degree or knowledge of computer science, have never tried to program and, even worse yet, have no desire to do either of those things. I just want to run Linux on a desktop like a (gasp) *user*. If my existence offends, I apologize in advance.

I have a couple questions, though.

1) What is a "live" system? If the computer is booted and the OS is running, is it not "live"? How could you back it up if it wasn't running? There must be another meaning for "live" system.

2) Is Kdar a front end for Dar? If so, I never realized that. Once you mentioned Dar I went into Synaptic and lo and behold -- it is already installed. But I don't remember installing it. So it must have been installed by Kdar. If this is correct, then is there a gnome-based front end for Dar? Or any other front ends for it?

---

### Post by rplantz on 2006-04-28
[QUOTE=John Jason Jordan]But it won't make a backup to an external USB drive. In fact, it's default location for the backup is on the same disk that you are backing up! How useful is that? Like what if your disk is getting kind of full? Plus, even if you have space, then you have to take the extra step to move the backup file to your external drive or burn it to DVDs. [/QUOTE]

I have used sbackup very little, but it saved me once. I was playing with it to see how it worked. Actually, you can backup to an external USB drive. I did it. Just go to the Simple Backup Config program and click on the "Destination" tab. Choose "Use custom local backup directory" and it will find your external USB disk (assuming you have it connected and running). At least it did for me.

After using sbackup, I did something really, really stupid and deleted my entire home directory. (Not only that, I had just read a post that warned people not to do what I did.) Anyway, sbackup restored everything flawlessly.

Admittedly, n = 1 in my experiment, but it certainly saved the day for me.

---

### Post by duality on 2006-04-28
yes there are,, use LVM2 and mirror your partition.... its probably the best way,, then if something messes up just point grub to the mirrored partition and you got your "saved ubuntu installation" running in a matter of minutes.

It may take some time to learn how to do this though =/

Now creating snapshots can be done with EVMS too with probably is the best way of making snapshots of the partitions.

for the other stuff just have your home directory (or wherever you store your stuff) in yet another partition and it will not be affected by changing the system.


I dont think using rsync is any good idea because it can break your system.

You dont need to have any degree in computer science, doing backups and backups to save the system should be made more clear to the users as this is verry essential for using linux.

---

### Post by rplantz on 2006-04-28
[QUOTE=duality]
It may take some time to learn how to do this though =/
[/quote]

I just glanced at the manual for evms. It looks fairly involved.

> 
I dont think using rsync is any good idea because it can break your system.


How so? I'm not trying to argue here. I'm "agnostic" regarding backup programs and am simply trying to learn more.

> 
You dont need to have any degree in computer science, doing backups and backups to save the system should be made more clear to the users as this is verry essential for using linux.
Or any OS. From the research that I've been doing for the past few months on backups, I'm amazed at how complex it is. And I have seen complaints about essentially all the backup programs having bugs -- from the "free" ones included with an OS installation to the very expensive commercial ones. I think that bugs in a backup program fall into the category that was well-stated by a friend some years ago: "Brain surgeons don't say 'oops'."

---

### Post by new2ub on 2006-04-28
[QUOTE=John Jason Jordan]I understood little of what you said, but that's OK. I understand that I should not be allowed to run Linux, because I am a n00bie and I am running it just on one standalone computer. Worse, I have no degree or knowledge of computer science, have never tried to program and, even worse yet, have no desire to do either of those things. I just want to run Linux on a desktop like a (gasp) *user*. If my existence offends, I apologize in advance.

I have a couple questions, though.

1) What is a "live" system? If the computer is booted and the OS is running, is it not "live"? How could you back it up if it wasn't running? There must be another meaning for "live" system.

2) Is Kdar a front end for Dar? If so, I never realized that. Once you mentioned Dar I went into Synaptic and lo and behold -- it is already installed. But I don't remember installing it. So it must have been installed by Kdar. If this is correct, then is there a gnome-based front end for Dar? Or any other front ends for it?[/QUOTE]

Your guess is right on "live system". It simply means the one that you are operating with at the moment.
How do you backup any Operating System? Easy - with another one. The Linux backup program Partition Image("partimage") is usually done with one of two CDs. You simply download their .ISOs, burn them to CD then boot them. These CDs have their own Operating System apart from others. The only requirement "System Rescue CD" and R.I.P. (recovery is possible)CDs is that the target (the backup disk in which the backup file is going to) is mounted and enough space is available.
As far as "kdar" is concerned it is derived from "dar" and "tar". Both dar and tar are something out of a UFO. They have options to suboptions to more options to which only a super geek would understand. KDAR or "kdar" is a nice graphical interface that makes all them options better put. You should at least try it by doing this:
     1. Hit Applications > Accessories > Terminal then <enter>.
     2. In Terminal type "su". Type in password for su.
     3. Get access to the Internet.
     4. While still in Terminal type in "apt-get install kdar" (without the quotes).
     5. Still in Terminal and after install type in "kdar". You should get a blue logo then after a short time "kwallet" will show up. Go ahead if you havent done kwallet before you should know that it is just another layer of security. Put in another password that you can remember. Once that is done that nice gui for kdar will show up.
Go ahead explore it !

---

### Post by duality on 2006-04-29
ive tried using rsync once and it didnt work that well (i did something wrong for sure) seince kdar is also using rsync, and kdar works verry well ,. You can also make an exact copy of your root partition by booting the ubuntu install and copying the partition at "partitioning" stage of the installation, there is a "copy partition" option. (you may need to activate the groups if you use LVM, wich is also done from the same menu)

---

### Post by John Jason Jordan on 2006-05-01
First, thanks to all the Linux gurus who have chimed in here. In my case, none of the suggestions are usable. But I appreciate the comments, and others may benefit anyway.

I have one computer. It must be backed up "live" because otherwise it can't be backed up at all. I can't back it up from another computer because there is no other computer. Bear in mind my earlier kvetch about Linux backup utilities -- there are tons of them and practically none for the individual user. All are designed for big organizations with lots of individual workstations being backed up to a big server somewhere in the sky. Ain't gonna happen in my world.

I do use Kdar to back up to my external USB pocket drive. It works, but locks up a lot. I just heard a complaint from a user on a local Linux e-list that his external USB drive caused lots of similar problems until he replaced it with a different brand. Evidently there are issues with USB. So right now I am considering that blaming Kdar for the lockups may have been unwarranted. The problem might be with USB and the pocket drive. I may owe Kdar an apology. 

Nevertheless, there is a serious paucity of backup utilities for a user such as me.

---

### Post by chalex on 2006-05-11
[QUOTE=John Jason Jordan]It must be backed up "live" because otherwise it can't be backed up at all. [/QUOTE]

I think people mean booting from a LiveCD, mounting your partitions read-only and copying them somewhere.  That way you're not writing something to disk while you're backing up.

> 
Nevertheless, there is a serious paucity of backup utilities for a user such as me.

I think you're just trolling.  What exactly is wrong with [sBackup]("http://sbackup.sourceforge.net/HomePage")?  What's wrong with [rsync]("http://www.mikerubel.org/computers/rsync_snapshots/")?  Both are easy to use and the former is designed specifically for a user such as you.  

If you want something even simpler, what's wrong with "cp" or "tar"?

---

### Post by paritybit on 2006-05-11
[QUOTE=chalex]
I think you're just trolling.  What exactly is wrong with [sBackup]("http://sbackup.sourceforge.net/HomePage")?  What's wrong with [rsync]("http://www.mikerubel.org/computers/rsync_snapshots/")?  Both are easy to use and the former is designed specifically for a user such as you.  

If you want something even simpler, what's wrong with "cp" or "tar"?[/QUOTE]
Sorry, but sBackup doesn't do half the things it says it does, doesn't have progress indication or anything like that. Has a lot of potential but is pretty crap. 
cp and tar aren't great at backups, I have had quite a few problems using tar to make backup with corrupt archives.
rsync is not an 'easy' solution. It would be a correct statment to say that there aren't a great deal of simple, user orientated backup programs but it appears there are some on the way.

---

### Post by rickyjones on 2006-05-13
[QUOTE=paritybit]Sorry, but sBackup doesn't do half the things it says it does, doesn't have progress indication or anything like that. Has a lot of potential but is pretty crap. 
cp and tar aren't great at backups, I have had quite a few problems using tar to make backup with corrupt archives.
rsync is not an 'easy' solution. It would be a correct statment to say that there aren't a great deal of simple, user orientated backup programs but it appears there are some on the way.[/QUOTE]

I've got to agree - I just tried testing out simple backup, and after telling it to backup to my FTP site, and hitting "Backup," it just ignored what I told it to do and made a backup in it's default directory. So no, simple backup does NOT do what it's supposed to do.

-Richard

---

### Post by rplantz on 2006-05-14
I have mentioned in another thread that I spent a fair amount of time earlier this year researching backup strategies for a friend who has a small business with several Macinsoshes. I've been in the computer business for over 30 years, and I was amazed at my own ignorance about backups.

"Backup" means different things to different people. For example, my friend writes lots of proposals. He wanted to be able to retrieve previous versions from his backups. (Fortunately, he developed his own naming scheme for this some time ago.)

Somebody running a server needs a backup that is an up to date copy and is bootable. A home user may just need a copy of his/her personal data files. Really critical stuff should be backed up off site. There is an endless array of needs/desires/costs.

When you add in the fact that backups are not sexy, it's easy to see why there does not seem to be any good backup programs.

I ran across a good discussion of the issues in an ebook, "Take Control of Mac OS X Backups" by Joe Kissell at [www.takecontrolbooks.com](www.takecontrolbooks.com). Although it's Mac specific, he does a good job of discussing the issues.

---

### Post by John Jason Jordan on 2006-05-14
[QUOTE=rplantz]Somebody running a server needs a backup that is an up to date copy and is bootable. A home user may just need a copy of his/her personal data files. Really critical stuff should be backed up off site. There is an endless array of needs/desires/costs.[/QUOTE]
Exactamente! Well put. This has always been my problem in discussing backup solutions -- I'd try to say what I needed but the Linux-heads would jump all over me when I complained that what I needed didn't exist. There is a fundamental problem with us humans. We assume that everyone else is doing the same things with their computers as we are. It just ain't so. (In psych it's a form of transference, and it takes a long time for someone to realize that NO ONE is doing the same thing as they are.) So someone using Linux in a corporate environment or someone with a comp sci degree could never grasp that *their* backup solution was useless for me.

Although the interface is a bit clunky, Kdar does what I need. Kdar is a front end for Dar. I just wish I could resolve the lockups, but I think that may be a USB issue, not a Kdar problem. I also wish it was gnome instead of kde, but oh well. I'm more the "home user" you described, so if someone else just needs to back up personal stuff, to an external drive, I can recommend trying Kdar. At least it doesn't cost anything to take it for a spin.

---

### Post by new2ub on 2006-05-16
I guess it is only fair I explain why I use Partition Image (partimage) over some of the other linux linux backup programs like Simple Backup(sbackup), Rsync(rsync) etc.
A little more than 18 months ago I started using the linux program Partition Image (partimage) which was found at their Internet site and one other site- R.I.P..

PROS: The advantages are speed (even in GZip compression) and dependabilty. A 3.24GB partition was backed up at 429MBs min or a little over 7 minutes which didnt impress me a lot. What stunned me was a simulated or actual restoral was 2GBs min or a little over 1 minute !. The finished backup file was 1053Mbs. It also backups any FAT file system(Winblows) and restores them equally. I have to tell you though partimage failed 3 times to restore which I give it a 96% success rate. At the time of failures I was backing it up to a FAT32 partition. Ive since switched over to backing up to EXT3 (linux file system). I have not had a failure with it since. I have installed and maintained more than 20 32 and 64 bit OSs including Windblows 98SE, XP-64, Fedora, Gentoo, SUSE, Kanotix, Yoper, PCLinux, Knoppix, Damn Small, Puppy and Slax just to mention a few. Partimage handled them all. Partimage is a simple linux binary. You can copy it from the CD's /usr/sbin directory to any linux distro without the need for dependencies. Its quite portable.
CONS: One OS partimage wont restore is XP-64 on a NTFS partition. It also has trouble with partitions with more than 8GBs on it. The last (minor) disadvantage is it takes up too much backup disk space which is why I continue to look for a incremental type program like KDAR.
I tested kdar on 3 different OSs. SUSE 10.0-64, Fedora FC4-64 and Kanotix 0.4-64. It succeeded to restore SUSE but failed on Fedora and Kanotix. I havent tried kdar on Ubuntu 5.10-64 or Gentoo-64 yet.

---

### Post by h3n5y on 2006-05-16
Try bacula, which is a full fledged backup solution that works locally or via the net. Initial configuration takes longer than some GUI programs, but it's worthwile.

Cheers,
henry

---

### Post by iggykoopa on 2006-06-25
the best program I've run into for backups is drak backup too bad its not for ubuntu it ran perfectly could configure it perfectly and had an awesome gui..but i still prefer xubuntu over pclinuxos so i guess I'll have to find something new

---

### Post by Drifter on 2006-06-26
I am unable to backup to an internal cdrw drive.  I use Quicken with crossover office, but I can't get quicken to backup to the rw disk in the cdrw drive.  I can't get it to backup to floppies either.  What can I do to get something to backup.  I have read most posts in this thread but no all of them.  Any help would be appreciated.

---

### Post by bayvista on 2006-06-27
I'm using SBACKUP and it appears to be working OK. Currently, I backup to my HOME folder and then copy that (inXP) to another PC. However, SBACKUP keeps one of its files locked, and I don't know how to get round this. Has anyone else tried to copy the SBACKUP files to another PC?

---

