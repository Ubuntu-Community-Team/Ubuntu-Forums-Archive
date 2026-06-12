---
title: "White screen in Gnome"
date: 2007-06-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by capecove on 2007-06-12
Well everyone, I have really done it this time.

In the true spirit of someone who can't leave well enough alone, I tried loading Envy last night (which usually SOLVES peoples problems I am told). Now mind you, I didn't start with any serious problems, just a little flicker in a 3D game I installed through Synaptic. But, of course, the first step to troubleshoot something like that is to install the newest drivers, right? ;)

Okay, so here is the deal. I installed Envy (my video card is an NVIDIA 7600 GS with 256 meg of RAM), chose NVIDIA, rebooted and got a corrupt XSERVER message (ugly blue and red screen with gray typeface). So, I did panic just a little bit but calmly restarted into the recovery console and ran:

dpkg-reconfigure xserver-xorg 

(which I found on these forums prior to having trouble and which I wrote down just in case)

Went through the screens, choosing mainly default options. Restarted, got into Gnome with no trouble at all. EXCEPT, its maximum resolution was set to 1024x768. So, I decided to uninstall Envy at that point. Did so, restarted, same XSERVER error.

Went through the dpkg-reconfigure thing again, rebooted, got Nautilus with no trouble, even at 1280x1024 resolution (or so it seems), then after it tries to load Gnome I get a black screen with gray panels top and bottom (like it looks unresponsive) which shows for approx 2 seconds, replaced by a purely white screen with my mouse cursor on it.

Okay,I can take it, how bad did I break it? :)

And, as an aside, do any of you 3/4 digit bean folks ever (or did you ever) break your Ubuntu and simply reinstall (is that giving up too easily?)

Thanks all!

---

### Post by capecove on 2007-06-12
Not a good sign that there are no suggestions yet. I suppose I will simply reinstall and learn to not do that again! :)

---

### Post by david_2001 on 2007-06-12
> **capecove said:**
> 

Okay,I can take it, how bad did I break it? :)

And, as an aside, do any of you 3/4 digit bean folks ever (or did you ever) break your Ubuntu and simply reinstall (is that giving up too easily?)

Thanks all!

You probably didn't break it that badly but unless you know the intricacies of setting up X then it's probably easier to reinstall and start again.  Posting your /etc/X11/xorg.conf would have helped diagnosis.

As Linux doesn't take that long to install, I actually taught myself how to administer the system by installing, fiddling with stuff until it broke, installing again, fiddling with more stuff until it broke, installing again, and so on until I stopped breaking it.  (Try doing that with Windows XP or Vista!)

A general principle to observe is to avoid installing the latest drivers for anything unless you are absolutely certain that you really, really need the latest drivers.  More to the point, only install the latest NVidia drivers from the NVidia website, which is what I believe Envy does, if you don't mind that your X installation will stop working each time the Ubuntu linux-image kernel package gets updated.  A simple "sudo apt-get install nvidia-glx" or "sudo apt-get install nvidia-glx-new" and a little editing of xorg.conf will install a NVidia driver that is perfectly usable in most cases, or just use the restricted drivers manager.

---

### Post by capecove on 2007-06-12
Excellent advice I am sure. Thanks for chiming in. Back when I was FIRST learning to use computers, a CP/M floppy was pretty easy to recreate as was a MS-DOS boot floppy. :)

Now a days, since I am learning all over again, I have discovered that Ubuntu is about the easiest thing to do a reinstall on. The first time through went well, even for a newbie like I am. Now, I have more experience and will know what to install or not to install (or at least have some more information about that). Plus, geez, is there any better feeling, knowing that you aren't REQUIRED to use Windows anymore? Wow, I'd reinstall Linux monthly if I had to. LOL...

(Knock on wood, I assure you) ;)

---

