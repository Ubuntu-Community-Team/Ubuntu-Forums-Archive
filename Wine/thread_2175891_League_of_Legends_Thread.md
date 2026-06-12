---
title: "League of Legends Thread"
date: 2013-09-21
forum: Wine
---

### Post by patrick19 on 2013-09-21
I've been messing with different methods of running LoL, and so far the best method for me has been through PlayOnLinux. It does run, and plays fine for the most part (see issues at bottom). I understand that there are post similar to this on winehq but I would like to organize my process of making the game run smoothly on Ubuntu, while allowing others to give their input when trying the same method. 

Make sure the basics are done first:

-Video adaptor is supported and running proprietary drivers (open source drivers were a significant decrease in performance for me, yours may vary)
    -Install by using software and sources and going to the right-most tab and selecting a proprietary driver and committing
-Have wine installed (I'll throw in winetricks for flexibility if you need:
```
sudo apt-get install wine winetricks
```

The rest should be handled by the following:

Here is the original howto that I followed: [http://linuxforcynics.com/how-to/how-to-install-and-play-league-of-legends-on-ubuntu](http://linuxforcynics.com/how-to/how-to-install-and-play-league-of-legends-on-ubuntu)

Please remember to follow the directions precisely, and have the latest build of PlayOnLinux 4.2.1 as described in the link. There is a direct .deb download. Make sure to check when finished upgrading with:

```

playonlinux --version

```

Here's my hardware: 

HP Sleekbook w/
```

AMD A6 4455M
GPU/APU Radeon 7500G w/ 512MB DDR667 shared

Ubuntu 13.04
3.8.0-30-generic x86_64
FGLRX from fglrx-updates repository

```


**Optional** Next we can try editing some of the registry in favor for gaming. Open PlayOnLinux, right click League of Legends and select Registry Editor. Also do your winecfg settings with this method.
I've tried some registry editing and added the typical Direct3D key and added strings for settings following this guide: [http://www.overclock.net/t/213952/how-to-advanced-wine-configuration-for-gaming](http://www.overclock.net/t/213952/how-to-advanced-wine-configuration-for-gaming)

Current strings in my Direct3D key:
```
DirectDrawRenderer opengl
VideoMemorySize 512

```

LoL will launch perfectly and I can usually play matches, but I noticed the following:

**Issues**
- When matched and launched into game, the load screen shows nobody connected for possibly 40 seconds to 2 minutes before responding and loading
- Minimap texture glitches/flickering
- About -50% performance decrease from inside Windows 8
- Rejoining a quitted match fails at the loading screen. It just shows everyone as disconnected and doesn't respond
- Random errors at launch from PlayOnLinux that causes it to forceclose. (I'll report the exact error when I can)

I'll continue to update this thread as I find anny success, or failures. It takes time as I must wait for any game that I left to be completed before I can start a new one to test. Please post your experiences!

**Current Notes and Changelog **

-Graphics may be flickering and artifacting more often after adding registry edits. Will try again without them.
```
 Removed GLSL Enabled string from Direct3D key. Waiting results.
```

---

### Post by Jeshu4ever on 2013-09-22
> **patrick19 said:**
> I've been messing with different methods of running LoL, and so far the best method for me has been through PlayOnLinux. It does run, and plays fine for the most part (see issues at bottom). I understand that there are post similar to this on winehq but I would like to organize my process of making the game run smoothly on Ubuntu, while allowing others to give their input when trying the same method. 

Make sure the basics are done first:

-Video adaptor is supported and running proprietary drivers (open source drivers were a significant decrease in performance for me, yours may vary)
    -Install by using software and sources and going to the right-most tab and selecting a proprietary driver and committing
-Have wine installed (I'll throw in winetricks for flexibility if you need:
```
sudo apt-get install wine winetricks
```

The rest should be handled by the following:

Here is the original howto that I followed: [http://linuxforcynics.com/how-to/how-to-install-and-play-league-of-legends-on-ubuntu](http://linuxforcynics.com/how-to/how-to-install-and-play-league-of-legends-on-ubuntu)

Please remember to follow the directions precisely, and have the latest build of PlayOnLinux 4.2.1 as described in the link. There is a direct .deb download. Make sure to check when finished upgrading with:

```

playonlinux --version

```

Here's my hardware: 

HP Sleekbook w/
```

AMD A6 4455M
GPU/APU Radeon 7500G w/ 512MB DDR667 shared

Ubuntu 13.04
3.8.0-30-generic x86_64
FGLRX from fglrx-updates repository

```


**Optional** Next we can try editing some of the registry in favor for gaming. Open PlayOnLinux, right click League of Legends and select Registry Editor. Also do your winecfg settings with this method.
I've tried some registry editing and added the typical Direct3D key and added strings for settings following this guide: [http://hackerbot.net/mmo/league-of-legends-lol](http://hackerbot.net/mmo/league-of-legends-lol)

Current strings in my Direct3D key:
```
DirectDrawRenderer opengl
VideoMemorySize 512

```

LoL will launch perfectly and I can usually play matches, but I noticed the following:

**Issues**
- When matched and launched into game, the load screen shows nobody connected for possibly 40 seconds to 2 minutes before responding and loading
- Minimap texture glitches/flickering
- About -50% performance decrease from inside Windows 8
- Rejoining a quitted match fails at the loading screen. It just shows everyone as disconnected and doesn't respond
- Random errors at launch from PlayOnLinux that causes it to forceclose. (I'll report the exact error when I can)

I'll continue to update this thread as I find anny success, or failures. It takes time as I must wait for any game that I left to be completed before I can start a new one to test. Please post your experiences!

**Current Notes and Changelog **

-Graphics may be flickering and artifacting more often after adding registry edits. Will try again without them.
```
 Removed GLSL Enabled string from Direct3D key. Waiting results.
```

Thanks soooo much...
...Ive been looking for this literally for days...

You are my hero / champion <3

:D

---

