---
title: "[SOLVED] few questions about xubutnu"
date: 2008-05-28
forum: x86 64-bit Users
---

### Post by DachaArh on 2008-05-28
I have ubuntu 64 bit installed on my comp. I have a separate home partiton.
I have just downloaded and tested from live mode xubuntu 8.04 64bit, and I just love it.
It is alot faster then ubutnu, so I'm thinking to install it over ubuntu, so I wan't to ask you some questions.

First : What are disadvantages of xubuntu over ubuntu ( if any) - for software compatibility, features ..etc...?
Second: Does xubuntu have workspaces , can it have synaptic?
Third: Can I leave my home partition unformated and to use it on xubuntu ..?


thanks for any help ..

---

### Post by jeffus_il on 2008-05-28
> **DachaArh said:**
> I have ubuntu 64 bit installed on my comp. I have a separate home partiton.
I have just downloaded and tested from live mode xubuntu 8.04 64bit, and I just love it.
It is alot faster then ubutnu, so I'm thinking to install it over ubuntu, so I wan't to ask you some questions.

First : What are disadvantages of xubuntu over ubuntu ( if any) - for software compatibility, features ..etc...?
[COLOR=Red]The advantages and disadvantages are up to you and depend on your personal preferences on the desktop. If you like a little lean and maybe faster, Xubuntu is for you. Technically you can run all Linux applications on either.[/COLOR]
> **DachaArh said:**
> Second: Does xubuntu have workspaces , can it have synaptic?
[COLOR=Red]Yes and Yes[/COLOR]
> **DachaArh said:**
> Third: Can I leave my home partition unformated and to use it on xubuntu ..?
[COLOR=Red]Yes, and more than that you don't need to reinstall, You can install the XFCE desktop and then choose either Gnome (Ubuntu) or XFCE (Xubuntu) at the Gdm menu before logging in. You can also intall the xubuntu-desktop package to bring the whole Xubuntu environment in, and if you don't use Gnome anymore, you can uninstall the gnome programs, using Synaptic.

You can also lighten your install by removing services you don't need, see the Gnome System->Administration->Services.

Since the same kernel is used by Xubuntu and Ubuntu, there iis no need to reinstall to change desktop and remember Gdm lets you choose the session to run, It can be XFCE (Xubuntu) Gnome (Ubuntu) KDE (Kubuntu and many other window managers like icewm, openbox etc. or plain old X Windows with no bells and whistles, but the best speed.
[/COLOR] 

> **DachaArh said:**
> hanks for any help ..

[COLOR=Red]By the way, all gnome panel applets can run in XFCE (Xubuntu), there is a wrapper applet for them.[/COLOR]

---

### Post by DachaArh on 2008-05-28
thanks for all help
How can I install XFCE, what should I select in synaptic, or what shoud I type in terminal ....?

---

### Post by jeffus_il on 2008-05-28
Install the package xubuntu-desktop in synaptic.
Here is the description:
> This package depends on all of the packages in the Xubuntu desktop system

It is safe to remove this package if some of the desktop system packages are
not desired.
"depends" means that this package will drag along all the necessary xubuntu xfce packages, see the "dependencies" tab of the package in synaptic.

---

### Post by Kilz on 2008-05-28
> **DachaArh said:**
> thanks for all help
How can I install XFCE, what should I select in synaptic, or what shoud I type in terminal ....?

You could also open the terminal and type in ```
sudo aptitude install xububtu-desktop
```

---

### Post by aaron.d on 2008-05-28
> **Kilz said:**
> You could also open the terminal and type in ```
sudo aptitude install xububtu-desktop
```

make that 

> sudo aptitude install xubu**n**tu-desktop

:)

---

### Post by DachaArh on 2008-05-28
thanks, I have managed to install xubuntu-desktop 
so I have one question now.
Is there a way to remove rectangle which is wraping icon names on desktop.
See it on this picture :
[IMG]http://i28.tinypic.com/15x5wlj.png[/IMG]

---

### Post by cardinals_fan on 2008-05-28
> **DachaArh said:**
> thanks, I have managed to install xubuntu-desktop 
so I have one question now.
Is there a way to remove rectangle which is wraping icon names on desktop.

