---
title: "Problems with DVD Menus"
date: 2006-08-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by deboring21 on 2006-08-25
Well I am trying to play DVDs on my pc and when I get it all ready, then menu comes up, but I can't select anything. I've tried MPlayer, Xine, Totem, TLC, and a couple other movie players, but nothing works. Oh yeah, I do have the DVD codecs loaded and everything. The wierd thing is that I can use the menus and everything on WinXP, but not on my new system. If you need anymore info, just ask and I will reply ;)
-Ryan

---

### Post by Lonthong on 2006-08-25
What I did was:
Enable universe & multiverse
Install Totem-xine (It automatically uninstall Totem-gstreamer) & libxine-extracodecs
install the debhelper, build-essential and fakeroot packages
apt-get install liba52-0.7.4-dev libdvdread3-dev libdvdnav-dev
sudo /usr/share/doc/libdvdread3/examples/install-css.sh

---

### Post by ColinG on 2006-08-25
What about VLC - that plays menus ok and is a very nice multimedia player as well.

---

### Post by deboring21 on 2006-08-25
I tried VLC last night and that was still a no go with the menus. I'll try the other suggestion when I get home...
-Ryan

---

### Post by ColinG on 2006-08-25
VLC requires a specific plug-in. It is called dvdnav if I recall correctly.

Colin

---

### Post by Ausus on 2006-08-26
Hi Lonthong,

I have problems obtaining the packages you mentioned.
These are the packages:
libxine-extracodecs and libdvdnav-dev

Playing dvd is still out.
I followed the restricted installation guide, for AMD 64 platform.:idea: 

Regards

---

### Post by Lonthong on 2006-08-27
> **Ausus said:**
> Hi Lonthong,

I have problems obtaining the packages you mentioned.
These are the packages:
libxine-extracodecs and libdvdnav-dev

Playing dvd is still out.
I followed the restricted installation guide, for AMD 64 platform.:idea: 

Regards

Have you enabled universe multiverse ?

---

### Post by Ausus on 2006-08-27
Hi Lonthong,

Yep all enabled.
After all the installations I managed to get it working.
Dont know who solved it from which suggestions.

Tnx for all the replies.

regards

---

