---
title: "unable to start xsession --- no .xsession file"
date: 2009-10-02
forum: x86 64-bit Users
---

### Post by Zizuph on 2009-10-02
The last thing I did was right-click a directory and choose to enable file sharing.  I was prompted to reboot, which I did.  Then I get this box at login that says...

Xsession: unable to start X session --- no "/home/zizuph/.xsession" file, no "/home/zizuph/.Xsession" file, no session managers, no window managers, and no terminal emulators found: aborting.

As per one suggestion I Googled, I allowed root login for X and root is able to log in without any problems.  Desktop comes right up.

As per another suggestion I found, I deleted the user account and its home directory, verified that it was deleted, then recreated it, verified it was there, and still get the same error.

Any ideas what to try next?  I just got a software raid set up on this thing about four hours ago after three days of reloading and troubleshooting.  I would hate to suddenly be forced to reload yet again, especially if I don't know what caused this.
-----
Hardware
Gigabyte MA785G-UD3H, AMD 64 X2 Dual 2 GHz, 4GB DDR2 800, GeForce 8400 GS 512.

Software
root@server:~# uname -a
Linux server 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:48:52 UTC 2009 x86_64 GNU/Linux
-----
Update: I read one post where a guy had this problem and resolved it by copying an .Xsession file from his /etc/gdm directory to his home directory.  However, I have no such file anywhere on my system.  And yes, I did updatedb and located for both upper and lower case X in the file name.
-----
Update: I read other posts like this one, where people were asked to provide the contents of their .xsession-errors files.  So, here it is...

root@server:/home/zizuph# cat .xsession-errors
/etc/gdm/Xsession: Beginning session setup...
sh: /usr/bin/cpp: Permission denied
Xsession: unable to start X session --- no "/home/zizuph/.xsession" file, no
"/home/zizuph/.Xsession" file, no session managers, no window managers, and no
terminal emulators found; aborting.

Also, from looking at that first line, I figured possibly it was a problem with the shell entry in /etc/passwd.  However, when I checked it, it was correct.
-----
Update: Also tried dpkg-reconfigure xserver-xorg.  No change.

---

### Post by bumanie on 2009-10-02
Try this. I had a similar if not identical issue during alpha testing on karmic koala.> sudo apt-get install nvidia-glx-185

---

### Post by Zizuph on 2009-10-02
Interesting...

root@server:/home/zizuph# apt-get install nvidia-glx-180
Reading package lists... Done
Building dependency tree
Reading state information... Done
nvidia-glx-180 is already the newest version.
The following packages were automatically installed and are no longer required:
  libdmraid1.0.0.rc15
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

This has to be related to my problem, since I am running a newly set up RAID.  But, if the package is no longer required, how do I resolve this?

-----
Update: I tried creating a new user and it has the same error logging into X.  Yet, root can still log in just fine.  That makes me wonder how permissions could possibly be affecting this.  I haven't done anything to permissions or changed any of the default settings on the partition containing root, boot, and home directories.

---

### Post by Zizuph on 2009-10-02
Still Googling around.  Haven't found a fix that works yet.  I do see many instances of this error going back to 2006, mostly on Debian based systems.  Most of what I've read are people who don't know how it started, and very few have any solutions posted.

I wonder if downgrading to 8.04 might provide more stability under this configuration.  Anyone out there with software RAID 1 on Ubuntu 9.04 managed by mdadm with some advice on how to proceed?  I really appreciate any input.

---

### Post by Zizuph on 2009-10-02
I give.  Reloading again.  I would like to find the cause of this for future reference.

---

