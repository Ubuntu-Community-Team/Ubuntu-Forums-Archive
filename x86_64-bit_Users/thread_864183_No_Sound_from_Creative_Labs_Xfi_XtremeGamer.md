---
title: "No Sound from Creative Labs Xfi XtremeGamer"
date: 2008-07-19
forum: x86 64-bit Users
---

### Post by airjrdn on 2008-07-19
I just got Ubuntu 8.04.1 64bit installed.  No sound other than pc beep though.

asoundconf list produces nothing

lspci shows a bunch of stuff, including:
02:09.0 Multimedia audio controller: Creative Labs SB X-Fi

Reading the 124 pages of posts from [here]("http://ubuntuforums.org/showthread.php?goto=newpost&t=571656") is a little much.

Any thoughts on how to get sound working?

---

### Post by Svenstaro on 2008-07-20
I got mine to work using this: [http://ubuntuforums.org/showpost.php?p=4823915&postcount=675](http://ubuntuforums.org/showpost.php?p=4823915&postcount=675)

But if you look for a simple and quick solution, use this: [http://ubuntuforums.org/showpost.php?p=4874981&postcount=2](http://ubuntuforums.org/showpost.php?p=4874981&postcount=2)

Enjoy.

---

### Post by airjrdn on 2008-07-20
That just seems like a lot of work to get a popular, name brand sound card working.

Not to mention the fact that it states it's going to break the Nvidia driver setup I've got working right now.

I just got Ubuntu installed a couple of days ago, and finally got VirtualBox working so I could do my Windows stuff in XP in there.  The last thing I want to do it muck up what I just got to work. :(

---

### Post by Svenstaro on 2008-07-20
Don't worry, you'll need to recompile the kernel so before you do anything you'll just download the NVIDIA driver manually from their site (its a setup which does everything automatically, don't worry)

Of course, if you want a really easy, just works way (that might occasionally break), give my second link a try.

Also, the reason the drivers take so long is that Creative only recently opened their documentation (so that nobody could see their crappy design since all the pro-claimed X-fi only features are really just software gimmicks).

---

### Post by airjrdn on 2008-07-21
Well, sound is working, but I can't get the Nvidia drivers working again.  I have no visual effects.  I've done enough things that honestly, I have no idea what state it's in.

At some points, it would boot into low graphics mode or something like that.  At others, it would boot to a black screen, and Ctrl-Alt-Backspace would do nothing.

I've downloaded the latest Nvidia drivers, and attempted the instructions the Creative Drivers page links to, but they only link to 7.04 and older, not 8.04.

I'm running the 64bit version of Ubuntu.  I have the newer kernel w/ALSA stuff going and sounds, but how do I get the latest Nvidia drivers installed?

---

### Post by airjrdn on 2008-07-21
Got it!

Used instructions from [here]("http://ubuntuforums.org/showpost.php?p=5086971&postcount=6").

---

### Post by Svenstaro on 2008-07-21
Uh, wait. Which way did you even choose? The compile-kernel one or the install-deb one?

Anyway, for now just backup your current xorg.conf
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.brokenbkup
and get a new xorg.conf
sudo dpkg-reconfigure xorg-server
Configure it as well as you can and then just install the NVIDIA drivers manually 
sudo ./NVIDIA*.sh
Make sure to let it configure xorg.conf for use with its drivers.

BUT! Make sure that all Ubuntu-official drivers for your NVIDIA are REMOVED! This is where I got fooled.


EDIT: Oh, I see too slow :P
Well, enjoy your Ubuntu installation then :)

---

### Post by airjrdn on 2008-07-22
I used the compiled one.  I figured it was the "right" way to do it.

Sound isn't consistent though.  For instance, the machine was shut down last night because we had some pretty major storms, and when I booted up this morning, it doesn't work.  The speaker near the clock has the circle w/the line through it.  I've seen it do that and be ok after different reboots.  Any idea on how to make it consistently work?

---

### Post by airjrdn on 2008-07-23
I'm still having an issue w/sound not working.  I walked through the uninstall, and the install, and each time, when I do a "make", I get "Error 2".

I've done some searching, but haven't figured out how to get passed this one.

---

