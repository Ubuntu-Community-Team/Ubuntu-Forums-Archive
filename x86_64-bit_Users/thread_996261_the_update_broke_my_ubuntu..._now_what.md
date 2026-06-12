---
title: "the update broke my ubuntu... now what?"
date: 2008-11-28
forum: x86 64-bit Users
---

### Post by LoneWolfJack on 2008-11-28
Since the last update my system is barely usable. It feels like the CPU is maxed out so that everything is sloppy and laggy. Yet the system monitor says there is no process that takes more than 1% of the CPU. The GNOME panels constantly get distorted, too, so I guess there was an update for that thing.

What do I do now? Reinstall?

---

### Post by steveneddy on 2008-11-28
What version of Ubuntu are you using?

---

### Post by LoneWolfJack on 2008-11-28
Gutsy... I guess if I will have to reinstall I can as well go with Ibex but actually, I don't have time right now to reinstall everything so it would be great if there was a way to fix my system or roll back the last updates.

---

### Post by John Jason Jordan on 2008-11-28
> **LoneWolfJack said:**
> Since the last update my system is barely usable. It feels like the CPU is maxed out so that everything is sloppy and laggy. Yet the system monitor says there is no process that takes more than 1% of the CPU. The GNOME panels constantly get distorted, too, so I guess there was an update for that thing.
What do I do now? Reinstall?

Dude, I feel your pain about reinstalling. Everyone always says "just reinstall," but evidently they do not actually use their computer for anything. I have dozens of major programs installed, and each has a gazillion tweaks and sometimes things I had to do to get them working. And I certainly do not have a log of all the things I did along the way - the log would be reams of pages. Reinstalling is not trivial.

Regarding your problem, I am not a guru, so I can't offer a simple solution. But it sounds as though your display is messed up somehow. I do know that Intrepid makes a major change to the way X is configured. In the past (through Hardy) the video, mouse and keyboard were all defined in the /etc/X11/xorg.conf file. Now the mouse and keyboard have been moved out of the xorg.conf file and the upgrade to Intrepid remarked out ("#") all the lines relating to the mouse and keyboard. Even the video is handled elsewhere for most users. I upgraded my desktop and discovered that it worked fine even after I completely deleted the xorg.conf file.

I can also add that the proprietary drivers for a lot of video cards have been changed. I have heard of people having problems with some of them.

If I was you I would start by running "lspci" from the command line to find out the exact name of the video chip in your computer. Then I would search the forums for recent posts on that video device.

---

### Post by twiz86 on 2008-11-29
I had a prob with my gfx card that was making my computer appear as if it were lagging. I have a nvidia card and it was overheating. That is one thing you could check cuz i thought my problem had to do with the kernel updates i got today but it was just a cooling problem.

things arent always as they appear

---

### Post by ragingpenguin on 2008-11-29
You should try and get some information that will confirm what you are thinking about cpu maxing out etc.

start by opening a terminal, and type

```

top

```

this will launch a program that will show you all the processes running on your machine, and give you an idea if it is CPU contention, or Memory, or something else.

P will sort processes by cpu
M will sort it by memory

There is also gnome-system-monitor that is accessible from the System>Administration menu that will give you a graphical insight into what is eating up all your resources.

---

### Post by LoneWolfJack on 2008-11-29
Thanks for trying to help, but the CPU is definitely idling. I suppose gnome or x got messed up with the last update that required a reboot of the machine. I've been using Gtusy for over a year now with the exact same hardware and it always worked almost perfectly.

Turning off compiz helped a bit, at least windows don't need two seconds to build up now, but its still way too slow.

Unless someone else has a brilliant idea, I guess it's reinstall time. *sigh*

---

### Post by briandu on 2008-11-29
Seems like your graphics card has gone astry - u say it is a nvidia right?

What driver are you using? You should be using ver 177 of the driver.

Install the later version I suggest - I found it stabilised the graphics.

---

### Post by ///MVinny on 2008-11-29
> **briandu said:**
> Seems like your graphics card has gone astry - u say it is a nvidia right? 
Install the later version I suggest - I found it stabilised the graphics. 

That is very true ... if you were using the proprietary driver before, every/any upgrade breaks the driver - even upgrades to the kernel.  The symptoms you mention seem very familiar.  Go get the proprietary driver:

[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us) 

There's instructions on the same download page.  Kill any x running sessions and from the console/directory of the download: ```
sudo sh NV* 
```

---

### Post by LoneWolfJack on 2008-11-29
Thanks, you pointed me in the right direction... I reactivated the restricted driver and my desktop is much more responsive again (even though it's still showing the restricted driver as disabled... huh?).

Also, I'm just now getting the latest driver from ATI.

Maybe I won't need to upgrade... which isn't too bad because Ibex is giving me headaches... showing plenty of error messages on the live cd, mouse not working right, etc.

But then again... I now almost want to upgrade. ;)

---

