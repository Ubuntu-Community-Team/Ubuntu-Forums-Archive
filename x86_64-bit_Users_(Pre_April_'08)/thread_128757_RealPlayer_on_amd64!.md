---
title: "RealPlayer on amd64!"
date: 2006-02-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by Frafra on 2006-02-12
I read this: [https://wiki.ubuntu.com/FirefoxAMD64FlashJava]("https://wiki.ubuntu.com/FirefoxAMD64FlashJava").
I tryed the same think for RealPlayer:

[LIST=1]
[*]*Open gnome-terminal*
[*]wget [http://software-dl.real.com/121df63f3ad272b58506/unix/RealPlayer10GOLD.bin](http://software-dl.real.com/121df63f3ad272b58506/unix/RealPlayer10GOLD.bin)
[*]chmod +x RealPlayer10GOLD.bin
[*]export GTK_PATH=/usr/lib32/gtk-2.0 
[*]export PANGO_RC_FILE=/etc/pango32/pangorc
[*]linux32 RealPlayer10GOLD.bin
[*]*Close and open gnome-terminal*
[*]cd ~/RealPlayer
[*]gedit ./realplay
[*]*Add before the first line:*
export GTK_PATH=/usr/lib32/gtk-2.0 
export PANGO_RC_FILE=/etc/pango32/pangorc
[*]*Save and close it*
[*]./realplay
[/LIST]

The icons are bad, but it works good! Now I want use firefox32 with the RealPlayer plugins. When I try to play a video in gnome-terminal I see:

[...]
** ERROR **: file hxstatisticsobserver.cpp: line 100 (void make_gvalue(GValue*, int, const unsigned char*)): assertion failed: (utf8_val)
aborting...
/home/frafra/RealPlayer/realplay: line 78: 12665 Abortito                $REALPLAYBIN "$@"

How can help me?

ps. I've start it with:
[LIST=1]
[*]*Open gnome-ternimal*
[*]export PATH="/usr/local/bin:/usr/local/sbin:/sbin:/usr/sbin:/bin:/usr/bin:/usr/bin/X11:/usr/games:/home/**[USER]**/RealPlayer"
[*]firefox32 &
[/LIST]

---

### Post by Frafra on 2006-02-12
I've find a better way:

[LIST=1]
[*]*Read: [https://wiki.ubuntu.com/FirefoxAMD64FlashJava]("https://wiki.ubuntu.com/FirefoxAMD64FlashJava")*
[*]*Open gnome-terminal*
[*]wget [http://software-dl.real.com/121df63f3ad272b58506/unix/RealPlayer10GOLD.bin](http://software-dl.real.com/121df63f3ad272b58506/unix/RealPlayer10GOLD.bin)
[*]chmod +x RealPlayer10GOLD.bin
[*]export GTK_PATH=/usr/lib32/gtk-2.0
[*]export PANGO_RC_FILE=/etc/pango32/pangorc
[*]sudo mkdir /usr/local/realplayer32/
[*]sudo chmod -R **USER:USER** /usr/local/realplayer32/
[*]linux32 RealPlayer10GOLD.bin
[*]*When answer, insert: /usr/local/realplayer32/*
[*]*Close and open gnome-terminal*
[*]gedit /usr/local/realplayer32/realplay
[*]*Add before the first line:*
export GTK_PATH=/usr/lib32/gtk-2.0
export PANGO_RC_FILE=/etc/pango32/pangorc
[*]*Save and close it*
[*]sudo ln -s /usr/local/realplayer32/realplay /usr/bin/realplay
[/LIST]

Now you can use it with a simple *realplay* command.

---

### Post by Frafra on 2006-02-12
I've tryed a lot of sites that need Realplayer. Only few site doesn't work :) I think that we can make an how-to :)

---

### Post by kingcharles1666 on 2006-03-02
Hi, I tried the above but it does not work for me.
I did get the new firefox and flash working with the 
[https://wiki.ubuntu.com/FirefoxAMD64FlashJava]("https://wiki.ubuntu.com/FirefoxAMD64FlashJava")
method. but when i get to step:

9. linux32 RealPlayer10GOLD.bin

I get the message:
Extracting files for RealPlayer installation...Segmentatie fout
Segmentatie fout is dutch for: Segementation error

anybody knows what this means?
and how to fix

Many Thanks
Mico

---

### Post by JungleBeast on 2006-03-12
Sounds great! :D      

So has this worked for anyone? Did anyone make a HowTo for it in the end? 

Just got the flash and Java on firefox32 working and really eager to get realplayer working at last too!

---

### Post by John Jason Jordan on 2006-03-12
[QUOTE=JungleBeast]Sounds great! :D      

So has this worked for anyone? Did anyone make a HowTo for it in the end? 

Just got the flash and Java on firefox32 working and really eager to get realplayer working at last too![/QUOTE]
I have Firefox, RealPlayer and Flash all working together in my chroot environment. I installed all three there using Synaptic32. I tried for a long time to get them all working in the 64-bit world, but finally gave up, created a 32-bit chroot, and life has been a lot easier ever since.

One thing I discovered was that RealPlayer was initially not working. In order to fix it I uninstalled it and installed Firefox32 first, then reinstalled it. (Or did I do that the other way around -- too stupid to remember.) In any event, the secret was installing them in the right order; then the proper plugins get installed.

One thing I discovered was that 32-bit Firefox (and RealPlayer as well) cannot go anywhere on the internet when I change locations (e.g., take my laptop to school). I have to link /etc/resolv.conf to the /chroot/breezy/32bits/etc/resolv.conf file in order to get the new DNS entries into the chroot file.

---

