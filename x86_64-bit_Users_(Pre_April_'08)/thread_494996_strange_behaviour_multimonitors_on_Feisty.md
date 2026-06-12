---
title: "strange behaviour multimonitors on Feisty"
date: 2007-07-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by funkwurm on 2007-07-07
I have an AMD Sempron 64bits and 2 nVidia graphics cards and I recently installed Ubuntu Feisty Fawn. I have 3 20" monitors with 1680x1050 resolution, and a simple 15" 1024x768. Now I've heard that different resolutions amongst your multimonitor setup isn't going to work on linux, so leaving that 15" aside I trust the nVidia Linux drivers to be able to cope with 3 monitors that have the same resolution.

To describe a long journey quick. I now can't open the terminal any more, scripts like Kilz'  Nspluginwrapper script won't do anything. A lot of windows (screensaver-settings for example) won't open any more, the window is half drawn and disappears again.

How do I bring my terminal and everything that depends on it back to life?

Besides the above issue that I would really like solved, here are a couple of problems that I think are unsolvable at the current state of Linux in general. Luckily I'm prepared to live with it for now.

2 Monitors on the same graphics card can only be twin-viewed, Xinerama won't work. This is a disadvantage because if I maximize a window, it is maximized over both displays. This ofcourse is hardly desirable.

A third monitor on a second graphics card can only be enabled with Xinerama, no twin-view. This doesn't really have any disadvantages, its just that people talk about is as if you have choice. This has proven not to be the case, the both have their own purpose.

Without touching the mouse nor the keyboard, Ubuntu made my primary display black. I move my mouse over it and see the mouse, only all controls are gone. I click where I think the workspace switchers resides and this still works. I click the upper-right corner, the desktop fades to dark and I try to guess where the restart-button is. I think I accidentally clicked the hibernate button guessing by the load-letter that came when booting Ubuntu again. This time non of my monitors work and 1 gives a "input not supported" warning. A hard reset did the trick.

As stated above, I'll take it for granted, I was just wondering how many of you believe that an OS with this kind of behaviour is "human" and ready for the masses... Because I believe we have a very long way to go, as this happened without any other packages than the default installed.

---

