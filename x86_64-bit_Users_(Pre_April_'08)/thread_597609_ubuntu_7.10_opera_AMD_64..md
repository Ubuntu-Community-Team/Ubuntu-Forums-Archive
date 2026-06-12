---
title: "ubuntu 7.10 opera AMD 64."
date: 2007-10-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by emulation_fan on 2007-10-30
I am in need of opera, but i can not find a version for 64 bit.
Could some one tell me how to get opera on my machine, or do i have to go back to using the ubuntu i386 distro?

---

### Post by sethvath on 2007-10-30
[ftp://ftp.opera.com/pub/opera/linux/950b/final/en/x86_64/](ftp://ftp.opera.com/pub/opera/linux/950b/final/en/x86_64/)

---

### Post by FredB on 2007-10-31
> **emulation_fan said:**
> I am in need of opera, but i can not find a version for 64 bit.
Could some one tell me how to get opera on my machine, or do i have to go back to using the ubuntu i386 distro?

Only starting for 9.5 final, there will be a 64bits version.

But you can still download the beta version, very crashy as far as I see.

---

### Post by johnny_b_good on 2008-03-21
thanx, it works! even if the fonts and the theme are ugly...

---

### Post by TimelessRogue on 2008-03-21
The Opera download site is now showing version 9.5 as final.  Downloading as we speak and will report back with any "problems" on my particular set-up ...

---

### Post by fbg111 on 2008-03-30
Anyone know the Opera unstable repository for Synaptic?

---

### Post by Cris(c) on 2008-03-31
Got and installed Opera 9.50 beta installed on my computer (AMD64). After 2 min of using it, it started crashing like every 1 min, specially when I tried with multimedia pages (youtube for instance)...so, I had to go back to Firefox...

Has someone had the same problem as I did? Any tips how to solve it?

---

### Post by Cris(c) on 2008-03-31
I suggest you try with this version (beta) of Opera:

[http://snapshot.opera.com/unix/snaps.../x86_64-linux/](http://snapshot.opera.com/unix/snaps.../x86_64-linux/)

It's much more stable than the one posted by sethvath (of course, when he posted this new beta release wasn't there)...

Enjoy!

---

### Post by fbg111 on 2008-03-31
I just installed the most recent 9.5 beta on 7.10 x64, and it works perfectly.  Had to dl it and manually install it, there's no x64 version in the non-free repositories yet.  Started this thread on the Opera *nix forum, some helpful links there:

[http://my.opera.com/community/forums/topic.dml?id=227823](http://my.opera.com/community/forums/topic.dml?id=227823)

---

### Post by Cris(c) on 2008-03-31
Yup...the beta 9.5b works prefectly fine on amd64 plataform, though you'll not find it in the repositories. But to install it you simply need to click on the downloaded package...

---

### Post by kung fu buntu on 2008-04-05
> **Cris(c) said:**
> I suggest you try with this version (beta) of Opera:

[http://snapshot.opera.com/unix/snaps.../x86_64-linux/](http://snapshot.opera.com/unix/snaps.../x86_64-linux/)

It's much more stable than the one posted by sethvath (of course, when he posted this new beta release wasn't there)...

Enjoy!Your URL is messed up both it helped me google for the opera deb here:
[http://snapshot.opera.com/unix/snapshot-1875/x86_64-linux/](http://snapshot.opera.com/unix/snapshot-1875/x86_64-linux/)

This may be of interest to you all:
Flash Player 9 working on Edgy Amd64 with nspluginwrapper
[http://ubuntuforums.org/showthread.php?t=341727](http://ubuntuforums.org/showthread.php?t=341727)

Now, if only I could get flash to work with this... I already have firefox_amd64 working fine with flash.
I started a thread about Opera + Flash + AMD64 at [http://ubuntuforums.org/showthread.php?p=4657887](http://ubuntuforums.org/showthread.php?p=4657887) with the intent of helping me solve this problem.

---

### Post by Trevorius on 2008-04-09
When I first installed it, it would crash fairly frequently (2-3 times per hour). It didn't seem to be as much related to flash as it was to the number of tabs I had open. After open it in the terminal, I got the error message "ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored." multiples times in a row, and before it crashed, it said "Segmentation fault (core dumped)" I reinstalled using the link 'kung fu buntu' posted, and it opened with the same error message but hasn't crashed yet (been going for over an hour including multile utube vids). We'll see how well it holds up.

---

### Post by Cris(c) on 2008-04-11
If you try with the 'final' version (beta 9.50) it is likely that Opera crashes a lot. What I did and so far has worked prefectly, it is to install a snapshop version of Opera, which you can find here: [http://my.opera.com/desktopteam/blog/](http://my.opera.com/desktopteam/blog/) Just click on the link UNIX (right hand side) and then on X86_64-linux to get the latest snapshop (which is very likely to change from week to week..this, I guess, is the reason why the previous address I posted was messed up...sorry about that!)

Although most of the pages work perfectly, there still a few that may pose some problems. It seems that Opera in Linux AMD64 does not like much anything that has to do with Flash. However, I DO HAVE Flash working. If you've installed Firefox then it is very likely you already have Flash instaled on your system. To make it work with Opera it seems the only thing you have to do is to redirect the path in Opera Pug-ins to wherever you installed Flash (/usr/lib/mozilla/plugins or /usr/lib/flashplugin-nonfree are 2 very likely options)...go to Preferences --> Content --> Plug-in Options and change the path there....at least for me, this's worked ok so far...

Hope it helps.

---

### Post by kung fu buntu on 2008-04-18
That is not the best solution!

The ideal is to mkdir /usr/lib/opera/plugins and to link libflashplayer.so (IIRC) there and any other plugins (like mplayer) you seem fit.
Otherwise Opera will load other plugins that it shouldn't like the flash wrapper used by Firefox.

Check here if you're curious
[http://my.opera.com/community/forums/topic.dml?id=228511&t=1207950769&page=1](http://my.opera.com/community/forums/topic.dml?id=228511&t=1207950769&page=1)

---

### Post by Cris(c) on 2008-04-21
Hey kung fu buntu...I was looking  at the thread you posted. Perhaps you're right: what you suggest (to link plugins from /usr/lib/opera/plugins) is better. However, I just provided you with a way to make flash work with AMD86 + Opera. So far I've had no problems with any site asking for flash (in particular youtube works perfectly). Just out of curiosity, what do you mean by your suggestion being better?

---

