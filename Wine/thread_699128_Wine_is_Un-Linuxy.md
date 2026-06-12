---
title: "Wine is Un-Linuxy"
date: 2008-02-17
forum: Wine
---

### Post by &amp;)ky#)^ on 2008-02-17
This is not a thread about the evangelism related to whether emulating or backwards engineering a Windows compatibility layer in Linux is a worthwhile or positive endeavor.

I'm here to report that Wine breaks Linux permissions security protocol.  I attempted to use Wine to run realMyst and Worms Armageddon.  realMyst didn't work to my satisfaction and Worms barely ran at all.  That being said, I experienced two bugs.  The first is a well-documented problem regarding entries left in the gnome menu after applications are removed or Wine itself is removed.  The bug I'm here to report is that Wine altered my xorg.conf file significantly enough to cause me concern.  Luckily, my carefully engineered copy was backed up and I was back to normal in no time.  That said, Wine editing xorg.conf at all is cause for concern.  I was never foolish enough to run Wine as root, so how did it gain permissions to write to xorg.conf?  It added a bunch of modelines and removed most of my customization.  I was using Wine version 0.9.46, the one in the gutsy repos.

---

### Post by trippinnik on 2008-02-17
What makes you think it was wine that altered your xorg.conf?  Recent versions of Ubuntu already modify xorg.conf files.

---

### Post by PmDematagoda on 2008-02-17
This thread has been moved to the Wine section.

---

### Post by Ferrat on 2008-02-17
> **bluej774 said:**
> This is not a thread about the evangelism related to whether emulating or backwards engineering a Windows compatibility layer in Linux is a worthwhile or positive endeavor.

I'm here to report that Wine breaks Linux permissions security protocol.  I attempted to use Wine to run realMyst and Worms Armageddon.  realMyst didn't work to my satisfaction and Worms barely ran at all.  That being said, I experienced two bugs.  The first is a well-documented problem regarding entries left in the gnome menu after applications are removed or Wine itself is removed.  The bug I'm here to report is that Wine altered my xorg.conf file significantly enough to cause me concern.  Luckily, my carefully engineered copy was backed up and I was back to normal in no time.  That said, Wine editing xorg.conf at all is cause for concern.  I was never foolish enough to run Wine as root, so how did it gain permissions to write to xorg.conf?  It added a bunch of modelines and removed most of my customization.  I was using Wine version 0.9.46, the one in the gutsy repos.

AFAIK that isn't possible since you do need admin/system rights to edit xorg.conf, sounds more like something in your system went of the reservation but not wine, well there could be wine involvement perhaps, wine did something like switch resolution or or likewise and for some reason your system disliked that and did something. 
But wine changing xorg.conf by it's own, nope I don't think so, launching something in wine might crash x but not change anything in xorg.conf 

what exactly was changed in your xorg.conf?

---

### Post by FrozenFox on 2008-02-17
> **bluej774 said:**
> This is not a thread about the evangelism related to whether emulating or backwards engineering a Windows compatibility layer in Linux is a worthwhile or positive endeavor.

I'm here to report that Wine breaks Linux permissions security protocol.  I attempted to use Wine to run realMyst and Worms Armageddon.  realMyst didn't work to my satisfaction and Worms barely ran at all.  That being said, I experienced two bugs.  The first is a well-documented problem regarding entries left in the gnome menu after applications are removed or Wine itself is removed.  The bug I'm here to report is that Wine altered my xorg.conf file significantly enough to cause me concern.  Luckily, my carefully engineered copy was backed up and I was back to normal in no time.  That said, Wine editing xorg.conf at all is cause for concern.  I was never foolish enough to run Wine as root, so how did it gain permissions to write to xorg.conf?  It added a bunch of modelines and removed most of my customization.  I was using Wine version 0.9.46, the one in the gutsy repos.

I also agree with the others, I customize and edit my xorg.conf all the time but I've never noticed it edit xorg at all, even installing from synaptic (ie as sudo/root). It certainly never reverted any of my changes, and I don't see anything different from my backup before i installed anything to after i installed everything (incl. wine)..

Also, worms 4: mayhem works flawlessly for me, same speed as windows, in wine 0.9.55. The worms games aren't too vastly different afaict, so perhaps you should upgrade to the newest version.. that one is quite old.

---

### Post by &amp;)ky#)^ on 2008-02-18
I am convinced that it was Wine because that was the only program I was running at the time and the only one that was unusual.  When I played realMyst, the game did change my resolution and then it did crash before it changed it back.  However, even if the game did need to change the resolution, it should have been able to since the only way to do that is to mess with X and it didn't have the user rights to do so.

Also, Worms Armageddon is better than Worms 4 because the 3D worms games aren't anywhere near as good as the 2D ones IMHO.

---

### Post by Ferrat on 2008-02-18
The program doesn't have to change the xorg.conf to change resolution, the resolution is in two layers so to speak, one backend which is the true res and one frontend that can be changed without doing anything to the xorg.conf

But if you had an X crash that could reset or scramble your xorg settings

---

### Post by FrozenFox on 2008-02-18
> **bluej774 said:**
> I am convinced that it was Wine because that was the only program I was running at the time and the only one that was unusual.  When I played realMyst, the game did change my resolution and then it did crash before it changed it back.  However, even if the game did need to change the resolution, it should have been able to since the only way to do that is to mess with X and it didn't have the user rights to do so.

Also, Worms Armageddon is better than Worms 4 because the 3D worms games aren't anywhere near as good as the 2D ones IMHO.

Hehe. Apologies, I thought Armageddon was one of the 3d ones in my previous comment. I dislike the first 3d worms, but worms 4 is awesome imo. I didn't really enjoy worms 2, which many say is the "best" of the 2d worms games. But to each their own ;)

As for the wine problem, I'll just echo what Ferrat said, essentially. Though I will add: it would be great if you could try to reproduce your problem from a scratch install (perhaps in virtualbox/vmware?) and report it to the appropriate party so whatever is wrong doesn't happen to anyone else. We'd also like to know how it happened, even (or particularly?) if we are mistaken!  :)

---

### Post by asdfoo on 2008-02-19
> **bluej774 said:**
> I am convinced that it was Wine because that was the only program I was running at the time and the only one that was unusual.  When I played realMyst, the game did change my resolution and then it did crash before it changed it back.  However, even if the game did need to change the resolution, it should have been able to since the only way to do that is to mess with X and it didn't have the user rights to do so.

Also, Worms Armageddon is better than Worms 4 because the 3D worms games aren't anywhere near as good as the 2D ones IMHO.


If you are convinced it was wine, this would only be possible if you managed to make it run as root which is a big no no.  Even then there is nothing in wine which even mentions xorg.conf let alone would modify it.  It's also unlikely that worms armageddon decided to modify it because that would make very little sense at all.


I think this is a case of mistaken identity.

---

