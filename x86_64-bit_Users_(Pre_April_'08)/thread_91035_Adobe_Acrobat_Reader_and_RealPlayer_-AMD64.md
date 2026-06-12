---
title: "Adobe Acrobat Reader and RealPlayer -AMD64"
date: 2005-11-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by jahLux on 2005-11-16
Has anyone sorted out the installation of Adobe Acrebat Reader 7.0 and RealPlayer 10 for the Ubuntu-AMD64 platform? If so, please share your knowledge and insight.
Selah.

---

### Post by pjs_flyer on 2005-11-16
I've got acrobat sorted - just about to try and do Realplayer!  I've used the chroot approach (there's a howto somewhere on here), so although its not ideal, I can use acrobat if for some reason none of the other pdf viewers work

---

### Post by pjs_flyer on 2005-11-16
...and Realplayer 10 works too!

---

### Post by vishnumrao on 2005-11-19
Could you shed some light on how you got adobe and real working? 

Thanks,
Vishnu Rao.

---

### Post by pjs_flyer on 2005-11-19
What I did was to install the chroot environment (effectively a 32bit environent in my 64bit world) using [http://ubuntuforums.org/showthread.php?t=24575](http://ubuntuforums.org/showthread.php?t=24575) (just replace "Hoary" with Breezy"). This gives you your 32 bit environment and firefox32.

I then created a new menu item called Synaptic 32 with the command line "gksudo synaptic32" and an icon from /usr/share/pixmaps

Next, just launch synaptic32 and install acroread, acroread-plugins and mozilla-acroread.  I then opened a terminal and did the following:

# dchroot -d
# sudo ln -s /usr/sbin/acroread /usr/sbin/acroread32
# exit
# sudo ln -s /usr/local/bin/do_dchroot /usr/local/bin/acroread32

The first line puts you into your 32bit environment, the next creates the symlink with the 32bit name, the third gets you back to the "normal" environment, and the fourth creates the link to the 32bit acroread from the 64bit system (the only problem I've got is that I have to accept the agreement every time I launch - any tips on how to stop this welcome!)

For realplayer, you can either launch the old version through synaptic32, or download the new version from the website.  Right click on the file, click on properties, go to permissions, and check the "execute" boxes.  Next, open a terminal, type "dchroot -d" to get into a 32bit environment, move to wherever the realplayer file is, then type ./realplayer10gold.bin and follow the instructions (I think there's a howto on here somewhere, but I can't find it). Then, whilst you're still in the 32bit shell, type

# sudo ln -s /usr/sbin/realplay /usr/sbin/realplay32
# exit
# sudo ln -s /usr/local/bin/do_dchroot /usr/local/bin/realplay32

Then, just add to the menu in the same way as for acroread32.

Enjoy!

---

### Post by jahLux on 2005-11-20
Thanks much, but I was hoping for something less intimidating than "chroot-ing". I guess I'll just wait around till that 'something' comes along . . .

---

### Post by pjs_flyer on 2005-11-20
Trust me, if you follow the instructions in the howto, it is straightforward - Breezy is my first Ubuntu distro (and I didn't try anything adventurous in my last one, Suse) - and getting chroot to work and seeing working flash sites in firefox is deeply satisfying!

---

### Post by prem_mallappa on 2005-12-06
I found pretty much interesting one, without chroot. if you have ia32-libs installed which default i think.

for more steps to follow here
[http://lists.debian.org/debian-amd64/2005/05/msg00707.html](http://lists.debian.org/debian-amd64/2005/05/msg00707.html)

---

### Post by rplantz on 2005-12-06
I think there's an error here:

[QUOTE=pjs_flyer]

# dchroot -d
# sudo ln -s /usr/sbin/acroread /usr/sbin/acroread32
# exit

[/QUOTE]

Since acroread got installed in /usr/local/bin:
```

bob@robert:~$ dchroot -d
Executing shell in 'breezy' chroot.
bob@robert:~$ which acroread
/usr/bin/acroread

```
(on my system), I needed to do:
```

bob@robert:~$ dchroot -d
Executing shell in 'breezy' chroot.
bob@robert:~$ which acroread
/usr/bin/acroread
bob@robert:~$ sudo ln -s /usr/bin/acroread /usr/bin/acroread32
bob@robert:~$ exit
exit

```

I haven't installed RealPlayer, but I'm confident that a similar process will work.

---

### Post by leetcharmer on 2006-01-31
I'm running into a problem with the realplayer under chroot.

> ./RealPlayer10GOLD.bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

---

### Post by ASaidi on 2006-08-03
In recent releases of ia32-libs-gtk you need to add the following lines to /usr/bin/acroread for it to work without a chroot:
PANGO_RC_FILE=/etc/pango32/pangorc
export PANGO_RC_FILE

---

### Post by zparihar on 2006-09-11
I'm running into a problem with the realplayer under chroot.
 
 
Quote:
 ./RealPlayer10GOLD.bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory 



Do this:

$    sudo apt-get install libstdc++5

---

