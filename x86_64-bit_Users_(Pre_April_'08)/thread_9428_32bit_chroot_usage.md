---
title: "32bit chroot usage"
date: 2004-12-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by Dylanby on 2004-12-28
To those people that are running a 32bit chroot on AMD64.

Could you please post some examples on how you install **native** Linux games & apps into your chroot & then how you go about launching them?

For example, I have the AMD64 Firefox installed, but would also like to install Firefox x86 w/Flash into my chroot (easy part). Then create a launcher for my 'Applications' menu labeled Firefox32 or something similar.

Also, I would like to install RTCW into my 32bit chroot. Can I just start the installation from within /var/chroot/home?

---

### Post by ahyden on 2004-12-28
You can type dchroot -d "command" and it executes that command in the chroot.

I have this script do_chroot in /usr/local/bin:
#!/bin/sh
/usr/bin/dchroot -d "`echo $0 | sed 's|^.*/||'` $*"

Then I create a symbolic link from that to the command I want to execute in the chroot, e.g.:
ln -s /usr/local/bin/do_chroot /usr/local/bin/firefox
which will execute firefox in the chroot environment when I launch it in my normal 64 bit environment. To launch my amd64 firefox I can type /usr/bin/firefox.

Instead if you want you can just create a script for launching the 32bit firefox e.g.:
#!/bin/bash
dchroot -d "firefox"

put it in /usr/local/bin and add it to the gnome menu.

If you're going to start a program that only works in 32bit, first type dchroot -d and you'll be in the 32 bit environment.

---

### Post by xpt on 2005-01-23
[QUOTE=ahyden]I have this script do_chroot in /usr/local/bin:
....[/QUOTE]

Excellent! Thanks a lot!!

---

### Post by s_p_a_r_k_y on 2005-01-23
On a similar note. I have xine with 32bit wincodecs but no sound in my chroot...Is there a way to get sound in a chrooted environment? I'm not to familier with them and this is my first forray into chrooted environment. If anyone has any idea please let me know.

---

### Post by Dylanby on 2005-01-24
I also have gxine installed in my chroot. I do get sound from it.

I know that with Cedega & some games I installed into the chroot I have to use OSS.
If I use ALSA in the chroot with those games I get no sound.

With gxine the sound driver is set to auto, so I'm not sure what driver it's actually using. I have the alsa-oss compatibiltiy library installed in my chroot. Not sure if that matters.

---

### Post by s_p_a_r_k_y on 2005-01-24
Do I have to have the same /dev directory in the chroot as the normal system?

---

### Post by xpt on 2005-01-24
[QUOTE=s_p_a_r_k_y]Do I have to have the same /dev directory in the chroot as the normal system?[/QUOTE]
 To whoever want to answer this question, please follow up and answer here. 

[http://www.ubuntuforums.org/showthread.php?t=2740&highlight=chroot](http://www.ubuntuforums.org/showthread.php?t=2740&highlight=chroot)

---

### Post by Tichondrius on 2005-01-31
[QUOTE=ahyden]You can type dchroot -d "command" and it executes that command in the chroot.

I have this script do_chroot in /usr/local/bin:
#!/bin/sh
/usr/bin/dchroot -d "`echo $0 | sed 's|^.*/||'` $*"

Then I create a symbolic link from that to the command I want to execute in the chroot, e.g.:
ln -s /usr/local/bin/do_chroot /usr/local/bin/firefox
which will execute firefox in the chroot environment when I launch it in my normal 64 bit environment. To launch my amd64 firefox I can type /usr/bin/firefox.

Instead if you want you can just create a script for launching the 32bit firefox e.g.:
#!/bin/bash
dchroot -d "firefox"

put it in /usr/local/bin and add it to the gnome menu.

If you're going to start a program that only works in 32bit, first type dchroot -d and you'll be in the 32 bit environment.[/QUOTE]


doesn't this script strip out the path before executing the command under chroot ?  So how would the command be executed if it doesn't happen to be on the path  ? isn't it simpler to create a special script in the 64 env (e.g. /usr/local/bin/firefox32) which does dchroot and executes the proper pathname in the 32 bit env ? This way nothing depends on default path being inter mingled between two different environments.

Actually, for firefox, why not just install the 32 bit firefox in the 64 bit env, and execute it normally ? why you need chroot for firefox ?!?

---

### Post by valadil on 2005-02-01
32 bit firefox will look for 32bit libs and not be able to find them.  

I followed that tutorial to the letter when setting up my chroot up until the point where you use the do_chroot script.  Instead of that I just type dchroot -d and then I get a bash shell within the chroot.  From there I run my 32 bit programs.

To get alsa to work in your chroot you do need to mount -o bind /dev to your chroot's dev (this is explained better in the tut that was posted).  You also need to modprobe snd_ioctl32.

---

### Post by lean on 2005-02-06
When I try dchroot evolution (or any other X program) i get:
Gtk-WARNING **: cannot open display:

---

### Post by Dylanby on 2005-02-07
Do you type:```
 dchroot **-d** <appname>
``` ?

---

### Post by xpt on 2005-02-16
[QUOTE=lean]When I try dchroot evolution (or any other X program) i get:
Gtk-WARNING **: cannot open display:[/QUOTE]

I think you forgot the -d, which is very important...

---

