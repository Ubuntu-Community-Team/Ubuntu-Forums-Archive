---
title: "Wine and Steam on Chromebook. Need serious help..."
date: 2018-07-06
forum: Wine
---

### Post by katineko on 2018-07-06
[COLOR=#1C1C1C][FONT=&amp]I have a Samsung Chromebook Pro with an Intel m3 processor that I am trying to install Wine, Steam and play some games from Steam on. I've been at this for several days now, and have tried numerous methods. Today, I have been following the instructions in these videos: [https://www.youtube.com/watch?v=3XaPQcgOtss](https://www.youtube.com/watch?v=3XaPQcgOtss) .
 Problem is that when I run the WINEPREFIX command in the terminal (mentioned in the video), and the path to SteamSetup.exe to install it, Wine says that SteamSetup.exe cannot be found. I've looked at PlayOnLinux, tried Winetricks etc. to no avail. Winetricks said that I needed to make a clean 32 bit prefix which I have also done lots of research on how to do. But, I can't find any straight forward help or answers.
[/FONT][/COLOR]
[COLOR=#1C1C1C][FONT=&amp]By the way, I am running Ubuntu 14.0.4 and I think I installed Wine 1.7. The Steam games I want to run aren't that demanding (mostly visual novels like Clannad etc.).
[/FONT][/COLOR]
[COLOR=#1C1C1C][FONT=&amp]Anyway, if someone would be able to walk me through this in a simple way if possible I will greatly appreciate it : )[/FONT][/COLOR]

---

### Post by TheFu on 2018-07-07
Welcome to the forums.

I have a few chromebooks, but stopped using WINE around 2015 and never used steam-anything.

There isn't any simple way to do what you want.  If there was, it would be automated already.  Is your chromebook running stock Ubuntu at boot or are you using a chroot like crouton?

Might not matter, but don't steam games validate the amount of storage is available? Have you verified there is sufficient room?
If you can run and post the output from **inxi -Fx** and **df -h**, those would be helpful.

Somethings to consider for the future: Be aware that support for 14.04 ends in less than a year, so you will need to move to a newer LTS. Some flavors of 14.04 already had support end over 2 yrs ago. Might find it harder to locate desktop help people running 14.04.  People on desktops have moved to 16.04 a few years ago and some have or will move to 18.04 in the next month or so.  Basically, only servers run 14.04 anymore.

If you want the best help here, post the exact commands being run.  Copy/paste, don't type, so any mistakes are easily checked.

---

