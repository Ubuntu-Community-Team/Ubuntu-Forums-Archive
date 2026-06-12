---
title: "Move World of Warcraft from my Windows Install to my Ubuntu Install?"
date: 2008-04-18
forum: Wine
---

### Post by tigerplug on 2008-04-18
Hey guys, 



This is a bit of a crazy question but I have a laptop with two partitions.

One is NTFS with Vista and WOW installed.


The has the Linux filesystem with Ubuntu installed.

I was wondering is it possible to move my world of warcraft over to ubuntu and if not is it possible to play the current installation  from ubuntu and how?


;)

---

### Post by thisismalhotra on 2008-04-18
> **tigerplug said:**
> Hey guys, 



This is a bit of a crazy question but I have a laptop with two partitions.

One is NTFS with Vista and WOW installed.


The has the Linux filesystem with Ubuntu installed.

I was wondering is it possible to move my world of warcraft over to ubuntu and if not is it possible to play the current installation  from ubuntu and how?


;)

It is actually really easy and I have done that.

Just copy your whole World of Warcraft folder (caution can be as big as 8gb with patches and stuff) from C:/Program Files on vista to /wine/path I don't remember/Program Files in Ubuntu and than modify teh config.wtf files as in this link and do the registry change etc etc.

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

**Also, remember to use Windows XP settings when in ubuntu as Windows Vista settings of wine are a bit bugged (atleast in my experience)**

For the Horde:popcorn:

---

### Post by synapse13 on 2008-04-18
Remember to remove any Windows-specific addons if you do this.  If you find that you run into trouble, it is actually quite easy to do a fresh install of WoW on Windows too.  I got it working on my Xubuntu box, and after configuring my video drivers through Envy I actually get slightly better performance than on XP.
Check this out for a fresh install, if you so desire:
[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

---

### Post by thisismalhotra on 2008-04-19
> **synapse13 said:**
> Remember to remove any Windows-specific addons if you do this.  If you find that you run into trouble, it is actually quite easy to do a fresh install of WoW on Windows too.  I got it working on my Xubuntu box, and after configuring my video drivers through Envy I actually get slightly better performance than on XP.
Check this out for a fresh install, if you so desire:
[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

I dont know if it's just me but all the mods to WoW which are installed by just copying stuff to the interface folder will work in linux under wine. That is the case with me and few other buddy who play WoW on linux.

---

### Post by tnl2k7 on 2008-04-19
Wouldn't it work just installing the game in Wine then copying the saved games folder (don't know the path to this, sorry) to the Wine Program Files folder?

---

### Post by daemonfly on 2008-04-19
Imho, copying over is a lot easier and faster. If you install new, then you have to go through the whole patching process. If you just copy over, it's already fully patched and you keep all your personal settings. All you have to do is just a quick edit to config.wtf.

I did it just today actually. Installed wine, copied over WoW, and added the 3 lines to config.wtf.  I have compiz enabled, so get lower performance, so next step would be to get it to run in it's own X session (which I haven't read up on yet).

---

