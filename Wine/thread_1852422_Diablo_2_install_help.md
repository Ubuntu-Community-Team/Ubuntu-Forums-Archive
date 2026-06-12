---
title: "Diablo 2 install help"
date: 2011-09-30
forum: Wine
---

### Post by inhumanrampager on 2011-09-30
I'm a linux noob, and this is my first post here so bare with me....I'll try to give you as much information as possible. Anywho I'm trying to install Diablo 2 (I have the battle chest, so I have LoD as well) and I can't install it. I'm running Ubuntu 11.04, and I'm using Playonlinux version 4.0.12, which is using Wine version 1.3.2. My actual wine version is 1.2.2....how that works out, I dunno. Like I said. I'm green about this linux stuffs. :P Aanyways, I'm getting a specific error when trying to load the end user license agreement (literally the first thing it tries to load). The license agreement doesn't load, I can't click "agree" and "disagree" appears clickable, but it isn't. And immediately following the crappy load, I get the following error.
```
Wine Program Crash
Internal errors - invalid parameters received
```
Can I get some help?

---

### Post by bakelitedoorbell on 2011-10-01
Hello, I'm no expert either, but I am running Diablo2 in Wine (not playonlinux).

Your error message sounds like a permissions issue.  Is there a way you can run it with sudo or gksudo?

Correction: this is a bad idea, don't use sudo.

---

### Post by inhumanrampager on 2011-10-08
If there is, then I am completely unsure how to do so.

---

### Post by inhumanrampager on 2011-10-15
Update:

I downgraded to Ubuntu 10.04, found out my issue on PlayOnLinux (which was I lacked the Gecko installer). However, I cannot play the game after install.....I can load the videos that open the game, but after that, my screen becomes a jumbled mess...no menus where there should be....no nothing. :P I'm not sure where to look to fix the settings, since it comes up fullscreen, and I figure the fullscreen is what's killing it (since I had similar issues with the Unreal series).

---

### Post by Soulcage on 2011-10-15
Never run wine with sudo. [http://wiki.winehq.org/FAQ#head-96bebfa287b4288974de0df23351f278b0d41014]("http://wiki.winehq.org/FAQ#head-96bebfa287b4288974de0df23351f278b0d41014")

---

### Post by avix on 2011-12-12
still no delete of message. I got it working now the video is having issues (this is not the only app that it does that with)

---

### Post by Dlambert on 2011-12-13
> **avix said:**
> still no delete of message. I got it working now the video is having issues (this is not the only app that it does that with)

Could use PlayOnLinux, but are your graphics drivers installed?

---

### Post by avix on 2011-12-13
I've been playing with trying to install the latest drivers from Nvidia. (my card is supported) but when ever I try to shut down X and GDM to install the new driver it just hangs. I'm going to give PlayonLinux a try. it starts. get the Blizzard and the sound and then the "input out of range" and it hangs.

---

### Post by Dlambert on 2011-12-13
> **avix said:**
> I've been playing with trying to install the latest drivers from Nvidia. (my card is supported) but when ever I try to shut down X and GDM to install the new driver it just hangs. I'm going to give PlayonLinux a try. it starts. get the Blizzard and the sound and then the "input out of range" and it hangs.

You could use Jockey (additional drivers in Ubuntu) and install an (outdated but stable) version of the Nvidia driver.

Also, i had trouble like this too!, First I had to disable Noveau, then boot into recovery mode via grub then install the drivers. *Ubuntu recommends the version in the Ubuntu repositories for guaranteed support*

---

### Post by Dlambert on 2011-12-13
> **Dlambert said:**
> You could use Jockey (additional drivers in Ubuntu) and install an (outdated but stable) version of the Nvidia driver.

Also, i had trouble like this too!, First I had to disable Noveau, then boot into recovery mode via grub then install the drivers. *Ubuntu recommends the version in the Ubuntu repositories for guaranteed support*

Also I had a problem that while installing the driver it would load X, preventing the driver from installing, so I had to switch to run-level 3 (I believe) to prevent that.

---

### Post by avix on 2011-12-14
I hadn't thought about changing the rub level. been trying to install it through Playonlinux and I must be doing something wrong there. starting to think it might just be easer to build a machine and put XP on it.

---

### Post by garyhibdon on 2011-12-23
ive never had use or need to use playonlinux, ive always run d2 on wine.

remove playonlinux, go to a terminal and type 

```
sudo apt-get install wine
```

that will download wine and put everything where it belongs.

as far as getting diablo installed, the EASIEST way is to dl it onto a windows machine and just copy the entire d2 folder to a flash drive and manually put it into the wine folders.

if this doesnt help, then im sorry.

---

### Post by avix on 2011-12-27
as it turned out it was a video problem. the MB was starting to die. got a new board in transit with much more power and video.  still, thanks for all the help guys, I sure did learn a lot.

---

### Post by avix on 2011-12-30
got the new board (from dual core to 6 core!!!) and all kinds of nice shiny and it came right up in wine. with a little fiddling with wine audio got sound too!

it did see to run a bit slow when others on the screen. going to play with wine video settings a bit later.

---

