---
title: "World of tanks on ubuntu 12.04"
date: 2012-11-18
forum: Wine
---

### Post by jfouclait on 2012-11-18
Hey!

I am running ubuntu 12.04 dual-booted with win 7 just because of this game.  I know that there are a lot of guides around explaining how to get WoT running under linux, however I just cannot get it to work.
I have followed a few but failed miserably again and again. 
What I'm asking is if there is a kind soul around here that would be ready to write down step by step instructions on how to get WoT running under ubuntu. I must admit that there are a lot of really good guides around, but even thought I am fairly fluent in ubuntu I still get stuck following those guides. Let's just say that compiling wine is just too much if I do not have step by step instructions. 

So If there is anyone willing to write down a noob-proof guide on how to get WoT running from scratch under ubuntu I belive that many would be grateful!!!!

Thank you!!!

---

### Post by jfouclait on 2012-11-21
bumping out of sheer hope.:P

---

### Post by mentorious on 2012-11-22
I tried with WotFlix and it worked really good. Look for this at winehq and russians WoT forum.

sorry, I posted from phone ;d

---

### Post by jfouclait on 2012-11-25
Hey!
thx for reply!

I tried the Wotflix option but the game produced an error and couuld not start. That was over a year ago.

With the new WoT 8.1 update it is all different. Some instructions say, that u do not need to run Wotflix  if WoT version over 8.0. All instructions are outdated.. My biggest problem is that even if I try following those instructions they all say I need to get the game full client. But as of the 8.1 update there is only the installer, WoT does not give me the option to download the full client and I cannot find it on any torrent sites..

So I'm stuck...

any ideas?

---

### Post by jfouclait on 2012-11-30
bumping again for more hits while hoping for a solution... at least I'm honest;)

---

### Post by mentorious on 2012-11-30
I installed using the newest wine and everything works [(tutorial)]("http://ubuntu.pl/forum/viewtopic.php?f=206&t=163415").. but doesn't play at well with 10/20 fps : /

---

### Post by jfouclait on 2012-12-03
Hey! THX for the reply, this solution did it for me! I  installed the game and it plays, however I do have a sync problem, but I can probably blame wargaming for that not linux!!

THX again for the solution!

---

### Post by d325gu on 2012-12-15
> **jfouclait said:**
> Hey! THX for the reply, this solution did it for me! I  installed the game and it plays, however I do have a sync problem, but I can probably blame wargaming for that not linux!!

THX again for the solution!


Confirmed, much of this worked for me. installed the most recent Dx9_36, msxml3, corefonts, the win2k networking patch (cant remember the name) and already had the download for the full game w/all updates. once all the patches/overrides were installed via winetricks installed WoT via the GUI and after a short wait, it fired up. Disconnected once in the garage, hasn't since. Adjusted the graphics and am only getting about 10 less than I did on winblows. (40-45 windows)

---

### Post by superdaveozzborn on 2012-12-15
Hay! this is great, thank you. always wanted to try this game...

---

### Post by Robbz on 2013-02-28
> **jfouclait said:**
> Hey!

I am running ubuntu 12.04 dual-booted with win 7 just because of this game.  I know that there are a lot of guides around explaining how to get WoT running under linux, however I just cannot get it to work.
I have followed a few but failed miserably again and again. 
What I'm asking is if there is a kind soul around here that would be ready to write down step by step instructions on how to get WoT running under ubuntu. I must admit that there are a lot of really good guides around, but even thought I am fairly fluent in ubuntu I still get stuck following those guides. Let's just say that compiling wine is just too much if I do not have step by step instructions. 

So If there is anyone willing to write down a noob-proof guide on how to get WoT running from scratch under ubuntu I belive that many would be grateful!!!!

Thank you!!!

Hello I have your complete Noob proof solution to this problem!   [http://forum.worldoftanks.com/index.php?/topic/210785-worldoftanks-for-linux-and-mac-users/](http://forum.worldoftanks.com/index.php?/topic/210785-worldoftanks-for-linux-and-mac-users/)

Enjoy!

---

### Post by mikemurray2 on 2013-09-02
First you need the most up-to-date PlayOnLinu, version 4.2.1, not the version pre-installed in the Ubuntu Software Centre in 12.04. The one that is already there has out of date mono and gecko packages and WoT needs the most recent PoL to work.

So, remove the original PoL from the USC.

Go to the playonlinux site and download the latest version. This will also have the latest version of Wine in it.

[http://www.playonlinux.com/script_files/PlayOnLinux/4.2.1/PlayOnLinux_4.2.1.deb](http://www.playonlinux.com/script_files/PlayOnLinux/4.2.1/PlayOnLinux_4.2.1.deb)

Install it.

Run PlayOnLinux, choose 'Install' and 'WorldOfTanks' from the games list and follow the instructions carefully.

If you get errors about mono or gecko or get a message that PlayOnLInux is too old, then you haven't installed the up-to-date version properly.

---

