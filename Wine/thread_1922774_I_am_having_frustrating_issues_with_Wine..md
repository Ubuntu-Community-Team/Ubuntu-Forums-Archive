---
title: "I am having frustrating issues with Wine."
date: 2012-02-09
forum: Wine
---

### Post by MrBandicootKid on 2012-02-09
Wine. A program we use to make Windows apps run on Linux operating systems.
 
Well, I downloaded the latest Wine version and I have some frustrating problems:
 
Sound.
I had no sound at all. When  I configured the sound, and test the sound, I just get this soft "wump-wump-wump" sound. Now I only get partial sound, not all of it, like it'll only play some sound files.
 
Speed.
The speed of the emulator is extremely slow. I can't sem to find any way to make it faster, but not too fast, just at normal speed.
 
I downloaded all the packages I could find to make these work, but I had no luck at all. Any help is much appreciated.

---

### Post by ron999 on 2012-02-09
> **MrBandicootKid said:**
> ... I downloaded the latest Wine version and I have some frustrating problems:
 
...I downloaded all the packages I could find to make these work, but I had no luck at all. Any help is much appreciated.

Hi
Use wine from the official ppa.
Enter these 3 commands:-
```
sudo add-apt-repository ppa:ubuntu-wine/ppa
```

```
sudo apt-get update
```

```
sudo apt-get install wine1.3 winetricks
```

---

### Post by oldos2er on 2012-02-09
Thread moved to Wine.

---

### Post by MrBandicootKid on 2012-02-09
> **ron999 said:**
> Hi
Use wine from the official ppa.
Enter these 3 commands:-
```
sudo add-apt-repository ppa:ubuntu-wine/ppa
```

```
sudo apt-get update
```

```
sudo apt-get install wine1.3 winetricks
```

It failed to install.

---

### Post by Tweak42 on 2012-02-09
Wine is not a end all solution to running windows apps, some apps work great, many not at all, others maybe partially working. Wine is constantly in a state of development, thus the more popular apps are more likely to get attention to be made functional sooner than lesser known. 

This sticky post at the top of the wine forum is a good starting point guide:[URL="http://ubuntuforums.org/showthread.php?t=885111"]
** Before asking for help with Wine << PLEASE READ BEFORE POSTING **[/URL]
Please pay special attention to the part **"Things to include when asking for help:"** as it helps get faster more accurate replies.  Additionally use search function on this forum for your app in question to reduce asking redundant questions and find already posted answers.


> **MrBandicootKid said:**
> Wine. A program we use to make Windows apps run on Linux operating systems.
 
Well, I downloaded the latest Wine version and I have some frustrating problems:
 
Sound.
I had no sound at all. When  I configured the sound, and test the sound, I just get this soft "wump-wump-wump" sound. Now I only get partial sound, not all of it, like it'll only play some sound files.
 
Speed.
The speed of the emulator is extremely slow. I can't sem to find any way to make it faster, but not too fast, just at normal speed.
 
I downloaded all the packages I could find to make these work, but I had no luck at all. Any help is much appreciated.

---

### Post by forrestcupp on 2012-02-10
> **MrBandicootKid said:**
> 
Speed.
The speed of the emulator is extremely slow. I can't sem to find any way to make it faster, but not too fast, just at normal speed.

You can't really expect a computer trying to work like Windows from within Linux to run Windows software at full speed. Some apps run closer to normal speed than others, but you can't expect that to be the norm.

Also, some apps require tweaks to get them to run better. The ones you're having problems with, you'll just have to google how to run that app with Wine. Some apps won't work at all. It's taken them a lot of work to try to recreate a Windows environment from scratch.

---

