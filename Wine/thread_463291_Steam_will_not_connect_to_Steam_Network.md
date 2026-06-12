---
title: "Steam will not connect to Steam Network"
date: 2007-06-03
forum: Wine
---

### Post by crazy25000 on 2007-06-03
Hello, 

I got the Steam installation working perfectly. When I log in, here is what it says:

"Could not connect to Steam Network. This could be due to a problem with your internet connection, or with the Steam network. Please visit [www.steampowered.com](www.steampowered.com) for more info"

I visited the website and it said it could be a problem with the schools network...etc but when I run it in Windows XP it runs and works perfectly fine. I tried this at home and at school, says same exact thing. When I run it in Windows, it works fine at home and at school.

I'm dual booting Windows XP Home and Ubuntu/Xubuntu 7.04 Feisty.

Anyone know how to fix this? Would be much appreciated.

---

### Post by Ferrat on 2007-06-03
are you using wine version 0.9.38? many have had problems with this

---

### Post by crazy25000 on 2007-06-03
> **Ferrat said:**
> are you using wine version 0.9.38? many have had problems with this

Yeah im using that version. So if I use the older version, it should work fine?

---

### Post by crazy25000 on 2007-06-03
THANKS FOR THE INFO!!!!!

w00000 it finally worked :) 

Im downloading Counter Strike Source right now!

---

### Post by ea_hatch on 2007-06-03
how would i revert back to 0.9.37 if i have 0.9.38??    ubuntu noob here;)

---

### Post by YokoZar on 2007-06-04
> **ea_hatch said:**
> how would i revert back to 0.9.37 if i have 0.9.38??    ubuntu noob here;)
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

---

### Post by ea_hatch on 2007-06-04
cool thanx..got it working now but how do it get it to stop telling me about the updates available for wine now?

---

### Post by abowman on 2007-06-07
> **ea_hatch said:**
> how would i revert back to 0.9.37 if i have 0.9.38??    ubuntu noob here;)

```
cd /var/cache/apt/archives
sudo dpkg -i wine_0.9.37~winehq0~ubuntu~6.10-1_i386.deb
```

---

### Post by kthxbai2u on 2007-12-16
Still says that message for me... And i downgraded to 9.37 or w.e you said up there O_o I want play CS and i got further somehow before... I cant even get a decent xp install because the images i get are screwed somehow. and then I find I have a bad drive O_o wine is my last resort to being able to play my cs :S

---

### Post by ubu-for on 2008-08-03
> **crazy25000 said:**
> "Could not connect to Steam Network. This could be due to a problem with your internet connection, or with the Steam network. Please visit [www.steampowered.com](www.steampowered.com) for more info"

I have the same problem with Feisty and Wine 1.0 since some days!

Now I will try some older Wine versions, but I would appreciate any further ideas to solve the problem, because Wine 0.9.59 and 0.9.44 don't work, too!

---

### Post by gotthardt on 2008-08-03
Came back after a 5 day trip and ran steam/HL2 for 20 mins last night then installed some updates then in the morning I got the first post's problem. Internet with any other game/app works fine.

One of these updates broke steam:

Upgraded the following packages:

deskbar-applet (2.22.2.1-0ubuntu1) to 2.22.3-0ubuntu1

eog (2.22.2-0ubuntu1) to 2.22.3-0ubuntu2

firefox (3.0.1+build1+nobinonly-0ubuntu0.8.04.2) to 

3.0.1+build1+nobinonly-0ubuntu0.8.04.3

firefox-3.0 (3.0.1+build1+nobinonly-0ubuntu0.8.04.2) to 

3.0.1+build1+nobinonly-0ubuntu0.8.04.3

firefox-3.0-gnome-support (3.0.1+build1+nobinonly-0ubuntu0.8.04.2) to 

3.0.1+build1+nobinonly-0ubuntu0.8.04.3

firefox-gnome-support (3.0.1+build1+nobinonly-0ubuntu0.8.04.2) to 

3.0.1+build1+nobinonly-0ubuntu0.8.04.3

gcalctool (5.22.2-0ubuntu1) to 5.22.3-0ubuntu0.1

gdm (2.20.6-0ubuntu2) to 2.20.7-0ubuntu1.1

