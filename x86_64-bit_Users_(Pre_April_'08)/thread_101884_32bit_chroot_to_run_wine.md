---
title: "32bit chroot to run wine?"
date: 2005-12-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by ryan76 on 2005-12-10
I just upgraded from Hoary to Breezy this week and am trying to install Wine so I can run the firmware for my wireless modem.

Does this Howto work for breezy?
[http://ubuntuforums.org/showthread.php?t=24575]("http://ubuntuforums.org/showthread.php?t=24575")

This is actually quite complicated for me to follow but if it works I'll give it a shot. If there's an easier way to run Wine on AMD64, I would love to know. I understand that it creates a 32-bit environment to run 32-bit applications but once it's set up I assume it's all command line? I'm OK with that I think.

Thanks in advance for any help

---

### Post by Suger on 2005-12-11
Works perfectly, takes a 15 minutes to set up. Then, if you want to have such things as launchers, you can without any problem, you've got smeg for that. I have launchers for a few windows applications, works like a charm.

---

### Post by Ferrat on 2005-12-11
Works like a charm, just replace all the hoary with breezy 

Main is commandline true but as stated you can use launchers and you wont see any terminal.

---

### Post by ryan76 on 2005-12-12
Thanks all

I'm still in Step 1 and it did this:

ryan@ubuntu:/$ sudo chroot /chroot/
chroot: cannot run command `/bin/bash': No such file or directory

eek! why??

---

### Post by Suger on 2005-12-12
Because you don't have bash installed in your chrooted env...
 Are you sure your debootstrap went well ? I would erase the /chroot and start again. And yes, be sure to replace hoary with breezy.

---

### Post by ryan76 on 2005-12-12
Thanks

I got right up to the last line of Step 5, everything went fine until I ran synaptic32:

ryan@ubuntu:~$ sudo synaptic32
(breezy) synaptic32

(synaptic32:8134): Gtk-WARNING **: cannot open display:
dchroot: Child exited non-zero.
dchroot: Operation failed.
ryan@ubuntu:~$

Does this mean I have to install something else? Which package?

---

### Post by Suger on 2005-12-13
You sure are an interesting case. What happens if you do

ryan@ubuntu:~$ dchroot -d
ryan@ubuntu:~$ sudo synaptic
 ?
And the same with synaptic32 ?

If the first works and not the second, it's a symlink problem. If both work, there is a problem with your chrooted environment (from experience, it's better not to symlink the chrooted environment, or at least to work with the absolute path and not the symlinked one (my chroot is effectively in my home partition, not in the root one, but symlinked in the root for convenience. Except in fstab, I used /home/chroot and not /chroot, having had problems else).

You can also try to do a
ryan@ubuntu:~$ dchroot -d
ryan@ubuntu:~$ sudo apt-get install libgtk2.0-0 --reinstall
ryan@ubuntu:~$ apt-get install synaptic --reinstall

---

### Post by ryan76 on 2005-12-13
Hmm.  here are the results:

```
ryan@ubuntu:/$ **dchroot -d**
Executing shell in 'breezy' chroot.
ryan@ubuntu:/$ **sudo synaptic**

(synaptic:11302): Gtk-WARNING **: cannot open display:
ryan@ubuntu:/$ **sudo apt-get install libgtk2.0-0 --reinstall**
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B/2053kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y

Preconfiguring packages ...
(Reading database ... 12802 files and directories currently installed.)
Preparing to replace libgtk2.0-0 2.8.6-0ubuntu2.1 (using .../libgtk2.0-0_2.8.6-0ubuntu2.1_i386.deb) ...
Unpacking replacement libgtk2.0-0 ...
Setting up libgtk2.0-0 (2.8.6-0ubuntu2.1) ...

ryan@ubuntu:/$ **sudo synaptic**

(synaptic:11338): Gtk-WARNING **: cannot open display:
ryan@ubuntu:/$ **sudo apt-get install synaptic --reinstall**
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B/1062kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y

Preconfiguring packages ...
(Reading database ... 12802 files and directories currently installed.)
Preparing to replace synaptic 0.57.4ubuntu10 (using .../synaptic_0.57.4ubuntu10_i386.deb) ...
Unpacking replacement synaptic ...
Setting up synaptic (0.57.4ubuntu10) ...

ryan@ubuntu:/$ **sudo synaptic**

(synaptic:11384): Gtk-WARNING **: cannot open display:
ryan@ubuntu:/$ **sudo synaptic32**

(synaptic32:11389): Gtk-WARNING **: cannot open display:
ryan@ubuntu:/$
```

I also noticed that /chroot is not visible when i'm in the chroot and it is when I'm not. 

I think I might just start again.... :(

---

### Post by Suger on 2005-12-13
It's normal that chroot is not visible : when you chroot, you go inside the chroot, so what you saw before as /chroot is now /. This is why you have to tell to fstab to bind some directories (home, fonts, dev, proc, cdrom) inside the chroot.

---

### Post by ryan76 on 2005-12-13
OK I understand that now...

Does anyone have any ideas on why synaptic or synaptic 32 aren't working?

I really appreciate all the help so far by the way.

---

### Post by Suger on 2005-12-14
I don't.

If you have enough space on the root partition, do a new try and follow the instructions step by step, without modifying anything except systematically replacing hoary with breezy. I think something went bad with your install and I'm at a loss. I installed quite a few chroots on amd64 ubuntu those past weeks and only had a problem when using symlinks for /chroot.

Sorry.

The other solution, which I tried to and you'll find somewhere in this forum (no time to look for it right now) is to run wine straight in the 64 bit world, but the maintainer of the wine package says it might make the system unstable. I never had any problems, but it's a little trickier and, for other programs, it might not work (acroread 32 and vlc 64have a conflict over some hard coded gtk path, for instance).

---

### Post by Septor on 2005-12-14
Is your $DISPLAY environment variable set?

after you chroot, try doing a "export DISPLAY=:0"

Also you don't need to use synaptic, just use apt-get if you are having problems.

---

