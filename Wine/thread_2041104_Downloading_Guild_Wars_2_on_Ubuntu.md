---
title: "Downloading Guild Wars 2 on Ubuntu"
date: 2012-08-11
forum: Wine
---

### Post by Nanur on 2012-08-11
Kind of a quick question: Is downloading Guild Wars 2 on Ubuntu pretty much the same process as downloading Guild Wars 1 on Ubuntu? 

I am just about to pre-order the game, and wanted to know what to do when I buy it.

Thanks.
 -Nanur

---

### Post by mvidberg on 2012-08-24
You can download the GW2 installer exe file from your account page at guildwars2.com (if you've registered an account by entering your key code which you should have by now if you've pre-ordered).  You can also download it from [http://backupshere.com/storage/gw2/Gw2Setup.exe](http://backupshere.com/storage/gw2/Gw2Setup.exe)

I've tried installing it via "wine Gw2Setup.exe" and have been able to press the "install game" button which installs for a long time then just crashes.  So as far as I can tell, it can't be installed at the moment but I haven't researched it.

I setup a Windows7 partition to boot and play from just because of this game... but I would like to get it working in Linux if possible.

---

### Post by mvidberg on 2012-08-24
So I did manage to get the installer to complete by restarting it about 20 times (ugh!).  Each time it downloaded a bit more before crashing.  Now to wait until launch to see if it actually works.

---

### Post by Nanur on 2012-08-25
I haven't yet pre-ordered it yet. So tell me how it goes when the game is launched.
Also, I believe as I am typing this message the game is up for those who pre-ordered.
:) 
have fun man!

---

### Post by oly on 2012-08-25
I am playing fine and its working pretty well for me, but i did have to add -dx9single to the start parameters to make it work correctly.

Also any linux guilds around ?

---

### Post by johnjust on 2012-08-28
The download crashed every 10,000 files or so, but it eventually did finish (and can be copied to other computers in case you have a laptop or other desktop, so you don't have to download it all again).

The game itself runs beautifully - I'm getting 35+ FPS on average with a Thinkpad T420s.

My desktop is another story, but the hardware is about 4 years old - the game still runs, but at about 10-15 FPS.  It's playable but busy areas are sketchy.

---

### Post by brian70809 on 2012-08-29
I got it working with playonlinux.. However, the trading post does not work..

There is a patch for it, but I can't find it!  lol

Anyone got the trading post Gem Store or Currency Exchange to show up.. it's an HTML based system apparently.

---

### Post by johnjust on 2012-08-29
That's not an Ubuntu/Linux/Wine problem, it's an issue with the game itself - I've seen people posting in the general chat about it every 5 minutes or so...

---

### Post by Nanur on 2012-08-30
Great! Thanks everyone!

---

### Post by johnjust on 2012-09-05
Just thought I'd update you on the trading post.

They launched it on Tuesday, but it still wasn't working for me (as well as other Windows users).  After I looked around and found some solutions involving building a custom Wine engine specifically for the game (which I don't possess the skill to do), I stumbled on the PlayOnLinux configuration for GW2, and there's a drop-down box where you can choose what Wine to use to launch GW2.

By default, it was set to Wine "1.5.9".  However, you can install new versions of wine right through PlayOnLinux, and one of the newer ones is called "1.5.12_GuildWars2".  Using this one makes the trading post work just about perfect, but I did see a slight decrease in performance (when panning the camera around in a busy area).

Be careful with the trading post though, my buttons were grayed out and I didn't think it was responding.  Come to find out I bought way more of an item than I needed, and I wound up spending all my gold...

---

