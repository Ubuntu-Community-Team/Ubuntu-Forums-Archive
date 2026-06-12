---
title: "league of legends with play on linux"
date: 2014-02-01
forum: Wine
---

### Post by mushroom08 on 2014-02-01
i have play on linux but when i try to install LoL i get to the progress bar but the window grays out becoming non-responsive anyone know how to fix this?

---

### Post by PotatoHead007 on 2014-02-01
Hey mushroom08 :)

I run League on Linux, Ubuntu 12.04.3 x32.
Here is how(quite easy, just follow the prompts).

Update PlayOnLinux(do this in a terminal[copy-paste]):

wget -q "http://deb.playonlinux.com/public.gpg" -O - | sudo apt-key add -
sudo wget [http://deb.playonlinux.com/playonlinux_maverick.list](http://deb.playonlinux.com/playonlinux_maverick.list) -O /etc/apt/sources.list.d/playonlinux.list
sudo apt-get update
sudo apt-get install playonlinux

Then, go to "Install a program", wait for PlayOnLinux to update its database quick, then where it says "Include, tick "Testing".
Ckick on games, and look for League of Legends. Click install, and follow prompts. If you did everything right, and there was no error, you should be able to install League
When all the files have been downloaded, you can easily go into your Account. But to play a game you need to run this:

force_s3tc_enable=true playonlinux

That command will enable you to play(at least i needed it), because otherwise your loading screen(before starting a game) will stay black. As it is, it will stay black for a while, and then only will it show the other players and loading etc.
That's it :) Hope it helped, and if you have problems, pelase ask :D

NB: I have experienced a few bugs, some major, some small. Here they are:
Some items(e.g Rabadons deathcap) are only red squares in the store. Should be able to fix that with a patch. 
FPS lag spikes while in combat. I have 1GB VRAM and a quad i5, and still i get hectic lag spikes while in combat. Might be able to fix using a different windows manager.
Game freezes. The worst of them all. Sometimes my game just freezes, can't do anything but force shutdown by pressing power-button. I suggest you don't play ranked if this happens.

---

### Post by howefield on 2014-02-01
Thread moved to the *"Wine"* forum.

---

