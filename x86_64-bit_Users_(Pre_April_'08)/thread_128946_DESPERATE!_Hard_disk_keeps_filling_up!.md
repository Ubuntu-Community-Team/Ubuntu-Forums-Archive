---
title: "DESPERATE! Hard disk keeps filling up!"
date: 2006-02-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by John Jason Jordan on 2006-02-12
This morning I couldn't log in to my Ubuntu-64 Breezy laptop. Going to command line I discovered the hard disk was full. So I moved 14 Gb of files off the computer onto my desktop. Then I was able to log in. And five minutes later everything stopped responding because nothing could write to the disk. I did df -h from a command line and the hard disk was full again. I saved no files and made no changes to anything in those five minutes.

I shut down from the login screen and restarted. Still can't log in -- disk full. So I went to the command line and deleted about 100 Mb more files. And still can't log in. Disk full error message. 

It's like I've got replicators eating my hard disk. OK, that's Stargate-y. But something evil is going on and I'm desperate. I have homework on this computer that is due Monday! I don't have time for this today! HELP!

---

### Post by FluffyElmo on 2006-02-12
First, make sure you get any important files of your system in case your disk is failing. Second I'd try to see what files may be taking up the space, running *ls -lR | sort +4n* from your home or  root directory will take a while but should give you a list with the largest files at the bottom.

Maybe run *dmesg* first to see if there are any disk errors being recorded?

---

### Post by John Jason Jordan on 2006-02-12
[QUOTE=FluffyElmo]First, make sure you get any important files of your system in case your disk is failing. Second I'd try to see what files may be taking up the space, running *ls -lR | sort +4n* from your home or  root directory will take a while but should give you a list with the largest files at the bottom.

Maybe run *dmesg* first to see if there are any disk errors being recorded?[/QUOTE]
Thanks for the reply. That helped. I discovered a 26 GB file in /media/usbdisk. After much hair pulling I figured out what happened:

This morning after I started the computer I decided to do a full backup with dump to my external 60 GB pocket drive. At the time my laptop drive (55 GB) had about 7-8 GB free. However, the pocket drive had about 18 GB on it from a previous backup. The new dump backup proceeded for about an hour, at which time dump announced that it wanted volume 2. It was then that I realized that the old dump file was still on the pocket disk. So I aborted the dump file intending to delete the old dump file, then redo the dump backup.

However, I needed to go somewhere first, so I pulled out the USB drive. This dismounted it, of course. At that point dump decided that it would just take it upon itself to continue the backup to what it thought was the USB drive. Instead it placed a 26 GB file in /media/usbdisk. I had no idea dump was still running. After all, I had aborted the dump, right?

So when I got where I was going and tried to start the computer I couldn't log in. The error message was that the disk was full. I couldn't figure out how that could be, but nevertheless I shelled to a command line and logged in, then deleted 7 GB of duplicate mp3 files and moved another 7 GB to my Windows computer.

Then I was finally able to log in. But about five minutes later the computer started acting wonky -- menus wouldn't drop down, programs wouldn't launch, etc. So I decided to shut down and restart. And when I restarted I encountered the same problem again -- disk full. That's when I hit the panic button. I have homework on this computer that is due tomorrow!

What was happening was that dump had set something somewhere to run itself as soon as the computer was restarted and to finish its backup. I admire its tenacity, but damn! I mean, dude, when I close down a program I expect it to close the eff down and stay down. I mean, relaunching itself after the computer was shut down?

Anyway, all is well again. All, that is, except now I am scared of dump. And there are no other backup utilities that are suitable for a single user with a single computer. Everything is designed for mammoth corporate environments with thousands of users and networking/administration issues. I tried Simple Backup but it is *too* simple, and the user interface is hopeless. Like, there is no way to specify a destination on my USB pocket disk - it has a drop-down menu only, which only sees a mount point, and you can't type into it. I've tried everything, but I've yet to get it to actually make a backup. Of course, no documentation, either.

So for now I'm just going to use Konqueror to drag the files in /home/jjj to a folder on my Windows computer. That won't help if I lose a configuration file and hose my desktop, but at least my homework is safe.

---

### Post by RAOF on 2006-02-13
[QUOTE=John Jason Jordan]...
So for now I'm just going to use Konqueror to drag the files in /home/jjj to a folder on my Windows computer. That won't help if I lose a configuration file and hose my desktop, but at least my homework is safe.[/QUOTE]
Actually, all of **your** configuration files are in your home directory anyway (you'll find a bunch of .something directories - they contain the program's configuration files).  Anything that you don't run as root will be storing its configuration in your home directory.  The only things not stored there are the system-wide settings - Xorg configuration, timezone config, networking, etc.

As an aside, you can get a better result by tar-ing your home directory and then copying the tarred file - it will preserve the file permissions, which can be important.  Just run "tar -cvjf /path/to/backupfile.tar.bz2 /home/jjj" - that should compress your home directory and put the backup where you want it.  Make sure you don't have the backup file under your home directory - tar is a bit stupid, and it will try to add the archive to itself.  Obviously, it can't do that, so it complains and stops working.

---

### Post by John Jason Jordan on 2006-02-13
[QUOTE=RAOF]Actually, all of **your** configuration files are in your home directory anyway (you'll find a bunch of .something directories - they contain the program's configuration files).  Anything that you don't run as root will be storing its configuration in your home directory.  The only things not stored there are the system-wide settings - Xorg configuration, timezone config, networking, etc.

As an aside, you can get a better result by tar-ing your home directory and then copying the tarred file - it will preserve the file permissions, which can be important.  Just run "tar -cvjf /path/to/backupfile.tar.bz2 /home/jjj" - that should compress your home directory and put the backup where you want it.  Make sure you don't have the backup file under your home directory - tar is a bit stupid, and it will try to add the archive to itself.  Obviously, it can't do that, so it complains and stops working.[/QUOTE]
I was sort of aware that configuration files are mostly in my home folder. But there are other issues. For one thing, I have a chroot environment, in which I have installed several things, and then spent more time getting a launcher working for them in the 64-bit world. Plus, just reinstalling all the applications would take a long time. That's why I think it would be easier just to make a backup that is essentially a mirror of the filesystem. If disaster strikes (e.g., a truck backs over my laptop at school), I can be back and running in the time it takes to restore the files to the hard disk on a new computer, exactly as I was before the accident.

What I'd really like, and what seems to be completely missing in Linux, is a simple GUI backup utility that a dummy n00b can figure out. There are a ton of backup solutions for massive enterprises with thousands of users. But there is nothing for a single user on a standalone computer. Unless you consider Simple Backup, but that thing is too buggy and its user interface doesn't work. 

Thanks for the suggestions

---

