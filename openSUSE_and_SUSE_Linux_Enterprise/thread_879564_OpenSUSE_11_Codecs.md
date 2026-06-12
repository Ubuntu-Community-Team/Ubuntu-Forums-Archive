---
title: "OpenSUSE 11 Codecs"
date: 2008-08-04
forum: openSUSE and SUSE Linux Enterprise
---

### Post by Vince4Amy on 2008-08-04
Need a little advise, I have no idea how to get mp3 or anything working on OpenSUSE 11. I have these formats working through Firefox using gnome-mplayer. But I don't actually have any working codecs for either Amarok or Exaile. 

I found this:

[http://opensuse-community.org/Restricted_Formats/11.0](http://opensuse-community.org/Restricted_Formats/11.0)

But it doesn't work for me. I'm using 64-Bit OpenSUSE 11.0 with KDE 3.5.

---

### Post by Growbag on 2008-08-04
Well, mp3 should play "out of the box", it did for me.  I used the DVD to install though, maybe the liveCD is different.

To add codecs:

Run yast (Administrator settings) from your menu, select "Software Repositories" from the "Software" tab, then click on "Add".

In the next frame, click "Community Repositories" and then "Add".

Select the standard ones, and any others you are interested in.  Make sure you select "Packman" and "Videolan".

Finish that, then go to the "Software Management" icon and search for "codec".  You might want to select "rpm provides" before searching.

You should find a package called "w32codecs-all".

---

### Post by Vince4Amy on 2008-08-04
Yes I used the DVD Version too. Okay thanks I'll give it a go.

---

### Post by 67GTA on 2008-08-04
You will also want to change Amarok's engine from yauap to xine. An easy way to get everything multimedia related in one click: [http://opensuse-community.org/Multimedia](http://opensuse-community.org/Multimedia) Opensuse's version of amarok is crippled. The pacman version will play anything you throw at it.

---

### Post by lxuser2008-X on 2008-08-06
[http://en.opensuse.org/Package_Repositories](http://en.opensuse.org/Package_Repositories)

Official Repositories

[http://download.opensuse.org/distribution/11.0/repo/oss/](http://download.opensuse.org/distribution/11.0/repo/oss/)
[http://download.opensuse.org/distribution/11.0/repo/non-oss/](http://download.opensuse.org/distribution/11.0/repo/non-oss/)
[http://download.opensuse.org/update/11.0/](http://download.opensuse.org/update/11.0/)

[http://download.opensuse.org/distribution/11.0/repo/src-oss/suse/](http://download.opensuse.org/distribution/11.0/repo/src-oss/suse/)
[http://download.opensuse.org/distribution/11.0/repo/src-non-oss/suse/](http://download.opensuse.org/distribution/11.0/repo/src-non-oss/suse/)

[http://download.opensuse.org/distribution/11.0/repo/debug/](http://download.opensuse.org/distribution/11.0/repo/debug/)


[http://download.opensuse.org/distribution/10.3/repo/oss/](http://download.opensuse.org/distribution/10.3/repo/oss/)
[http://download.opensuse.org/distribution/10.3/repo/non-oss/](http://download.opensuse.org/distribution/10.3/repo/non-oss/)
[http://download.opensuse.org/update/10.3/](http://download.opensuse.org/update/10.3/)

[http://download.opensuse.org/distribution/10.3/repo/src-oss/suse/](http://download.opensuse.org/distribution/10.3/repo/src-oss/suse/)
[http://download.opensuse.org/distribution/10.3/repo/src-non-oss/suse/](http://download.opensuse.org/distribution/10.3/repo/src-non-oss/suse/)

[http://download.opensuse.org/distribution/10.3/repo/debug/](http://download.opensuse.org/distribution/10.3/repo/debug/)

[....]

---------------
Community
Webpin Package Search
[http://packages.opensuse-community.org/](http://packages.opensuse-community.org/)

-------------------
For MP3 playback, all one needs to do is to install the 
gst-fluendo-mp3 package from non-oss repo found on DVD or Online!

[http://download.opensuse.org/distribution/11.0/repo/non-oss/suse/x86_64/](http://download.opensuse.org/distribution/11.0/repo/non-oss/suse/x86_64/)
gst-fluendo-mp3-2-72.1.x86_64.rpm  

[http://download.opensuse.org/distribution/11.0/repo/non-oss/suse/i586/](http://download.opensuse.org/distribution/11.0/repo/non-oss/suse/i586/)
gst-fluendo-mp3-2-72.1.i586.rpm 

Some other packages from this repo (DVD or Online):
RealPlayer-10.0.9-51.1.i586.rpm 
acroread-8.1.2-34.1.i586.rpm 
antivir-2.1.10.15-41.1.i586.rpm
flash-player-9.0.124.0-10.1.i586.rpm  
opera-9.27-15.1.i586.rpm 
java-1_5_0-sun-1.5.0_update15-12.1.i586.rpm  
java-1_6_0-sun-1.6.0.u6-8.1.i586.rpm  
[...]

NB: I got nice video playback by installing everything that seemed appropriate from the [VLC repo.]("http://download.videolan.org/pub/videolan/vlc/SuSE/") Packman repo is good but it carries a lot of packages and the repo is constantly refreshed and thus can be a PITA if one has limited bandwidth or low broadband allowance.

Cheers

---

### Post by Growbag on 2008-08-08
Wow!

I just spent the last 2 days setting my machine up OFFLINE!

Yeas, you read that correctly, I did a fresh install from the openSUSE 11 DVD.

Crazy maybe, but I have my reasons.

Well, I managed to get multimedia working perfectly.

The dependencies were an absolute nightmare, but now I have a folder containing ALL the extra stuff (that I use), and a script to install it.

Minus my themes and other non-essential apps (like Skype, Sweethome3d,  and GoogleEarth), it weighs in at 77.6 megs, and that includes the latest Nvidia driver!

It also copies the firmware for a Broadcom 4312 wireless card, and enables it.

All I need is the standard openSUSE 11 DVD, no network connection required, the rest is automatic.

Just don't ask for a copy, as that would be naughty! ;)

---

### Post by mikjp on 2008-08-08
mp3's play out of the box here, too. Fresh install using openSUSE 11.0 DVD (boxed edition).

Greetings,

mikko

---