gnome-about (1:2.22.2-0ubuntu3) to 1:2.22.3-0ubuntu1

gnome-cards-data (1:2.22.2.1-0ubuntu1) to 1:2.22.3-0ubuntu2

gnome-desktop-data (1:2.22.2-0ubuntu3) to 1:2.22.3-0ubuntu1

gnome-games (1:2.22.2.1-0ubuntu1) to 1:2.22.3-0ubuntu2

gnome-games-data (1:2.22.2.1-0ubuntu1) to 1:2.22.3-0ubuntu2

gnome-panel (1:2.22.2-0ubuntu1) to 1:2.22.2-0ubuntu1.1

gnome-panel-data (1:2.22.2-0ubuntu1) to 1:2.22.2-0ubuntu1.1

gnome-system-monitor (2.22.1-0ubuntu2) to 2.22.3-0ubuntu2

gtk2-engines (1:2.14.1-0ubuntu1) to 1:2.14.3-0ubuntu2

gtkhtml3.14 (3.18.2-0ubuntu1) to 3.18.3-0ubuntu2

gvfs (0.2.5-0ubuntu1) to 0.2.5-0ubuntu2

gvfs-backends (0.2.5-0ubuntu1) to 0.2.5-0ubuntu2

gvfs-fuse (0.2.5-0ubuntu1) to 0.2.5-0ubuntu2

hal (0.5.11~rc2-1ubuntu8.1) to 0.5.11~rc2-1ubuntu8.2

iproute (20071016-2ubuntu1) to 20071016-2ubuntu2

kdebase-bin (4:3.5.9-0ubuntu7.2) to 4:3.5.9-0ubuntu7.3

kdebase-bin-kde3 (4:3.5.9-0ubuntu7.2) to 4:3.5.9-0ubuntu7.3

kdebase-kio-plugins (4:3.5.9-0ubuntu7.2) to 4:3.5.9-0ubuntu7.3

kdesktop (4:3.5.9-0ubuntu7.2) to 4:3.5.9-0ubuntu7.3

libavcodec1d (3:0.cvs20070307-5ubuntu7) to 3:0.cvs20070307-5ubuntu7.1

libavformat1d (3:0.cvs20070307-5ubuntu7) to 3:0.cvs20070307-5ubuntu7.1

libavutil1d (3:0.cvs20070307-5ubuntu7) to 3:0.cvs20070307-5ubuntu7.1

libglib2.0-0 (2.16.3-1ubuntu3) to 2.16.4-0ubuntu2

libglibmm-2.4-1c2a (2.16.0-1) to 2.16.4-0ubuntu1

libgnome-desktop-2 (1:2.22.2-0ubuntu3) to 1:2.22.3-0ubuntu1

libgtkhtml3.14-19 (3.18.2-0ubuntu1) to 3.18.3-0ubuntu2

libgtksourceview2.0-0 (2.2.1-1) to 2.2.2-0ubuntu1

libgtksourceview2.0-common (2.2.1-1) to 2.2.2-0ubuntu1

libgvfscommon0 (0.2.5-0ubuntu1) to 0.2.5-0ubuntu2

libgweather-common (2.22.1.1-0ubuntu2) to 2.22.3-0ubuntu2

libgweather1 (2.22.1.1-0ubuntu2) to 2.22.3-0ubuntu2

libhal-storage1 (0.5.11~rc2-1ubuntu8.1) to 0.5.11~rc2-1ubuntu8.2

libhal1 (0.5.11~rc2-1ubuntu8.1) to 0.5.11~rc2-1ubuntu8.2

libkonq4 (4:3.5.9-0ubuntu7.2) to 4:3.5.9-0ubuntu7.3

libldap-2.4-2 (2.4.9-0ubuntu0.8.04) to 2.4.9-0ubuntu0.8.04.1

libpanel-applet2-0 (1:2.22.2-0ubuntu1) to 1:2.22.2-0ubuntu1.1

libpoppler-glib2 (0.6.4-1ubuntu3) to 0.6.4-1ubuntu3.1

libpoppler2 (0.6.4-1ubuntu3) to 0.6.4-1ubuntu3.1

