---
title: "Quake 3 - Tremulous Full Conversion Mod 64bit users **IMPORTANT**"
date: 2005-08-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by hammett111 on 2005-08-13
Hello Fellow 64bit Ubuntu and Kubuntu-ites I have a problem solver for you if you decide to install the tremulous mod for Quake3. :smile:  :smile: 

By now you would have realised that games that are not natively compiled for our unique and most funky 64bit environment, need something like the "Linux32" command to install them. The tremulous mod is just one of these many games. But never fear I have installed and am now running it.  :razz:  :razz: 

So  _Step 1 - _ download the mod from [http://tremulous.net/](http://tremulous.net/) and save it wherever you please, I saved it to my home directory where all my games are lurking.

_Step 2 - _ Use the linux32 command, something like "sudo linux32 ./tremulous-q3-1.0.0-installer.x86.run" to install the mod. NOW!!! this is important!! Your quake3 installation **MUST!!!** be in /usr/local/games/quake3 so that when the termulous mod is installed its path will be /usr/local/games/quake3/tremulous. Once this is done EXCELLENT!! Remember you can only install into this directory as ROOT!!

_Step 3 - _ Go to your tremulous directory and edit as root the script "tremulous.sh" THIS again is very important!!. The bugger will read something like this: [-X 

#! /bin/sh
quake3 $* +set com_hunkMegs 100 +set fs_game tremulous

THIS!! is not cool for us,sicne as you'll remember quake3 does **NOT** run for us using the quake3 binaries. Instead we use quake3-smp. So edit as so: [-X 

#! /bin/sh
quake3-smp $* +set com_hunkMegs 100 +set fs_game tremulous

NOW!! for the cool part, running it.

_Step 4 - _ Open up a terminal in the tremulous directory and type ./tremulous.sh and test if it works....which it will. Once it runs shut down and you can now go to your desktop where the tremulous mod shortcut will be installed under GAMES in your kicker.

HAVE FUN AND "AMD64-whore" will see you for some fragging action. \\:D/  \\:D/

---

