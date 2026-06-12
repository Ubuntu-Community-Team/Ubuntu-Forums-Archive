---
title: "amd64 unresolved dependency issues, mplayer-amd64, vlc, TONS more"
date: 2006-01-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by digitalsy on 2006-01-27
I just installed Breezy 64bit on my new AMD64 System. Installation was a breeze (pun intended) and I booted into a completely (for the most part) operational OS, which was nice. I'm coming from Gentoo so the speed of installation was far greater. Anyway after uncommenting the lines for universe and multiverse and commenting out the cd source I let the synaptic manager update the system. It updated everything without error and asked me to reboot (new kernel). I booted up perfectly and had no problems.

Now I'm trying to install say mplayer-amd64 and I run into unresolved dependency issues involving aalib and a slew of other things (at work now, can't paste exact error). What I noticed is there is no package for aalib...but there is one for libaa. Why does mplayer-amd64 depend on the deprecated package? VLC won't install either, and neither will a TON of other things - same unresolved dependency issues. I NEVER had this problem in Gentoo and even when I used Debian prior,  I never had it THIS bad. How do I fix these unresolved depency issues, because honestly a large chunk of whatever's in the repositories will not install for me, either through synaptic or command line. 
'
I don't this this is normal either because I've read many others on the forums that DO have mplayer-amd64 and vlc, etc installed.  

Please help. I'm not a n00b to linux, just a n00b to 64bit....

Thanks,
digi

---

### Post by uniko on 2006-01-27
You might want to install mplayer, not the mplayer-amd64 package which is older btw. 
I installed VLC from dapper's packages, downloading every needed package separately depending on dependancy issues :) Although I originally installed the breezy version, but it wasn't compiled against gtk, so that why  the dapper version.

I'm sure you did try apt-get update before trying to install the packages, but I usually do it anyway everytime I'm about to install anything new.

---

### Post by digitalsy on 2006-01-27
Yeah definately tried apt-get update. But it just seems like if I randomly search through the sections in synaptic and pick something to install maybe 6 or 7 things out of 10 will fail because of unresolved dependencies. This can't be normal. How did things get so b0rked on my system, all I did was install, upgrade then realized I needed to change sources.list then updated again and upgraded again. Now things that I really want won't install...

---

### Post by digitalsy on 2006-01-27
[QUOTE=uniko]You might want to install mplayer, not the mplayer-amd64 package which is older btw. 
I installed VLC from dapper's packages, downloading every needed package separately depending on dependancy issues :) Although I originally installed the breezy version, but it wasn't compiled against gtk, so that why  the dapper version.

I'm sure you did try apt-get update before trying to install the packages, but I usually do it anyway everytime I'm about to install anything new.[/QUOTE]

I just tried installing mplayer (non amd64 version) and I get unresolved dependency issues with that as well.

mplayer:
 Depends: libdirectfb-0.9-22  but it is not installable
 Depends: libggi2 (>=1:2.0.5) but it is not installable
 Depends: libglib1.2 (>=1.2.0) but it is not installable
 Depends: libgtk1.2 (>=1.2.10-4) but it is not installable
 Depends: libjack0.80.0-0 (>=0.99.0) but it is not installable
 Depends: libmad0 (>=0.15.1b) but it is not installable
 Depends: xmms (>=1.2.10+cvs20050209) but it is not installable

Here's what I get with mplayer-amd64
mplayer-amd64:
 Depends: aalib1 (>= 1.2)
 Depends: libdirectfb-0.9-22  but it is not installable
 Depends: libggi2 (>=1:2.0.5) but it is not installable
 Depends: libglib1.2 (>=1.2.0) but it is not installable
 Depends: libgtk1.2 (>=1.2.10-4) but it is not installable
 Depends: libmad0 (>=0.15.1b) but it is not installable
 Depends: libstdc++5 (>=1:3.3.4-1) but it is not installable
 Depends: xmms (>=1.2.10+cvs20050209) but it is not installable

---

### Post by digitalsy on 2006-01-27
Not sure how it happened but I *think* my sources.list was incomplete despite having copied it exactly from one of the other threads. I thought of this because seaching through the ubuntu packages on the web I found all of the packages that many packages were complaining were "not installable". I ended up copying the sources list from here -> [http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php) and apt-get update and now it seems to have successfully installed mplayer-amd64! YAY!

---

### Post by kelleychambers on 2006-01-29
[QUOTE=digitalsy]Not sure how it happened but I *think* my sources.list was incomplete despite having copied it exactly from one of the other threads. I thought of this because seaching through the ubuntu packages on the web I found all of the packages that many packages were complaining were "not installable". I ended up copying the sources list from here -> [http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php) and apt-get update and now it seems to have successfully installed mplayer-amd64! YAY![/QUOTE]


THank you!!  I was having serious sources.list problems and the link you gave me solved them!!!  Great post...

---

