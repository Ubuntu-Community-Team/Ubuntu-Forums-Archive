---
title: "Undefined video mode number: 31c"
date: 2008-11-23
forum: x86 64-bit Users
---

### Post by JeyPeyy on 2008-11-23
I've posted this in general help, but it doesn't seems like you get much attention there.

When booting up Ubuntu, before X starts, I get this message:

> 
Starting up...
Undefined video mode number: 31c
Press <ENTER> to see video modes available, <SPACE> to continue, or wait 30 seconds

If I press enter, I get a list of video modes, and I have to choose one. If I press space Ubuntu boots up, but it takes about 6 times more time than before.

I've tried recovery mode and xfix, but it haven't helped me out.

I can still use my computer, but it's a bit annoying that I have to wait that long and that I can't use compiz-fusion.

---

### Post by twisted_steel on 2008-11-23
I haven't seen this before, but can you post what video card you are using?  Also, if you've made any changes to your xorg.conf, post the /etc/xorg.conf file.  Have you edited your grub configuration to add a "vga=" line?  That seems to be the recurring theme of similar posts I've found.

As far as getting responses to threads, it can take a while because you just have to have the right person come along at the right time.

---

### Post by twisted_steel on 2008-11-23
Did you try the steps in this thread [http://ubuntuforums.org/showthread.php?t=846245?](http://ubuntuforums.org/showthread.php?t=846245?)  It looks like that helped at least 2 people.

---

### Post by Yellow Pasque on 2008-11-23
Open your grub config file for editing:
```
gksudo gedit /boot/grub/menu.lst
```
Add vga=785 to the "kernel" line. For example, make it look like:
```
kernel		/boot/vmlinuz-2.6.27-7-generic root=<your UUID> ro quiet splash vga=785
```

Note that 785 is the code for 640x480-16 bit. If you want a different mode for your terminals, use codes in this table: [http://www.mepis.org/node/2992](http://www.mepis.org/node/2992)

---

### Post by JeyPeyy on 2008-11-23
Ok, I don't get the message anymore. But it stills takes time to boot and I can't get the desktop effects working right. Maybe that's another problem(?)

---

### Post by maxpoweron on 2008-12-17
I had the same problem as you.  But today I found a fix at _[http://www.ubuntu-art.org]("http://www.ubuntu-art.org/content/show.php/usplash+chrome+new?content=94965")_ while searching for a new splash screen.  

Thanks to **elfrench** who had directions for resolving widescreen issues on his post.

First you need hwinfo installed.  

[INDENT]**sudo apt-get install hwinfo**[/INDENT]

After it is installed you run hwinfo with the framebuffer switch.

[INDENT]**sudo hwinfo --framebuffer**[/INDENT]

Look for you monitor resolution for the splash screen (mine is 1280x1024 at 16bits).  For me, that number is 0x031a.

Then you want to edit your grub menu list.

[INDENT]**sudo gedit /boot/grub/menu.lst**[/INDENT]

Search for "vga=" (without quotes) and change the value of 796 to 0x031a.

Hope that helps!

---