[http://xubuntu.wordpress.com/2007/08/27/howto-remove-the-borders-of-your-desktop-icon-text/](http://xubuntu.wordpress.com/2007/08/27/howto-remove-the-borders-of-your-desktop-icon-text/)

---

### Post by DachaArh on 2008-05-28
I tried it and it did not work...
I noticed that I have it only on some themes ...

I have this in terminal when I type that :

> dachaarh@dachaarh-desktop:~$ touch ~/.gtkrc-2.0
dachaarh@dachaarh-desktop:~$ mousepad ~/.gtkrc-2.0
/home/dachaarh/.gtkrc-2.0:4: error: unexpected character `\342', expected string constant
/home/dachaarh/.themes/T-ish-Brushed/gtk-2.0/gtkrc:59: Clearlooks configuration option "sunkenmenu" is not supported and will be ignored.
/home/dachaarh/.themes/T-ish-Brushed/gtk-2.0/gtkrc:60: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/dachaarh/.themes/T-ish-Brushed/gtk-2.0/gtkrc:61: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/dachaarh/.themes/T-ish-Brushed/gtk-2.0/gtkrc:62: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.


---

### Post by DachaArh on 2008-05-28
I did it ;) 

I can't see my windows - ntfs partitions in XFCE enviroment...and in gnome I can see them ...
why is that and can I do something about that ?

---

### Post by radagast1155 on 2008-05-28
> **DachaArh said:**
> I have ubuntu 64 bit installed on my comp. I have a separate home partiton.
I have just downloaded and tested from live mode xubuntu 8.04 64bit, and I just love it.
It is alot faster then ubutnu, so I'm thinking to install it over ubuntu, so I wan't to ask you some questions.

First : What are disadvantages of xubuntu over ubuntu ( if any) - for software compatibility, features ..etc...?
Second: Does xubuntu have workspaces , can it have synaptic?
Third: Can I leave my home partition unformated and to use it on xubuntu ..?


thanks for any help ..

Thanks so much for the screen shot im installing it through Ubuntu now!

---

### Post by Kilz on 2008-05-28
> **DachaArh said:**
> I did it ;) 

I can't see my windows - ntfs partitions in XFCE enviroment...and in gnome I can see them ...
why is that and can I do something about that ?

Xfce is a lighter desktop, as such it sometimes requires you to do things manually. [Here is a thread that can help you do just that.]("http://www.uluga.ubuntuforums.org/showthread.php?t=797959")

---

### Post by DachaArh on 2008-05-28
here ar emy partitions:
> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0bf40bf3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           2        3859    30989385    7  HPFS/NTFS
/dev/sda2            3860       19457   125290935    f  W95 Ext'd (LBA)
/dev/sda5            3860        4081     1783183+   7  HPFS/NTFS
/dev/sda6            4082        4343     2104483+  82  Linux swap / Solaris
/dev/sda7            4344        8295    31744408+  83  Linux
/dev/sda8            8296       19457    89658733+  83

and here is what I get when I try:
> sudo mount -t ntfs /dev/sda1/media/System

> Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

And nothing happens, I stil do not have my NTFS partition in /media

Am I doing something wrong.?

---

### Post by eriqjaffe on 2008-05-29
You might be better off mounting by UUID in /etc/fstab.

```
sudo blkid
```
...will get the UUID's for you (here's my blkid output):

```
/dev/sda1: UUID="00000000458D9A71" TYPE="ntfs" LABEL="18_GB_HD" 
/dev/sdb1: UUID="8A44ED2C44ED1C27" LABEL="18_GB_HD_2" TYPE="ntfs" 
/dev/loop0: UUID="d48c38c3-64bd-4bd7-ae6f-96da5547b31f" TYPE="ext3" 
/dev/sdc1: UUID="4110E0A85F16A4B6" LABEL="18_GB_HD_2" TYPE="ntfs" 
/dev/sdd1: UUID="3C2D3C9F491B1A16" TYPE="ntfs" 
/dev/sdd2: UUID="3429C5520E412D92" TYPE="ntfs"
```

Make your mount directories manually and then edit /etc/fstab:

```
/dev/disk/by-uuid/3C2D3C9F491B1A16 /media/d_drive ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/disk/by-uuid/4110E0A85F16A4B6 /home/eriq/Music ntfs-3g defaults,locale=en_US.UTF-8 0 0 
/dev/disk/by-uuid/3429C5520E412D92 /media/e_drive ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/disk/by-uuid/8A44ED2C44ED1C27 /media/old_e_drive ntfs-3g defaults,locale=en_US.UTF-8 0 0
```

"sudo mount -a" will mount everything in fstab, and they'll automount when you log in.

---

### Post by DachaArh on 2008-05-29
here are my UUID's
> /dev/sda1: UUID="C2ACCEEFACCEDD53" LABEL="System" TYPE="ntfs" 
/dev/sda5: UUID="145B8DDABF238821" LABEL="Razno" TYPE="ntfs" 
/dev/sda6: TYPE="swap" UUID="d30e3b5c-d9bc-4c7d-81a2-ff5478eb6381" 
/dev/sda7: UUID="d6770310-e921-45cc-9edf-3bfa83a9da69" TYPE="ext3" 
/dev/sda8: UUID="c70fecef-f47c-418b-943b-4d7e84c34f83" TYPE="ext3" 

what should I type in terminal ...?

---

### Post by aaron.d on 2008-05-29
> **DachaArh said:**
> sudo mount -t ntfs /dev/sda1/media/System

did you actually type that? because you have a typo with the mount point and device running together. it should be:

```
sudo mount -t ntfs /dev/sda1 /media/System
```

So try that.


Now, as mentioned, if all is well you may want to make it permanent by editing the File Systems Table (/etc/fstab):

```
sudo gedit /etc/fstab
```

and following roughly what was shown in eriqjaffe's post above ^, substituting the obvious (UUIDs and mount points) with your own, and testing with > mount -a

**_NOTE:_**
PLEASE, make a backup of this file before you do anything.

```
sudo cp /etc/fstab /etc/fstab.bk
``` or similar, just in case you have slippery fingers. Its best practice to back all major configuration file up before editing.

---

### Post by DachaArh on 2008-05-29
I'm sorry but I'm affraid to make a mistake :
so Can You please tell me what to add in /etc/fstab
if my 
UUID'is like this :
> /dev/sda1: UUID="C2ACCEEFACCEDD53" LABEL="System" TYPE="ntfs"
/dev/sda5: UUID="145B8DDABF238821" LABEL="Razno" TYPE="ntfs"
/dev/sda6: TYPE="swap" UUID="d30e3b5c-d9bc-4c7d-81a2-ff5478eb6381"
/dev/sda7: UUID="d6770310-e921-45cc-9edf-3bfa83a9da69" TYPE="ext3"
/dev/sda8: UUID="c70fecef-f47c-418b-943b-4d7e84c34f83" TYPE="ext3"

thanks alot

---

### Post by Kilz on 2008-05-29
Also when you use 
```
sudo mount -t ntfs /dev/sda1 /media/System
```

Make sure that /media/System exists before you try and mount something there.

---

### Post by aaron.d on 2008-05-29
> **DachaArh said:**
> I'm sorry but I'm affraid to make a mistake :
so Can You please tell me what to add in /etc/fstab
if my 
UUID'is like this :


thanks alot

can you first make sure that manually mounting the partition works?


```
sudo mount -t ntfs /dev/sda1 /media/System


```

as mentioned, make sure /media/System exists (case sensitive).

If that works, please provide us with the output of:

```
cat /etc/fstab
```

and we can help you tailor your fstab.

---

### Post by DachaArh on 2008-05-30
I did it with :
sudo mount -t ntfs /dev/sda1 /media/System

first I created folders Razno and System in /media with gksudo thunar.
But now I have another problem.
Only root has permissions to read and write on that partitions, can I have permissions too ?


thanks alot

---

### Post by aaron.d on 2008-05-30
i think you need the umask option. to test, umount the partition and re-run the command like so:
```

sudo mount -t ntfs /dev/sda1 /media/System -o umask=000
```

test it to see, I could be wrong as it has been a while. I generally mount my NTFS partitions read-only for all users when I want them mounted, and if i recall, i was using "umask=0222". Let me know.

---

### Post by DachaArh on 2008-05-30
thanks alot, now I can read and write to these partitions , but will they stay mounted when I restart computer ?

---

### Post by DachaArh on 2008-05-30
I made shortcuts on panel to run these commands from terminal, don't know better

---

### Post by aaron.d on 2008-05-30
> **DachaArh said:**
> thanks alot, now I can read and write to these partitions , but will they stay mounted when I restart computer ?

nope... now do a:

```
cat /etc/fstab
```

and we can try to tailor your fstab for you.

back it up too while you are at it:

```
sudo cp /etc/fstab /etc/fstab.bkp
```

---

### Post by DachaArh on 2008-05-30
thanks alot, but no need I'm better with running command from panel, maybe sometimes I do not wan't to mount , so this is better option ;)

thanks again for all your help.
Sorted

---

### Post by aaron.d on 2008-05-30
> **DachaArh said:**
> thanks alot, but no need I'm better with running command from panel, maybe sometimes I do not wan't to mount , so this is better option ;)

thanks again for all your help.
Sorted

No problem, enjoy.

---

