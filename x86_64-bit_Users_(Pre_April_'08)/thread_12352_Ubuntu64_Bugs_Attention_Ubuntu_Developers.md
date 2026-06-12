---
title: "Ubuntu64 Bugs? Attention: Ubuntu Developers"
date: 2005-01-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by drbista on 2005-01-24
**Find below are the bugs with the Warty64 Installation CD that I encountered.**

(I doubt it would be replied or solved by the Ubuntu Team soon!? See my other pending post for days: [http://ubuntuforums.org/showthread.php?p=52866#post52866](http://ubuntuforums.org/showthread.php?p=52866#post52866))

Before I  report the bugs, let me give you the hardware specifications so that I could make it clear to the ubuntu developers.

**Hardwares:**

Athlon 64 3000+
MSI Motherboard based on VIa K8M800-based
1GB DDR RAM
80GB HDD (Seagate Barracuda)
ICL 14C monitor
2 button PS/2 mouse
105 PS/2 Keyboard
FC1-32bit already installed

**Pre Partions:**

Using fdisk, I created 16 partitions for installing 3 different distro. FC1 is already installed and I wished to have following mountpoints for ubuntu64:

/dev/hda7 --> /
/dev/hda2 --> /boot
/dev/hda10 --> /var
/dev/hda14 --> /usr

the following 4 partitions are shared with FC1:
/dev/hda5 --> swap
/dev/hda11--> swap
/dev/hda6 --> /tmp
/dev/hda16 --> /home


**INSTALLATION BUGS**

1) When I tried to install above without formating (keeping the partion as it is and using the data inside) for /dev/hda6 (with shared /tmp mountpoint), it gave a loop at "Partition Disk" stage which has already been reported at [http://ubuntuforums.org/showthread.php?p=52866#post52866](http://ubuntuforums.org/showthread.php?p=52866#post52866).

Therefore, what I did was copied all the files from the /dev/hda6 (which was also tmp of the already installed FC1) and asked the installer to format the partition and mount /dev/hda6 with /tmp, it went ahead, but...

Similar problem as explained in the above thread appeared for /dev/hda16 which is a shared mountpoint for /home both for FC1 and ubuntu. So when I just clicked on 'no' to correct the error (This ext2 filesystem has a rather strange layout! Parted can't resize this and a warning that it I say no the /dev/hda16 would not have /home mountpoint), but it continued installing the Ubuntu64.

2) When I rebooted the machine after installing additional applications, it simply stuck at the login prompt. No X-server installed. "dpkg -l xserver-xfree86" shows to my astonishment that no Xserver was installed! However, I did "apt-get install xserver-xfree86" and it installed the xserver and later I did "dpkg-reconfigure xserver-xfree86" and assigned the relevant values and created XF86Config-4, but when I tried to run the X server (with rebooting and without both) by executing "startx" Ubuntu said the command not found. I tried to restart the gdm (/etc/init.d/gdm stop/start), but says no gdm is installed. Of course I did see the gnome and a world of other X utilities are installed through "dpkg -l"

Wondering how to solve it? 


3) Interestingly,  I checked whether /home was NOT mounted to /dev/hda16 as per the warning (1), but it was mounted!?

However, when I logged as the primary user (I thought that it would share the same homedirectory of the /dev/hda16, ubuntu just created the primary user in /. I already have the same user in FC1 with its home directory. And creating a user with the same primary name to link to the user configurations in /home (my /dev/hda16) would be stupid.

Now how can I sort out the problem?

Thus, the Ubuntu64Warty has a world of bugs from the very beginning of installation. Who dare to solve?  :confused:

---

### Post by Dylanby on 2005-01-24
Just a small point, but I know of only one developer who reads/posts to the forums (Daniel Stone).

However, I know many developers read/post on the mailing lists.

If you really want to interact with the developers, then that's the place to post IMHO.

You could also try IRC, but I'm not a regular there so I couldn't comment on it.

As for your problems...well I'm just a newb myself so I can't offer much help, sorry.

---

### Post by xpt on 2005-01-24
[QUOTE=Dylanby]Just a small point, but I know of only one developer who reads/posts to the forums (Daniel Stone).

However, I know many developers read/post on the mailing lists.

If you really want to interact with the developers, then that's the place to post IMHO.

You could also try IRC, but I'm not a regular there so I couldn't comment on it.
[/QUOTE]

This is the sadest fact that I learnt so far. 

I knew that Ubuntu has a very friendly IRC. I knew from many sources that many problems have been solved there instantly, and I saw with my own eyes. 

But when trying to solve my own problem, I turn to this web forum for help. Why? because others might have the same problem before, or after me. If the probelm is solved over the IRC, no document is archived. Only one person get help, and the friendly Ubuntu people at IRC would have to walk another person again for the very same problem. 

Same for the mlist. I still don't know where to search the Ubuntu mlist archive. Even if I can, I doubt that if I dig into an old problem and ask new/relavent question there, it will be archived at the same place. So it is also much less helpful than the web forum. 

**I strongly suggest the whole Ubuntu community use the web forum as their prime problem/sloving place, especially for Ubuntu members.**

thanks

---

### Post by daniels on 2005-01-24
I've seen the xserver-xfree86 thing come up a couple of times now, but no idea as to how it would happen (well, OK, a very vague idea), and have never, ever managed to reproduce it.  But as soon as I can, I'll work on fixing it.

---

