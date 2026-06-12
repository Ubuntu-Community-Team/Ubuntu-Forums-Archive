---
title: "Problem with ntfs-3g HELP"
date: 2007-06-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by J.One on 2007-06-21
Hi. I have install ntfs-3g from Automatix2 and also ntsf config from synaptic package manager and i cannot enable write on my second hard drive (internal and ntfs) I have feist x64 and an AMD64.
A friend of mine has pentium 4 and has installed feisty x86 and ntfs-3g s working just fine withought ntfs config. Is this fault because of the x64 version? Can i have a help here because i have post again nad again and no help from anybody 
(Previews Post) ------> [http://ubuntuforums.org/showthread.php?t=476418](http://ubuntuforums.org/showthread.php?t=476418)

---

### Post by crjackson on 2007-06-21
> **J.One said:**
> Hi. I have install ntfs-3g from Automatix2 and also ntsf config from synaptic package manager and i cannot enable write on my second hard drive (internal and ntfs) I have feist x64 and an AMD64.
A friend of mine has pentium 4 and has installed feisty x86 and ntfs-3g s working just fine withought ntfs config. Is this fault because of the x64 version? Can i have a help here because i have post again nad again and no help from anybody 
(Previews Post) ------> [http://ubuntuforums.org/showthread.php?t=476418](http://ubuntuforums.org/showthread.php?t=476418)

I don't know what is causing your particular problem, but I'm running the A64 version and ntfs-3g works perfectly for me. I have 4 hard drives in my system and I can read/write to all of them using ntfs-3g

---

### Post by Cappy on 2007-06-21
Feisty automatically comes with NTFS-3G.
I'm guessing your problem is permissions, you don't have permission to write to it because it is owned by root.
Try this:
```
sudo chown -R $USER:$USER /media/whateveryourdriveis
sudo chmod 774 -R /media/whateveryourdriveis
[/CODE

If this doesn't work try posting your
[CODE]gedit /etc/fstab
```

---

### Post by J.One on 2007-06-21
i didn't get it right...I didn't understand "whatmydriveis" ......
What do you mean by that, the drives name? (mine is Drive 2) or  e.x.  the "sda5"?
Because i put sudo chown -R $USER:$USER /media/Drive 2 and
sudo chown -R $USER:$USER /media/sda5 and it didn't works...

---

### Post by J.One on 2007-06-21
it cames with a chown: cannot access `/media/sda5': No such file or directory 
or a
chown: cannot access `/media/Drive 2': No such file or directory

Sorry. newbe here

---

### Post by Cappy on 2007-06-21
When you open the hard drive the path to it is at the top.
It will be /media/something

---

### Post by misterjazy on 2007-06-30
I am also using the AMD64 build of Feisty, and I'm having what sounds like a similar NTFS-3G problem.

I literally just upgraded from Edgy, where I had full write access to my NTFS partition with NTFS-3G/Fuse.  Upon entering Feisty, I can read & modify existing files on the NTFS partition, but I cannot *create* new files.  I have already tried using ntfs-config, even completely unmounting the partition, deleting the entry from fstab, and letting ntfs-config pick it up.  Still got the same behavior.

I then purged the system of the NTFS-3G and FUSE packages, rebooted, and reinstalled.  Same behavior - I can read and modify existing files, but cannot create new ones.  The FUSE kernel module is installed.


Here's my fstab entry:
```
/dev/hda1 /media/hda1 ntfs-3g defaults,locale=en_US.UTF-8 0 0
```

And here's it's entry in *mount*'s output:
```
/dev/hda1 on /media/hda1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
```

And ensuring the module is indeed installed:
```
root@wonkavator:~# lsmod | grep fuse
fuse                   51888  4 
```

Creating a file:
```
root@wonkavator:/media/hda1/cygwin# ls
bin  cygdrive  cygwin.bat  cygwin.ico  etc  home  lib  packages  tmp  usr  var

root@wonkavator:/media/hda1/cygwin# touch newfile.txt
touch: cannot touch `newfile.txt': Input/output error

root@wonkavator:/media/hda1/cygwin# ls > out.txt
bash: out.txt: Input/output error

root@wonkavator:/media/hda1/cygwin# ls
bin  cygdrive  cygwin.bat  cygwin.ico  etc  home  lib  packages  tmp  usr  var
```

However, if I modify an existing file, it works:
```
root@wonkavator:/media/hda1/cygwin# echo "I've been modified!  FIX ME PLEASE" > cygwin.bat

root@wonkavator:/media/hda1/cygwin# cat cygwin.bat
I've been modified!  FIX ME PLEASE
```

The same behavior happens on other NTFS partitions, too:
```
root@wonkavator:/media/80 gig hd# mount
...
/dev/sdf1 on /media/80 gig hd_ type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)

root@wonkavator:/media/80 gig hd_# touch newfile.txt
touch: cannot touch `newfile.txt': Input/output error
```


Any idea on what's gone wrong and/or how to fix it?

---

### Post by J.One on 2007-07-02
Guys, the solution for was that i had to UNMOUNT first my hard drive and the enable write method from ntfs-3g configurator.The i rebooted and it worked!

---

### Post by misterjazy on 2007-07-02
I tried unmounting before using the configuration tool.  Still got the same effects.  I even tried commenting out that line in fstab and manually mounting the drive with the -o rw option.  I still can only read & modify files.

Strangely enough, NTFS-3g works fine on Feisty on my laptop (also AMD-64).

---

### Post by szaka on 2007-07-02
> **misterjazy said:**
> 
```

root@wonkavator:/media/80 gig hd_# touch newfile.txt
touch: cannot touch `newfile.txt': Input/output error
```

Any idea on what's gone wrong and/or how to fix it?
I believe this is supported in NTFS-3G 1.616: [http://ntfs-3g.org/releases.html](http://ntfs-3g.org/releases.html)
*fix: file creation always gave "I/O error" if the $MFT Bitmap wasn't up-to-date*

Alternatively run chkdsk DRIVE: /f on Windows. Only NTFS-3G 1.616 can fix the volume corruption type with which Windows "presented" you.

---

### Post by misterjazy on 2007-07-05
> **szaka said:**
> I believe this is supported in NTFS-3G 1.616: [http://ntfs-3g.org/releases.html](http://ntfs-3g.org/releases.html)
*fix: file creation always gave "I/O error" if the $MFT Bitmap wasn't up-to-date*

Alternatively run chkdsk DRIVE: /f on Windows. Only NTFS-3G 1.616 can fix the volume corruption type with which Windows "presented" you.


I'll give chkdsk a try next time I boot to Windows, and failing that, will give 1.616 a try.  Thanks for the info!

---

### Post by misterjazy on 2007-07-25
chkdsk did indeed help.  I haven't tried it on the internal drive, but I tried it on an external (which started experiencing the same issue on a different feisty machine), and it worked.  Didn't need to upgrade ntfs-3g.

Thanks again!

---

