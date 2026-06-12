---
title: "ntfs-3g problems"
date: 2006-11-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by jjandrj6679 on 2006-11-17
Hi all
I have just installed a fresh copy of Edgy
I have Xp  too so I used ntfs-3g to see the other drives.
I had got this configured before, seee previous post[HTML]http://ubuntuforums.org/showthread.php?t=290288[/HTML] but I was using Drapper drake and it worked fine but with Edgy it doesnt.
Now I have no access to the drives as before, I re-did everything but nothing worked.
Any help would be welcomed
Josh

---

### Post by jjandrj6679 on 2006-11-17
Hi all
I've sorted it
Not to sure what happened but the Terminal threw up a suggestion, that I tentertive took and it worked see below:
```
josh@josh-desktop:~$ cd build
josh@josh-desktop:~/build$ sudo apt-get install debhelper cdbs python python2.4 python2.4-dbus libdbus-glib-1-dev libglib2.0-dev libsysfs-dev libexpat1-dev libpopt-dev pkg-config pciutils libcap-dev doxygen intltool libusb-dev sharutils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
debhelper is already the newest version.
cdbs is already the newest version.
python is already the newest version.
python2.4 is already the newest version.
Note, selecting python-dbus instead of python2.4-dbus
python-dbus is already the newest version.
libdbus-glib-1-dev is already the newest version.
libglib2.0-dev is already the newest version.
libsysfs-dev is already the newest version.
libexpat1-dev is already the newest version.
libpopt-dev is already the newest version.
pkg-config is already the newest version.
pciutils is already the newest version.
libcap-dev is already the newest version.
doxygen is already the newest version.
intltool is already the newest version.
libusb-dev is already the newest version.
sharutils is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  ntfs-3g: Depends: libntfs-3g0 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
``` So I did just that```
josh@josh-desktop:~/build$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
josh@josh-desktop:~/build$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libntfs-3g0
The following NEW packages will be installed:
  libntfs-3g0
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 81.1kB of archives.
After unpacking 217kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://gb.archive.ubuntu.com edgy/universe libntfs-3g0 20060920-0ubuntu2 [81.1kB]
Fetched 81.1kB in 1s (65.3kB/s)                         
Selecting previously deselected package libntfs-3g0.
(Reading database ... 97344 files and directories currently installed.)
Unpacking libntfs-3g0 (from .../libntfs-3g0_20060920-0ubuntu2_amd64.deb) ...
Setting up libntfs-3g0 (20060920-0ubuntu2) ...

Setting up ntfs-3g (0.20061031-BETA-2) ...
josh@josh-desktop:~/build$ 
``` Then carried on with the rest of the install as before and it worked.
All access to all drives. Which is good.

Hope this helps anyone converting from Drapper to Edgy

Josh

---

### Post by jjandrj6679 on 2006-11-17
Hi all
Well its not all good news, I seem to be missing hda5.
I also have 2 Floppy, of which one is a floppy and the other seems to have 5.50gigs free. I have sussed that this is hda5 but how do I get it to show up?
I tried```
gksu gedit /fstab
``` and realised that I had not configured it properly whilst installing ntfs-g3, so I edited it and restarted only to have a BSOD saying my x server or something wasnt loading, so booted into recovery mode and navigated my way to fstab but couldn't edit it in there. So rebooted to Xp, found the fstab.bak copied it and pasted it into fstab.
Now we ar up'n'runnin' again but still no drives.

So how do I edit something whilst in recovery mode?
How do I sort out hda5?
Where has hda2,3 & 4 gone? I know one is a swap file but the other two?

I have these drives:
```
40G 2 Partitions 19g each One XP & One U64 (obviosly 3 Parts)
37G (Old linux install) (was split into dual Linux boot)
78G Data only
239G Data only
```
Some where along the line I've goofed up
So I'm looking for 3 drives all of which I can see in Xp?? And use??

Any help would be helpfull.

Josh

---

### Post by n0sferatu on 2006-11-18
Have you tried
> sudo fdisk -l /dev/hda to see your partition names?  Just make sure /dev/hda is in fact your hard drive name.

---

### Post by jjandrj6679 on 2006-11-18
Hi 
Here is the result???
```
josh@josh-desktop:~$ sudo fdisk -l /dev/hda
Password:

Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2499    20073186    7  HPFS/NTFS
/dev/hda2            2500        4998    20073217+   f  W95 Ext'd (LBA)
/dev/hda5            2500        3723     9831748+  83  Linux
/dev/hda6            3724        3787      514048+  82  Linux swap / Solaris
/dev/hda7            3788        4998     9727326   83  Linux

``` I cant tell wich drive is which. Where is 3 & 4? I think 5 ,6 & 7 (I hade dual boot linux on that drive). How do I format it within linux for storage use?

---

### Post by jjandrj6679 on 2006-11-18
Hold on a mo isnt hda1 my linux opperating system?
thats on a 40g drive dual boot with Xp? The drive above if you add a swap file that makes 6 drives, minus the first two (40 linux/xp) then your left with the 37g split into 4. If you follow??
How come I have 2 completely seperate drivea both being hda1??
JJ[COLOR="Navy"][COLOR="White"][COLOR="Black"][/COLOR][/COLOR][/COLOR]

---

