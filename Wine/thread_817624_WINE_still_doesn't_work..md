---
title: "WINE still doesn't work."
date: 2008-06-03
forum: Wine
---

### Post by Pap3r on 2008-06-03
I posted a question regarding CSS a while back on two forums--  Overclock.net and these wonderful forums.  My problem consists of my WINE install not being able to run CSS, or any other game, *** effectively as Ubuntu 7.1

The day I opened the package manager and saw that I could upgrade to 8.04 I jumped at the opportunity.  CSS ran wonderfully under WINE in 7.1, 70+FPS on an overclocked 7600GT!!  I figured it would be a huge boost to performance.  When I finished upgrading, I tested my games to check if they worked, you know, just in case.  I opened up Steam, launched CSS, and found that it froze at the Sending Client Info, or whatever, screen.  The mouse started to move lazily, with much lag.  I ended up needing to restart my computer, because it froze everything.  I eventually resorted to uninstalling wine, and reinstalling it, just in case that mught be the problem.  Same results.

This was months ago.

That kept up for a while, and on my quest for redemption I ran into a program by the name of Wine-doors.  I read up on it, and I was PUMPED, to say the least.  I would finally get to play my games!  I laid the blame on the 1.0rc version of WINE, and found that Wine-doors had the ability to run certain programs under certain versions of WINE.  9.59 worked well with Steam, so I chose that.  To my disbelief, nothing changed.  I again, had to restart my computer, because  it all froze up.  I again, uninstalled/reinstalled wine 2-3 times and then wine-doors again, just to be sure.  Same results.

This too, was months ago.

I would think about it every once in a while.  I was pretty content with not playing games anymore, after all, it had been about a month since CSS worked, so I didn't really care that much.  Just recently though, I stumbled upon Playonlinux.  I knew better than to get my hopes up by now, but I gave it a try anyway.  I installed it, installed Steam through it, installed Wine 9.59 through it, and gave it a try.  CSS booted, started loading.... froze.   DMANIT!

I'm dumbfounded as to how an update to Ubuntu could have killed my gaming, but I think I should attribute it to WINE.  How can I fix this?:confused:

Thanks.

EDIT

I'd like to also point out, that I run Compiz Fusion.  In 7.10, when I used the benchmark plugin I got 999fps.  In 8.04, using the benchmark command, I get 30-40FPS, and if I switch the WM from compiz --replace, to the automated one through compiz, I get 230+fps.

---

### Post by cogadh on 2008-06-03
I would suggest that you downgrade back to 7.10 for now. In my own experience, 8.04 is to Ubuntu what Vista is to Windows. I never could get the Nvidia drivers working properly at all and the PulseAudio sound system is really not ready for general usage yet. I rolled back to Kubuntu 7.10 and everything, including Wine and Steam-enabled applications, works perfectly now (well, nearly perfectly).

---

### Post by Pap3r on 2008-06-03
I just don't want to do a full reinstall....

Any way not to?

---

### Post by cogadh on 2008-06-03
AFAIK there is no real way to downgrade, other than a complete reinstall. I have my system set up with a separate partition for my home directories for just such circumstances. The OS has a 20GB drive mounted at / and the home directories have a 100GB drive mounted at /home. Any time I need to reinstall (or upgrade), I just tell the partitioner where to mount everything, but to only format the 20GB drive. The system gets installed cleanly and I don't lose any of my setting or personal stuff. If you have the option to set something like that up, I highly recommend it, it can save you a load of trouble in the long run.

---

### Post by Pap3r on 2008-06-03
So, supposing I were to copy my entire Home directory to a disk, I would be able to keep my information.. as in, dependencies are not held from home to /usr files or anything?  I am only tentative about that because I hate messy installs, or messy folders in general.  It's clean or a clean install in my book.

---

### Post by mac143_01 on 2008-06-04
How to install wine? 

Maybe the time will come that wine will work perfectly for 8.04 and maybe games will run smoothly...

---

### Post by Brynster on 2008-06-04
I strangly have had no bother with wine and 8.04.

I simply set the winecfg menu to use alsa and my video resolution to the same as my desktop resolution. I get 100+ fps with full details settings. Where as in 7.10 i experienced no end bother getting the nvidia driver to work and at best got 60-70 fps.....


PC's are weird.

---