libpostproc1d (3:0.cvs20070307-5ubuntu7) to 3:0.cvs20070307-5ubuntu7.1

libsmbios1 (0.13.10-1ubuntu1) to 0.13.10-1ubuntu1.1

libwnck-common (2.22.1-0ubuntu1) to 2.22.3-0ubuntu1

libwnck22 (2.22.1-0ubuntu1) to 2.22.3-0ubuntu1

libxslt1.1 (1.1.22-1ubuntu1) to 1.1.22-1ubuntu1.2

poppler-utils (0.6.4-1ubuntu3) to 0.6.4-1ubuntu3.1

procps (1:3.2.7-5ubuntu2) to 1:3.2.7-5ubuntu3

python-gobject (2.14.1-2ubuntu2) to 2.14.2-0ubuntu1

python2.5 (2.5.2-2ubuntu4) to 2.5.2-2ubuntu4.1

python2.5-minimal (2.5.2-2ubuntu4) to 2.5.2-2ubuntu4.1

ufw (0.16.2.2) to 0.16.2.3

xsltproc (1.1.22-1ubuntu1) to 1.1.22-1ubuntu1.2

xulrunner-1.9 (1.9.0.1+build1+nobinonly-0ubuntu0.8.04.2) to 

1.9.0.1+build1+nobinonly-0ubuntu0.8.04.3

xulrunner-1.9-gnome-support (1.9.0.1+build1+nobinonly-0ubuntu0.8.04.2) to 

1.9.0.1+build1+nobinonly-0ubuntu0.8.04.3

Find the mole!

---

### Post by desertboy on 2008-08-03
Broke for me too happened after those updates

---

### Post by ubu-for on 2008-08-03
Maybe Ubuntu blocks some important outgoing ports since these updates?

Till now I couldn't find a working Wine version.

---

### Post by gotthardt on 2008-08-03
Found the fix

Delete ClientRegistery.blob in the wine/drive_c/program files/steam directory.

have a nice day

---

### Post by desertboy on 2008-08-03
That fixed it, was going to buy quake wars but it's a lot cheaper on ebay and at least I know it will definitely work.

---

### Post by ubu-for on 2008-08-04
> **gotthardt said:**
> Delete ClientRegistery.blob in the wine/drive_c/program files/steam directory.

Thanks gotthardt!

For the following Steam update, I had to downgrade to Wine 0.9.44.

---

### Post by straxus on 2008-08-13
I'm having this problem, but deleting ClientRegistry.blob doesn't fix it. Also, it only happens over my wireless connection. (Even though Steam updates just fine) It works fine when wired.

This just started a few days ago.

---

### Post by straxus on 2008-08-14
Found my problem.  It's my terrible router.  For some reason putting my PC in the DMZ really screws things up. You would think it would help connection problems.  I turned the DMZ off and Steam worked fine.

This is the second time the DMZ on my D-Link DI-604 has confused something on my network. (I had forgotten about the prior incident until now) Steer clear of these things.

---

### Post by Lab on 2008-08-22
Wow, thanks so much straxus ... that was exactly my problem :guitar::guitar:

---

### Post by hell_prince on 2008-08-26
Sorry Guys for being the noob I am but steam won't connect to the server... What should I do? I read his post but well.. I'm new to ubuntu still... Any help?

---

### Post by desertboy on 2008-08-26
> **hell_prince said:**
> Sorry Guys for being the noob I am but steam won't connect to the server... What should I do? I read his post but well.. I'm new to ubuntu still... Any help?

For me I had to from terminal

cd /home/stuart/wine/drive_c/program files/steam
rm ClientRegistery.blob


replace stuart with whatever your home is called.

---

### Post by hell_prince on 2008-08-26
Problem Solved... Dunno how though... It just did... I have a NVidia GeForce 8500Gt and Can't run in DirectX 9.0 graphics though... Runing in 7... But uhm is it normal do decrease very badly the performance when with 9.0?

---

### Post by moesan on 2011-05-03
For people who did not get steam working even after removing the blob file, try uninstalling steam, then installing Play On Linux, and installing steam from there.
Worked for me, don't know why, because Play On Linux is sort of a wine gui... But it did.

---

### Post by bapoumba on 2011-05-05
This is quite an old thread.

---

