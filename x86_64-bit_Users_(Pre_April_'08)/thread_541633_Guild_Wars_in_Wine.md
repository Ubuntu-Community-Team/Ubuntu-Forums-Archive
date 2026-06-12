---
title: "Guild Wars in Wine"
date: 2007-09-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by DPic on 2007-09-03
I just installed Ubuntu 7.04 (64-bit) for a friend of mine and installed Wine through [http://wiki.winehq.org/UbuntuAMD64](http://wiki.winehq.org/UbuntuAMD64) and then Guild Wars through [http://wiki.guildwars.com/wiki/Linux#Get_Guild_Wars](http://wiki.guildwars.com/wiki/Linux#Get_Guild_Wars) 

Everything seemed to work okay-- i started up Guild Wars and it downloaded the files like normal but then the screen went black and the cursor changed (as if the game was starting) but then nothing happened. The computer was still responsive when i hit num lock to see if it was frozen but there was nothing else i could do and i had to do a forced shutdown to get out of it.

---

### Post by johannes on 2007-09-03
May not be a very helpful answer, but I haven't found 32-bit wine to be very stable at all on 64-bit platforms. It crashes quite often.

If you are going to use wine a lot I think you would be better off on a 32-bit platform. Is there any particular reason your friend needs a 64-bit OS?

---

### Post by Kilz on 2007-09-03
> **johannes said:**
> May not be a very helpful answer, but I haven't found 32-bit wine to be very stable at all on 64-bit platforms. It crashes quite often.

If you are going to use wine a lot I think you would be better off on a 32-bit platform. Is there any particular reason your friend needs a 64-bit OS?

A search of wine will bring up loads of posts. 80% will be in the i386 sections of the forums. Perhaps it isnt the bit of the os that is to blame. But that Wine is still Beta software. That it is trying to let you run applications that are not native. That what runs on wine is nice, and to be happy with that.

---

### Post by DPic on 2007-09-03
Well i installed the 64-bit OS because that's the processor he has. I already spent hours setting everything up for him so i don't think we're going to change the OS but he still has an extra HDD that we were planning on using as a backup but i suppose i could partition off a small part of the drive to use to install Ubuntu 32-bit, yes?

---

### Post by johannes on 2007-09-03
Just because he has a 64-bit processor you don't have to install a 64-bit OS. I can't guarantee Guild Wars will work better on 32-bit Ubuntu (i have never tried) but I think it might be worth trying if you have the time and hard disk space.

---

### Post by ExcessNeo on 2007-09-03
> **DPic said:**
> I just installed Ubuntu 7.04 (64-bit) for a friend of mine and installed Wine through [http://wiki.winehq.org/UbuntuAMD64](http://wiki.winehq.org/UbuntuAMD64) and then Guild Wars through [http://wiki.guildwars.com/wiki/Linux#Get_Guild_Wars](http://wiki.guildwars.com/wiki/Linux#Get_Guild_Wars) 

Everything seemed to work okay-- i started up Guild Wars and it downloaded the files like normal but then the screen went black and the cursor changed (as if the game was starting) but then nothing happened. The computer was still responsive when i hit num lock to see if it was frozen but there was nothing else i could do and i had to do a forced shutdown to get out of it.

Try using the proper Feisty AMD64 Wine?

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

4 terminal lines, much easier install imo.
> 
wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list](http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/winehq.list
sudo apt-get update
sudo apt-get install wine


---

### Post by DPic on 2007-09-03
Yeah, that's what i did. Sorry, i posted the wrong link in the initial post. Anyways, we got it working by configuring Guild Wars to open in a window instead of fullscreen because for some reason nobody can get it to work on fullscreen. And even like this the game crashed mid-game.

---

### Post by afonic on 2007-09-04
Hi,

first of all are you sure your video card drivers are OK? What card do you have and what version of the drivers?

Next, make sure i32-libs are installed (i32-libs-sdl as well). There is no problem with the 64bit Feisty, it does run fine.

Now about wine, there is some command option you need to add to make it run, something with sound in it but I have forgotten right now! I will get back to you.

Finally, I STRONGLY suggest using Cedega for Guild Wars. In Wine you can't even get the sound working. I use it for about a year now and I can play GW just fine. :)

---

### Post by fornax01 on 2007-09-05
if using wine i find it best to run it with the following options:

-dx8 -noshaders -windowed -dsound

-dx8 - will run the game using DirectX 8.1 renderer
-noshaders - will disable shaders (boosts performance and removes some graphics bugs)
-windowed - will run game in window - full screen doesn't work too well yet
-dsound - will force game to use older sound engine, this will make game run with some sounds
-nosound - if you are still experiencing problems with sound use this option to disable sounds and allow game to play

---

