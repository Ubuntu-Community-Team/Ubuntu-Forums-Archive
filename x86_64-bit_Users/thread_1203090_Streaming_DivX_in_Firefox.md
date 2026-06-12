---
title: "Streaming DivX in Firefox"
date: 2009-07-02
forum: x86 64-bit Users
---

### Post by Sims12345 on 2009-07-02
Hi,

I am running Ubuntu 9.04 64bit and am having a bit of trouble with streaming DivX files in Firefox. Before I installed Adobe Flash I was able to stream almost all of them. Now, all I get is a black box that says 'waiting for video'

I have installed a bunch of plugins as well including the VLC one not pictured below. 


Thanks

---

### Post by Sims12345 on 2009-07-02
Solved by installing mplayer and the firefox thing for it

---

### Post by sldunn05 on 2009-07-02
yeah 
sudo apt-get install mplayer
sudo apt-get install mozilla mplayer

you also need to remove vlc and totem

sudo apt-get remove totem-mozilla mozilla-plugin-vlc

---

### Post by philinux on 2009-07-03
Thats odd. I did a google for divx clips and they all played, even HD, with the totem plugin. Mine is a default install.

---

### Post by Nightreaver1986 on 2009-08-11
Alright, so this doesn't seem to be working anymore. :(

I'm running a new install of Jaunty, still pretty clean save for a MU client that I put on there.

When I do sudo apt-get install mozilla mplayer, I get a warning message that it's missing a dependancy seamonkey and it won't be installed. So I go ahead and install seamonkey like it's wanting, and run the command again, and Ig et the same warning about seamonkey.

Tried the apt-get -f install to try fixing it, and the dpkg --configure -a, and still nada with it.

What is this seamonkey that mplayer is wanting?

---

