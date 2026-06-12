---
title: "Skip GRUB Screen - 9.10"
date: 2009-11-01
forum: x86 64-bit Users
---

### Post by CodyT07 on 2009-11-01
A Happy Karmic user here :)
I have ubuntu installed on my laptop and it is mainly used by my parents for Internet browsing and that is it. I would like Karmic to skip the grub screen for selecting kernels and go straight for the default. 
In case it matters I have a hidden partition on my laptop. It is a windows vista recovery partition (I left it on there as a 'just in case.')

OS Ubuntu 9.10 Karmic Koala 64 bit.

---

### Post by Photonic Nature on 2009-11-01
> **CodyT07 said:**
> A Happy Karmic user here :)
 I would like Karmic to skip the grub screen for selecting kernels and go straight for the default. 



Open a terminal window and type the following:

***sudo nautilus***

This will open your file browser as root.
[LIST=1]
[*]click on File System
[*]Click the arow next to boot
[*]Click the arrow next to grub
[*]Right click on menu.lst
[*]Left click Copy
[*]Right click on grub and left click on paste
[/LIST]

This will make a backup copy: ***menu (copy).lst***
So if you goof up your grub menu and your machine will not boot, you can later (using a live cd), delete menu.lst and rename ***menu (copy).lst*** to ***menu.lst***
Which will get you back to where you started.

Now let's continue...
**_Only change the following in the menu.lst file._**

With your file browser that is still open...
Double click menu.lst to open it in gedit as root.

Scroll down (not very far from top) to the second entry without a # or ## in front of it which will be ***timeout*** and change the value to 0 (that is a zero).

and  the next item down... remove the # before ***#hiddenmenu*** 

Now click on the save icon up top and then close your gedit, nautilus, and terminal windows.
The terminal being the last one to close.

Restart your machine... your wish is your command

enjoy.:D

---

### Post by zzzBrett on 2009-11-02
Correct me if I'm wrong, but I think these instructions work for GRUB Legacy.  If OP is a Karmic user, I assume he has GRUB 2.

---

### Post by jespdj on 2009-11-02
There is no **menu.lst** anymore with the new version of GRUB that's in Ubuntu 9.10.

---

### Post by skotos on 2009-11-02
Well, whether you are a Jaunty or a Karmic user, there is an easy GUI that can be run to change some startup/login settings: **StartUp-Manager**.

It is available in the standard repositories and works well with both versions of GRUB.

To change the delay, you can look at the first tab - *Boot options* - and change the first item - *Timeout in seconds* - accordingly.

If I remember well, setting it to *0* should be a wait forever value. You should probably set it to *1*.

HTH.

---

### Post by hkkea on 2009-11-02
Don't know how to disable boot menu after installation. a simply way is change the time out period to as short as possible, say 1 sec. You can edit file /etc/default/grub and change the value of GRUB_TIMEOUT, after you done it run command 'sudo update-grub'. It will take effect next time you boot up your machine...

---

