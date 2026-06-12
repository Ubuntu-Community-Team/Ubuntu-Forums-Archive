---
title: "Gnome not loading properly"
date: 2005-11-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by audaz on 2005-11-09
I put breezy on an old G3 and I have had some problems with Gnome. I get the login screen just fine, but when I try to log in, all i get is the login sound. I don't get the ubuntu splash screen or anything else. Just a brown background and a mouse cursor.

In fairness, I had this problem when I first installed, but i got to a terminal and did a sudo apt-get update and sudo apt-get dist-upgrade and it worked for a while. But I am now unable to get into Gnome.

Any suggestions?

---

### Post by youngdaniel on 2005-11-09
so many people are having this problem, yet there are so few people giving solutions! if only installing ubuntu was easier than this, everyone would be using linux! so many people get put off by a problematic install!!

I have installed 5.10 on a powerbook G3 perfectly, get to the login, and login fine, then get the welcome jingle and a nice little mouse cursor that even moves, and thats it!! I want the rest of it!!

Please help us!!!

---

### Post by youngdaniel on 2005-11-11
Is it me, or am I reading this same problem over and over again!!!

Surely theyre must be a post with the right solution!! Please help me!! It is making me so god dam mad!!! even angry!!!

Its like having a ferrari with no petrol!!! It is killing me!! 

I have a apple powerbook G3, 400mhz "Firewire" Model. 192mb of Ram, 8mb Video and DVD Drive.

Ubuntu 5.10 Installed perfectly fine. On first attempt to login it took the details fine and proceeded to a brown screen, with an active mouse and even played the jingle to annoy me even more!! 

I have read so many dam posts talking about changing stuff in Xorg.conf but whatever i have tried has failed to help!! 

Please guys anything you can do to help!!! Please!!!

Dan

---

### Post by lothar.swe on 2005-11-15
I'm positive it's the ATI 8 Mb graphics card causing this problem. It also occurs with my iMac G3/350 but not with my iMac G4/700 which has a nVidia 32 Mb graphics card. I was testing this out with the Ubuntu 5.10 PPC live-CD. Booting process runs fine, screen goes black, jingle is heard while the computer chews a lot on the CD disc. After a while it stops chewing. Apparently the Gnome desktop is working, because things happen (like CD starting to chew again) when I click the mouse randomly, and the short, bumpy sounds which accompagny mouse-click events are heard. Only problem is that the screen is completely black.

---

### Post by ssam on 2005-11-15
it could be this

[https://wiki.ubuntu.com/UbuntuDateBug](https://wiki.ubuntu.com/UbuntuDateBug)

i am trying my best to tell people

---

### Post by audaz on 2005-11-16
ssam is right! Thanks on behalf of the community!

It's working again. As a side note, the date on my computer was some time in 1956....wierd.

---

### Post by ssam on 2005-11-17
i think some macs have different zero dates, most that i have seen are 1904

---

### Post by jdp on 2005-11-17
ssam is mostly right.  For slot-loading iMacs the issue really is the xorg.conf with improper settings.  On my 350 SL w/ 256MB the 5.10 LiveCD booted to a black screen when trying to load Gnome, and the clock is fine.  I moved to VTTY1, did **sudo vi /etc/X11/xorg.conf** and changed the H.Refresh to **60-66** and V.Refresh to **75-117** then restarted GNOME from whence things worked fine.

---

