---
title: "openoffice &amp; japanese (scim) problem on ia64"
date: 2006-08-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by komuta on 2006-08-17
hi

since recently (don't know exactly when), I'm not able anymore to use SCIM with openoffice. I need it to write in japanese. When launched, openoffice prints this:

(soffice.bin:14042): Gtk-WARNING **: /usr/lib32/gtk-2.0/2.4.0/immodules/im-scim.so: cannot open shared object file: No such file or directory

(soffice.bin:14042): Gtk-WARNING **: Loading IM context type 'scim' failed

ia32 version of scim module isn't available in ia32-gtk package, and I can't figure out why openoffice isn't looking for the ia64 version. I'm pretty sure the whole thing used to work on my amd64 machine.

Can anyone help me ?

---

### Post by Mongoose on 2006-08-18
I know it's not exactly what you want, but I use im-ja for my Japanese input on AMD64.  You can use the debian im-ja source packages and just do a dpkg make and have AMD64 debs.  If you need more help doing this I can update the site, which I should do anyway.  ;)

Here's an old HOWTO I wrote for it as well:

[http://www.icculus.org/~mongoose/japanese.html](http://www.icculus.org/~mongoose/japanese.html)

---

### Post by Mongoose on 2006-08-22
In case you didn't notice -- I was subtlely implying you can do the reverse.  You could build the i386 package in a chroot for example and use it in your lib32.   =)

---

### Post by komuta on 2006-08-22
Thanks, but I'm not interessed in using another im. SCIM is ok for me, there's just an issue with openoffice on i64 arch, and I think it's an ubuntu issue, so it should be corrected. The problem is that right now I'm not 100% sure that it was working before, and if it was, before what upgrade, so I can't furnish a more precise disgnostic. Anyway, I may end up installing a 32bit ubuntu if I can't find any solution to this problem.

---

### Post by Mongoose on 2006-08-24
From my second post:

Build the i386 package for "it" -- being SCIM.

Also for others reading this thread you need to jump through some hoops to even get openoffice to do entry:

[http://www.mrbass.org/linux/mepis/japaneseinput/](http://www.mrbass.org/linux/mepis/japaneseinput/)

---

### Post by komuta on 2006-08-24
Well, my openoffice is already configured for japanese input, so I really think now it was working before some recent update.

---

### Post by uhu_maotouying on 2007-05-17
I just like to let you know that you are not the only one : 
I am with Ubuntu 6.06 LTS, Dapper, AMD x64 and I cannot input Chinese Characters to Ubuntu OpenOffice using SCIM .

It appears to me too that the 32 bit library im-scim.so went missing : 
When I call :	~$ ooffice --writer
It tells me :	(soffice.bin:10610): Gtk-WARNING **: /usr/lib32/gtk-2.0/2.4.0/immodules/im-scim.so: cannot open shared object file: No such file or directory

~$ aptitude search ia32-libs
i   ia32-libs                            - ia32 shared libraries for use on amd64 and ia6
i   ia32-libs-gtk                        - gtk+ ia32 shared libraries for with OpenOffice
p   ia32-libs-kde                        - KDE ia32 shared libraries for with OpenOffice.
i   ia32-libs-openoffice.org             - ia32 shared libraries for with OpenOffice.org
p   ia32-libs-sdl                        - ia32 shared libraries of sdl related packages

Please advise ...

---

### Post by uhu_maotouying on 2007-05-17
... I have added the missing 
im-scim.so
(from my 32 bit laptop installation), 
however then 'ooffice --writer' told me that there were other libs missing like 
libscim-1.0.so.8 
libscim-x11utils-1.0.so.8 
At this point I have to give up, because I have no clue what I am doing ;-)

I have filed (undecided)  Bug #115234,

---

### Post by aikishugyo on 2007-05-17
Hmm, why don't you first see if you can put in any Japanese at all in OpenOffice? I had problems in Debian Etch a year ago and they were related to OO, not to the Japanese input. In that case, there's not much you can do to fix it yourself unless you go into OO coding (gulp!).

So, I am using Anthy-UIM on Ubuntu and Debian for more than 2 years now. It works, no doubt about it. Give it a go, and if it works, uninstall the packages. I can tell you I could not get SCIM to work very well...

Install uim, anthy, uim-anthy and uim-applet-gnome. Probably you will get uim-common and uim-utils added as well. Then go to the taskbar, right click to add new item and look for the UIM applet (switcher) in the selection. Add it to the taskbar, and configure it (right click) to show all the various options. Then set it to anthy (the only other option is "direct") and shift-space should switch between english and japanese (or you can use the mouse to select input choices from the pulldown menus).

If that works, then probably you can get scim to work also, and at least you have a workable fallback.
Good luck!

---

### Post by ububuL on 2007-05-18
I am using scim with OpenOffice and it works fine under 64 bit feisty. I don't remember where I found my solution. Basically, you need to tell OpenOffice suite to use scim-bridge. I put the steps in a script. 
```
wget http://shanren.bol.ucla.edu/linux/fixooffice.sh
```
```
chmod 744 fixooffice.sh
```
```
./fixooffice.sh
```
Hopefully, it works for you.

---

### Post by uhu_maotouying on 2007-05-18
thanks ububuL ...
... sadly, it does not do the trick with my Dapper 6.06 LTS :-((

---

### Post by Mongoose on 2007-05-18
I now use scim too -- since I don't have to make amd64 package for it all the time.  Openoffice in edgy and fiesty work fine with it for my Japanese IME.  I just use canna, but it doesn't matter as long as you follow that guide and setup OpenOffice -- as for LTS I'm not sure if it supports 64bit scim with OpenOffice.  You might have to install i386 packages into your lib32.  If you're really in a rush you can dump the packages into /tmp and copy what you need over into lib32, however I know edgy at least had a full scim-lib32 at one point.

---

