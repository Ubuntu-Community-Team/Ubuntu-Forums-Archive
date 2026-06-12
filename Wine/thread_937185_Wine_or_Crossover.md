---
title: "Wine or Crossover"
date: 2008-10-03
forum: Wine
---

### Post by N00b-un-2 on 2008-10-03
I'm wondering if Crossover works any better than Wine for windows programs.  I've used wine before and was thoroughly unimpressed.  It had a 0% success rate with ANY games at all and Cedega wasn't much better. It did Microsoft Office just fine, but I've since decided to stick it out with OpenOffice since it does everything I need it to do and then some.  I'll do anything to support the open source cause within reason, but at the same time I am a realist and I have certain needs and expectations from my computer.  I'm just wondering if it's worth the money to pay for Crossover.  The main program I'm interested in using is Fruity Loops 7, since I've paid good money for it and expect to use it.  I installed FL7 with Wine and was thoroughly unimpressed with it's performance-hangs, crashes, and the fact that the .DS (drumsynth) files are completely unusable and support of .wav files (which the vast majority of the samples I use are) is very hit or miss.  I was able to get them all to work after batching them out again using audacity, but there are literally THOUSANDS of .wav files that come with Fruity Loops (not to mention my OWN collection of samples).
I've paid good money for fruityloops as well as Sampletank2, and I damn well intend to use them.  I've tried using LMMS, and while it does provide some very minimal songwriting ability, the fact that I can't get any of my .VST or .DXI synths to work with it makes it useless to me.

---

### Post by howefield on 2008-10-03
There is no mention of Fruity Loops on the crossover office website, so that can't be a good sign.

I'd say a virtual machine would be your best bet.

---

### Post by asdfoo on 2008-10-03
> **N00b-un-2 said:**
> I'm wondering if Crossover works any better than Wine for windows programs.  I've used wine before and was thoroughly unimpressed.  It had a 0% success rate with ANY games at all and Cedega wasn't much better. It did Microsoft Office just fine, but I've since decided to stick it out with OpenOffice since it does everything I need it to do and then some.  I'll do anything to support the open source cause within reason, but at the same time I am a realist and I have certain needs and expectations from my computer.  I'm just wondering if it's worth the money to pay for Crossover.  The main program I'm interested in using is Fruity Loops 7, since I've paid good money for it and expect to use it.  I installed FL7 with Wine and was thoroughly unimpressed with it's performance-hangs, crashes, and the fact that the .DS (drumsynth) files are completely unusable and support of .wav files (which the vast majority of the samples I use are) is very hit or miss.  I was able to get them all to work after batching them out again using audacity, but there are literally THOUSANDS of .wav files that come with Fruity Loops (not to mention my OWN collection of samples).
I've paid good money for fruityloops as well as Sampletank2, and I damn well intend to use them.  I've tried using LMMS, and while it does provide some very minimal songwriting ability, the fact that I can't get any of my .VST or .DXI synths to work with it makes it useless to me.


I've used FL7 under Wine with success, I think I ran it continuously for 2 weeks.

Did you follow the instructions on the AppDB?  You have to add some information about the ogg vorbis codec or oggs won't play and it needs mfc42.dll otherwise some plugins will hang when it can't find this file, since it's not part of Windows, Wine does not have its own version.

The maintainers on the FL AppDB entry are quite helpful so you should ask them if you have any problems with the instructions.


As far as games go, which video card do you have?  If you have ATI then that would explain a lot of your problems, otherwise if you have nvidia then you should have a fairly good success rate (again if you look for instructions per app on the AppDB)

[http://appdb.winehq.org](http://appdb.winehq.org)

---

