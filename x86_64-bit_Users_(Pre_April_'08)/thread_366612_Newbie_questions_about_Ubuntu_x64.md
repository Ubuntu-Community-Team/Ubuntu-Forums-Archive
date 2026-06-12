---
title: "Newbie questions about Ubuntu x64"
date: 2007-02-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by JKoder on 2007-02-21
Hello.
Today i will install Ubuntu 64 bit edition.
I am a programmer so i dont play games :D. My question related ti this 64bit edition is:

1. The synaptic repositories are ALL 64 bit ? or they are the default ubuntu repositories ( 32 bit )
2. Can anyone share his/her experience using Ubuntu 64 ( Pros / Cons )
3. Kernel compilink is different ?
4. Gcc and stuff for C programming , can i find all of this in Synaptic , and will they be on 64 bit ?


Thank you and excuse me for my newbie questions :(

---

### Post by Spr0k3t on 2007-02-21
#2,

For the most part it was an easy install and update with a few minor problems with the kernel and nVidia.  I've got Flash 9 installed thanks to the help of Kilz script for FireFox32.  For the most part, everything that has worked on my Pentium4 was just as easy or had a decent workaround for it.  64bit is definately the way to go, eventually there will be better support for 64bit.  In the days of the 16bit OS to the 32bit OS it didn't happen in a span shorter than two years, so I don't see the overall change happening immediately.

---

### Post by JKoder on 2007-02-21
> **Spr0k3t said:**
> #2,

For the most part it was an easy install and update with a few minor problems with the kernel and nVidia.  I've got Flash 9 installed thanks to the help of Kilz script for FireFox32.  For the most part, everything that has worked on my Pentium4 was just as easy or had a decent workaround for it.  64bit is definately the way to go, eventually there will be better support for 64bit.  In the days of the 16bit OS to the 32bit OS it didn't happen in a span shorter than two years, so I don't see the overall change happening immediately.

Thank you!.
Hopefully i will compile a new kernel 2.6.20 since i did it one on Slackware.
My videocard is Ati Radeon Xpress 1100 but i think ( hopefully) i will not have problems with it .
Thank you !

---

### Post by Kilz on 2007-02-21
> **JKoder said:**
> Thank you!.
Hopefully i will compile a new kernel 2.6.20 since i did it one on Slackware.
My videocard is Ati Radeon Xpress 1100 but i think ( hopefully) i will not have problems with it .
Thank you !

ATI has pretty good linux support. Not as good as Nividia, but they do make video drivers. If you need aceleration you will need to use the proprietary driver. If you are installing Edgy, [here is a good guide]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide") on how to install the proprietary drivers (method 2).

---

### Post by JKoder on 2007-02-21
> **Kilz said:**
> ATI has pretty good linux support. Not as good as Nividia, but they do make video drivers. If you need aceleration you will need to use the proprietary driver. If you are installing Edgy, [here is a good guide]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide") on how to install the proprietary drivers (method 2).

Really appreciate it Thank you !

---

### Post by Kilz on 2007-02-21
> **JKoder said:**
> Really appreciate it Thank you !

Your welcome. One of the best parts about Ubuntu is helping :KS

---

### Post by kuja on 2007-02-21
> **JKoder said:**
> Hello.
Today i will install Ubuntu 64 bit edition.
I am a programmer so i dont play games :D. My question related ti this 64bit edition is:

1. The synaptic repositories are ALL 64 bit ? or they are the default ubuntu repositories ( 32 bit )
2. Can anyone share his/her experience using Ubuntu 64 ( Pros / Cons )
3. Kernel compilink is different ?
4. Gcc and stuff for C programming , can i find all of this in Synaptic , and will they be on 64 bit ?


Thank you and excuse me for my newbie questions :(
#1: They're 64-bit
#2: Smooth as silk
#3: No, kernel compilation is the same
#4: That stuff is all there, and it's 64-bit.

---

### Post by JKoder on 2007-02-23
> **kuja said:**
> #1: They're 64-bit
#2: Smooth as silk
#3: No, kernel compilation is the same
#4: That stuff is all there, and it's 64-bit.

Many many thanks !!!!
One more thing. Have any ideea how to disable de Ubuntu spalsh screen suince it's abit ugly , i mean is blak and white and the progress bar is messed up ?

But any way BIG THANK's

---

### Post by John Jason Jordan on 2007-02-23
> **JKoder said:**
> Many many thanks !!!!
One more thing. Have any ideea how to disable de Ubuntu spalsh screen suince it's abit ugly , i mean is blak and white and the progress bar is messed up ?
But any way BIG THANK's
Once you have it installed and running, go into System > Administration > Update Manager. You will probably find a lot of new stuff. Some of it will fix that splash screen.

If it does not, do this:

Open a terminal and type 

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.old

This makes a backup copy of your menu.lst file named menu.lst.old. Remember that you did this just in case the following renders your computer unbootable. If it does, use the live/install CD to delete the new version of the file you are going to make and rename menu.lst.old as menu.lst. Then type

sudo gedit /boot/grub/menu.lst

Give it your root password. When Gedit opens with the menu.lst file find the first place where it lists the items that appear in your boot menu. It should look something like:

## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=8348ba8b-3f9f-455b-8213-a9491374ea9f ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
savedefault
boot

Change the end of your kernel line so it says "ro quiet splash" at the end like mine does and save the file. DON'T CHANGE ANYTHING ELSE IN THE FILE, even if it is different from mine.  

When you reboot you will have no splash screen at all.

---

### Post by dfreer on 2007-02-23
To change your boot splash screen use usplash. [*_gnome-look.org_*]("http://www.gnome-look.org") has some great splash screens that you can download, I am currently using this one:
[*_Fingerprint_*]("http://www.gnome-look.org/content/show.php?content=50468")

This site helps you install the fingerprint splash, although you could easily install any other one using this guide.
[*_Fingerprint usplash Installation_*]("https://sourceforge.net/docman/display_doc.php?docid=40914&group_id=187765")

To complete get rid of splash, I believe all you need to do is edit your /boot/grub/menu.lst file.
Scroll down to the kernel entry that you wish to modify (newest kernel likely to be the topmost one. Simply remove the word "splash" and reboot your machine :D Hope that helps!

---

