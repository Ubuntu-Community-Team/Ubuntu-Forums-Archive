---
title: "Package confusion - liblircclient0"
date: 2007-02-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by John Jason Jordan on 2007-02-25
A couple of months ago I upgraded my Dapper amd64 computer to Edgy amd64. Afterwards there were a bunch of things to fix, and I just discovered another one -- obsolete packages.

Originally there were 52 "local or obsolete" packages listed in Synaptic. I have slowly upgraded all of them two or three per day just to make sure everything still works after upgrading; that is, except for one remaining package: liblircclient0.

For all the others there was always a newer package listed in Synaptic, so I just removed the old one and installed the new one. But for liblircclient0 there is no new one listed in the All section of Synaptic. Since there is no new one and Synaptic thinks it is obsolete I decided to uninstall it. But doing so would also remove 

mencoder
mozilla-mplayer
mplayer
mplayer-fonts
rhythmbox
totem-mozilla
totem-xine
vlc
vlc-nox
vlc-penguin-alsa
vlc-penguin-arts
vlc-penguin-esd
wxvlc

So evidently this file is needed for just about anything that deals with multimedia. 

When I select it in Synaptic, then Properties > Versions it says

liblircclient0 0.8.0-9ubuntu1~dapper (now)
liblircclient0 0.8.0-5ubuntu1 (edgy)

The first one is what is currently installed. I would just uninstall it and install the second one except for some niggling thoughts. First, why didn't the upgrade to Edgy also upgrade this file? Second, the second of the two is not listed in Synaptic; in order to install it I have to do Package > Force version. Third, I have my dumb moments, but doesn't 9 come after 5? Like, why is 0.8.0-5 a later version than 0.8.0-9? Or is it? And fourth, evidently this file has something to do with infrared devices. I think the laptop that Edgy is installed on does have an infrared port, but I don't own any peripherals to connect to it. And what do those other multimedia programs have to do with infrared?

I suspect if I force the new package I'll muck something up and, since the one currently installed is no longer in the repositories, I won't be able to go back. Therefore, I thought I'd ask before shooting myself in the foot.

---

### Post by Stemp on 2007-02-25
What gives you :
```
sudo aptitude update
sudo aptitude dist-upgrade 

```
?

---

### Post by John Jason Jordan on 2007-02-25
> **Stemp said:**
> What gives you :
```
sudo aptitude update
sudo aptitude dist-upgrade 
```
I did sudo aptitude update and it checked all the sources list. I didn't see anything relating to the liblircclient0 package (or any others, for that matter).

As for aptitude dist-upgrade, this is what it says in man aptitude:

 dist-upgrade
              Upgrades installed packages to their most recent version, remov&#8208;
              ing  or  installing  packages as necessary. This command is less
              conservative than upgrade and thus more likely  to  perform  un&#8208;
              wanted  actions. Users are advised to either use upgrade instead
              or to carefully inspect the list of packages to be installed and
              removed.

So thanks for the suggestion, but no way am I doing that before I know what it will do. Meantime, I will stick to Synaptic where I can get more information before committing to something. Actually, Update Manager says the computer is up to date, so I suspect that aptitude dist-upgrade will do nothing. But I prefer to know what it will do before I push the button. :)

---

