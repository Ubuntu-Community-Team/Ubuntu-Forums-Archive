---
title: "Ex microsoft user seeks help"
date: 2007-01-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by Metal03 on 2007-01-07
I just switched to Ubuntu yesterday and I am trying to get this platform as working as possible!!  (I don't wanna go back to WindowsXP!!)  I am just experiencing problems because I have a amd64bits computer!!

Here are the things I'd need help with (And please when you answer, keep in mind I've been using Linux for only a few hours...  so make your explanations "for dummies") :

- First I'm trying to watch the videos I had before on windowsXP (.wmv, .avi, .mpg, DivX videos) and I can't seems to find the proper player or the proper codecs

- Second I can't seem to be able to access my other Hard drive (NTFS formated under WindowsXP)

- And last thing, but not the least....  I'd like to play World of Warcraft on Ubuntu!!

Thanks for your time!

---

### Post by Metal03 on 2007-01-07
Oh, and one other thing....

Is an anti-virus something I should look for on Linux or is it useless?

---

### Post by kebes on 2007-01-07
First off: welcome! I hope you'll find Ubuntu to your liking.


Now to your questions:
-To get all the "essential" multimedia codecs installed, an easy way is to use "automatix." This ia program that will load up the most commonly requested extra features. Go here:
[http://www.getautomatix.com/](http://www.getautomatix.com/)
and follow the installation instructions. When you run automatix, it will give you a list of things you can install. Find the ones you want. You'll probably be interested in "multimedia codecs", "play mp3s", "play DVDs", "mplayer and mencoder", "firefox", "flash plugin for firefox", and others...


-You should be able to access your NTFS drive. If you open your file browser (nautilus) and go to the "/media/" folder, do you see a folder called "Windows" (or whatever..)? If so, just click on that and it will open. If no such folder exists, you can "mount" it. (There should be something like "Disks & Partitions" or "filesystems" in your system settings menu.)


-Running WoW on Linux can be tricky, but is possible. It involves using a program called "wine". There are good instructions for enabling wine on Ubuntu:
[http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)

After doing that, in theory you just run the WoW installer. However in practice it might be more tricky (never done it). You should search these forums for a how-to on that subject, or post this question again in the Ubuntu Gaming sub-forum...

Hope that helps... post again if anything is unclear.

---

### Post by bigken on 2007-01-07
use [automatix]("http://www.getautomatix.com/") for the codecs ect 

they say a firewall is better than virus software on linux

---

### Post by kebes on 2007-01-07
> **Metal03 said:**
> Oh, and one other thing....

Is an anti-virus something I should look for on Linux or is it useless?

Short answer: don't bother.


Long answer: If you're running Ubuntu by itself, and you're "safe" (don't run untrustworthy software) then you don't need a virus scanner. There are only a few theoretical viruses for Linux and no active ones (that I'm aware of). However many people who run Linux in a mixed environment (on a network with Windows machines or dual-booting with a Windows install) will still install a virus checker in Linux so that they can detect Windows viruses and prevent them from spreading to other Windows machines.

However I'd say even if you're dual-booting, as long as you have a virus checker running while booted into Windows, you're quite safe.

---

### Post by kebes on 2007-01-07
With regard to WoW, this thread:
[http://ubuntuforums.org/showthread.php?t=120615](http://ubuntuforums.org/showthread.php?t=120615)

Describes how others have gotten it working. It seems to involve adding patches to wine, and then compiling it. This is more complicated than just installing wine the way I mentioned before. However if you're willing to invest some time and effort it looks like it can be done.

---

### Post by Metal03 on 2007-01-07
The problem I've had is that I've been told that wine does not exist on amd64 platforms...  If it does, please tell me how to use it and how to install it!

---

### Post by kebes on 2007-01-07
You said your hardware was AMD64, but are you running the 64-bit Ubuntu? If you're running the 32-bit Ubuntu, then wine works fine.

If you're running the 64-bit Ubuntu, I believe wine still runs (you can run 32 bit programs in 64-bit Linux). You may need to install some 32-bit libraries... or you can compile wine and it should run on 64-bit systems (you may need to compile wine anyways to get WoW working).

In either case, it's certainly worth a try.

---

### Post by Metal03 on 2007-01-07
Ok, first...  yes I am using the 64bits Edgy Ubuntu...  so if I can use wine in 32 still...  please walk me thru it!!  Step by step!  :)

Second, I've used automatix...  thanks a lot!!  I can now read movies with VCL..  I just have troubles with a .rmvb file...  but since I had problem on windows with this...  I can wait on Ubuntu!!

Also, I've tried to access my NTFS HD and I can't seem to find it...  but I used to be able to see it!  But when I tried to mount it, it wouldn't!!  But now I can see it anywhere!!!  :(  Not in the media directory...  nowhere!!

Please help...  all my stuff is on this HD!!

---

### Post by kebes on 2007-01-07
> **Metal03 said:**
> I've tried to access my NTFS HD and I can't seem to find it...  but I used to be able to see it!  But when I tried to mount it, it wouldn't!!  But now I can see it anywhere!!!  :(  Not in the media directory...  nowhere!!

In a terminal (Applications > Accessories > Terminal), type this:

more /etc/fstab

You should see something like:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda2       /media/windows           ntfs    defaults        0       2
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

If you don't have any line mapping to "/media/windows" (or whatever it was), then that's a problem! (You can copy the output from that command to this thread if you like.)


To add the partition to the list, go System > Admin > Disks

Then select your disk and the appropriate partition. (The filesystem type will be "NTFS".) Make sure the "Access Path" is what you want it to be ("/media/windows" or whatever). You can click on "Enable" if necessary. You should then be able to find it in the filesystem. Go Places > Computer
and then go into Filesystem > Media > Windows

---

### Post by Metal03 on 2007-01-07
Here is What I got from your commanc line : 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=eb9d0ccc-78cd-4adc-b56f-704cf9dac167 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=4d2911ce-5440-43f3-a47d-4eba6ac371b4 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

It seems the line you wanted is not there!

And also, when I go to System > Admin >

I see no "Disk" options or anything like it...  What's wrong...  hehehe!!

btw...  Thanks a lot for your time Kebes!

---

### Post by kebes on 2007-01-07
> **Metal03 said:**
> It seems the line you wanted is not there!

Indeed! We need to add it!

Graphically, on Ubuntu, you should be able to click "System" on the upper menubar, then "Administration" and then "Disks". (Maybe it's labelled as "Disk & Partitions" or something?) If you're using Kubuntu/KDE, it would be KMenu > System Settings > Disk & Filesystems


If those options are not there (which seems strange), then you can try doing it in the terminal. To do this you need to figure out the correct device that points to the partition you want. First do this:
```

ls /dev/hd* -laF

```

Which should list the partitions you have. From your "fstab" output in the last post it seems that "/dev/hda1" is your root filesystem ("/"), and that "/dev/hda5" is your swap. If your Windows is on the same hard drive as Ubuntu, then it's probably "/dev/hda2" (or maybe "/dev/hda3".

Now type this:
```

cd /media/
ls

```

This will go into the media folder and list contents. Is the directory for your windows mount there? If it is there, then go into it and make sure it is empty:

```

cd windows
ls
cd ..

```

Presumaly that "ls" step didn't return anything, right? (If you saw your windows files then it's already mounted!)

If your windows directory wasn't even listed, then make it:
```

sudo mkdir windows

```

And then try and mount your required partition to that directory:
```

sudo mount /dev/hda2 windows

```
(Of course make sure "/dev/hda2" is what you think is the windows partition.)
If the above command worked, then you should be able to go into the directory and list your windows files:

```

cd windows
ls

```

If the above worked, then you can update your file "/etc/fstab" to include the missing line.

---

### Post by kebes on 2007-01-07
So just to complete what I was saying in my last post...once you've figured out the device for your windows partition (say its "/dev/hda2") and you have created a directory for it to mount to (like "/media/windows"), then you can edit the file "/etc/fstab" and add a line like:

```

/dev/hda2       /media/windows           ntfs    auto,users,rw,exec,uid=metal,gid=metal        0       2

```

To edit fstab you go:
gtksu gedit /etc/fstab


Bear in mind that above where it says uid=metal, I just put "metal" because I don't know what your username is... replace both instances of "metal" with your actual username. Then close and save the file and reboot. (Or just go "mount -a" on commandline if you don't want to reboot.)


If these commandline instructions are too confusing (I going through it all very fast), let me know...

---

### Post by Metal03 on 2007-01-07
Ok, I feel that we are getting somewhere...  my windows HD was /dev/hdb1

I mounted it...  I can now see it in the /media/ directory...  but when I try to access it, it says that I don't have the permission for that!  Could it be because of the NTFS formating?

---

### Post by kebes on 2007-01-07
Something else just occured to me! Instead of the commandline instructions try typing the following in a terminal:

disks-admin


This should open up the disk admin utility that I was trying to get you to click on. (You'll need to enter your password.) You can then use that graphical utility to set up the partition, as I was mentioning before.

---

### Post by Metal03 on 2007-01-07
Ok, I feel that we are getting somewhere... my windows HD was /dev/hdb1

I mounted it... I can now see it in the /media/ directory... but when I try to access it, it says that I don't have the permission for that! Could it be because of the NTFS formating?

And I also tried the disks-admin command...

bash: disks-admin : command not found

:(

---

### Post by kebes on 2007-01-07
Strange that "disks-admin" is not installed. You could install it with Synaptic if you want. (on commandline you can go "sudo aptitude install disks-admin" to install it.)

The "not enough permission" may well be because you mounted it as "root" (superuser). So if you go:
ls -laF /media/

It will probably list something like:
```

drwxr-xr-x  4 root  root  4096 2006-10-06 20:24 ./
drwxr-xr-x 21 root  root  4096 2006-11-09 18:27 ../
lrwxrwxrwx  1 root  root     6 2006-09-27 10:04 cdrom -> cdrom0/
drwxr-xr-x  2 root  root  4096 2006-09-27 10:04 cdrom0/
drwx------  8 root root 4096 2006-11-22 13:58 windows/

```

Since "windows/" is owned by "root", only root can go into it. You can change that by going:
```

sudo chown metal:metal windows/ -R

```

Then see if you can go into it (by going "cd windows")... I'm getting you to do this mostly to make sure that we have the right partition... but if you're sure "/dev/hdb1" is your windows, then you can perhaps unmount it and then go change your fstab as I was mentioning before. When you're ready to unmount:
```

umount /dev/hdb1

```

...and then go modify fstab.

---

### Post by Metal03 on 2007-01-07
OMG!!!

THANKS!!  I have access to my files!!  SHWEET!!

ok, now I have another problem...  I've encrypted some files in windowsXP...  can I get access to those in any ways now?

Oh seriously...  I have access to my music and my movies and stuff...  thanks!!

---

### Post by kuja on 2007-01-08
I doubt it, you'll probably have to decrypt them from windows.

---

### Post by kebes on 2007-01-08
> **Metal03 said:**
> Oh seriously...  I have access to my music and my movies and stuff...  thanks!!

No problem... glad it worked.

> ok, now I have another problem...  I've encrypted some files in windowsXP...  can I get access to those in any ways now?

As far as I know, it's not possible. The Windows file encryption key is itself encrypted with your Windows logon password. (Which means that if your logon account gets screwed the data is lost.) You'll have to decrypt the data in Windows so that it can be read by both operating systems.

However you could switch to using an encryption system that is supported on both Windows and Linux. Something like truecrypt (never used it myself but it looks good).


Also note that reading from your NTFS drive should work, but that writing to it is still considered experimental (although nowadays most people find it quite stable). However there are filesystem drivers for Windows (there's one called ext2IFS and another called ext2fsd) that allow it to access the ext2/ext3 Linux partitions. So this is another option for sharing files between the two OSes.


Good luck, and have fun with Ubuntu!

---

### Post by BIGtrouble77 on 2007-01-08
Back to the World of Warcraft question... If you want ZERO hassle getting it working then you can get Cedega.  Cedega is basically winex designed for games.  There's very little programming because you have game profiles.  I'm currently running Civ IV, Oblivion and Birth of America with cedega.  It does have a subscription fee of $5 month and you are required to pay for the first 3 months.

---

