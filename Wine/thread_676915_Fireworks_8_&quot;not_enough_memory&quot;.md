---
title: "Fireworks 8 &quot;not enough memory&quot;"
date: 2008-01-24
forum: Wine
---

### Post by robaldred on 2008-01-24
Hey, I am trying to run Fireworks 8 on wine 0.9.53
It installs fine, loads up, but when I create a new document or open an existing, there is a message in the top left "Not enough memory"

Anyone else had this issue and maybe have a solution?

Thanks
Rob

---

### Post by OliW on 2008-01-25
Same error here. *Subscribing*

---

### Post by simplysimple on 2008-01-28
same error as well...I had to laugh given that I just upgraded my ram to 4gig ddr2

hopefully there is a fix because i would really prefer to run a few programs without having to do a full blown virtualization of xp.

(subscribing)

---

### Post by SmileyChris on 2008-02-06
Ditto. Strange thing is, I was using it fine only a couple of hours ago and now I'm getting the "not enough memory" come up every time, even after a full system restart.

---

### Post by OliW on 2008-02-06
Well I still get the same on wine-0.9.54

Other people who are having this issue: is your ~/.wine folder on the same filesystem as / ?

I've got quite a perverse setup. My /home is on RAID5 and then, I have ~/.wine mapped out onto a single Raptor HD (because I don't need the security of RAID and I need the speed)

---

### Post by SmileyChris on 2008-02-06
> **OliW said:**
> Well I still get the same on wine-0.9.54

Other people who are having this issue: is your ~/.wine folder on the same filesystem as / ?

I've got quite a perverse setup. My /home is on RAID5 and then, I have ~/.wine mapped out onto a single Raptor HD (because I don't need the security of RAID and I need the speed)

Mine is on the same filesystem. I'm finding it extremely odd that I could be using Fireworks fine, then an hour later (with no system updates or anything) it decided that it wasn't going to play any more...

---

### Post by HornedBeast on 2008-02-18
Same issue here. Is 0.9.55 not in the wine repo for Gutsy yet? Maybe thats fixed it? Anyone compiled and tried it yet? Anyone compiled and put up a deb yet!?

---

### Post by OliW on 2008-02-18
I compiled it on Hardy. Still broken.

---

### Post by 247Production on 2008-02-20
I downloaded the Wine update this morning, and since then I've been getting the same 'out of memory' message. Before the update it was working fine.

I'm running Guitsy on an AMD64 machine with 2Gb of RAM

---

### Post by SmileyChris on 2008-02-20
Well I got frustrated with this today and did a bit of investigation:

[LIST=1]
[*] deleted ~/.wine
[*] installed Fireworks
[*] backed up ~/.wine
[*] used Fireworks until it broke
[*] compared ~/.wine-backup to ~/.wine
[/LIST]

Removing the Macromedia profile info seemed to fix it, and I narrowed it down to having the "Optimize" panel open.

Try this:

[LIST]
[*] collapse the optimize panel (F6 should do it)
[*] restart Fireworks
[*] without opening the optimize panel, see if things are working again -- they were for me.
[/LIST]

This doesn't really solve the problem because if you open the panel again the bug reappears. Annoying to say the least, since the best use of fireworks IMO is a web image slicing tool and the optimize panel is rather critical to this, but at least this is a start to figuring it out...

---

### Post by 247Production on 2008-02-21
Thanks SmileyChris, just managed to at least open an image that wasn't displaying yesterday, will see how it works out for the rest of the day.

Hope they fix the bug soon, this is our only Linux machine and was hoping my boss would let me rid the production office of Windows, things like this don't help my cause... although a Linux equivalent of Studio 8 would be nice!

---

### Post by OliW on 2008-02-21
> **SmileyChris said:**
>  Annoying to say the least, since the best use of fireworks IMO is a web image slicing tool and the optimize panel is rather critical to this, but at least this is a start to figuring it out...

Well I'm glad there's somebody else who uses Fireworks the same way as me. And top marks for your investigative powers. I can confirm that the optimise panel is the culprit.

I also tried detaching it from the sidepanel to see if that was any better but had no luck whatsoever.

I don't suppose anybody here knows of a good slicer/optimiser for Linux?

---

### Post by SmileyChris on 2008-02-21
If someone wanted to rollback Wine versions to see which version broke it (if it ever worked, but I thought I remember it working), that'd be enough for a bug report.

---

### Post by optimusmedia on 2008-04-11
Fireworks 8 is getting the same issue.  It happened about the time I upgraded to Hardy Beta. 

I too was able to use the optimize work-around, but that is a critical feature for firefox.

Anyone got an official bug report on this? Or know where I can start one?

---

### Post by SmileyChris on 2008-04-13
> **optimusmedia said:**
> Fireworks 8 is getting the same issue.  It happened about the time I upgraded to Hardy Beta. 

This is a bit of a confusing statemnt. What do you mean the "same issue" - we're all talking about Fireworks 8...

> Anyone got an official bug report on this? Or know where I can start one?

I don't think there is an official bug report for this - it probably would be a good idea to submit one through wine's bug tracker. When you (or anyone else listening) have done it, be sure to post the bug URL here.

---

### Post by hamamelis on 2008-04-20
"Ian  // Aug 21, 2007 at 4:37 pm
I’ve just upgraded to wine 0.9.43 and find that Fireworks8 has started to work fine. It even integrates with DW8. It does not seem to work with CX 6.1 which based on an older version of wine."

[http://luiscosio.com/how-to-dreamweaver-and-flash-8-running-on-ubuntu-dapper](http://luiscosio.com/how-to-dreamweaver-and-flash-8-running-on-ubuntu-dapper)
I posted the above  so Fireworks8  worked with wine 0.9.43. 
Hope this helps with the roll back to a working version.

---

### Post by hamamelis on 2008-04-22
I can confirm what is on the post below. Fireworks8 works with wine v51 (including Optimise) but gives the out of memory error with v52 and after up to 59, the latest I tried.
[http://groups.google.com/group/comp.emulators.ms-windows.wine/browse_thread/thread/ff162855a40f2211/b44177cfc3e0f0b4?lnk=raot#b44177cfc3e0f0b4](http://groups.google.com/group/comp.emulators.ms-windows.wine/browse_thread/thread/ff162855a40f2211/b44177cfc3e0f0b4?lnk=raot#b44177cfc3e0f0b4)

This is in line with the bug report:
[http://bugs.winehq.org/show_bug.cgi?id=7125](http://bugs.winehq.org/show_bug.cgi?id=7125)

---

### Post by LinuxRocks713 on 2008-04-22
Fireworks MX works perfectly in Wine 0.9.59.

---

### Post by OliW on 2008-04-22
Which version number is MX?

---

### Post by SigmaSanti on 2008-04-23
I have the same problem too with Fireworks MX 2004, not enough memory error. The error in windows is the result of - you guessed it - not enough memory. Does wine inhibit the amount of memory windows applications can run? It seems like that should be easy to fix.

---

### Post by optimusmedia on 2008-05-02
I somehow lost my subscription to this thread... but an update.  It seems to have been solved by some system update.  I am using wine 0.9.59. and Fireworks 8.

If this is solved for the rest of you, I'll edit the subject to solved.  Sorry I don't know more.

---

### Post by SmileyChris on 2008-05-02
I'm pretty sure the issue is still there for me. You can open up and use the optimize panel now?

---

### Post by simplysimple on 2008-05-04
I had a large project at work and ended up using windows since I was unable to get this issue resolved awhile back...i decided to recently give it a shot agian and got the error when opening the align panel/window....just thought i would give an update for what's it's worth.

I really hope this is resolved because I'm 92% on my way to ditching windows and switching to ubuntu!!

Hope this finds everyone doing well.

Take care!

---

### Post by SmileyChris on 2008-05-04
Huzzah!

I use the [official Wine APT repository]("http://www.winehq.org/site/download-deb") and they just released v0.9.61.

It solved all the problems for me.

---

### Post by simplysimple on 2008-05-09
I hope you are right that all the problems are solved. I gave up and am running Virtual Box again...a fine trade off for what I'm doing. I hope you continue to be able to run FireWorks using Wine without error.:) 

Take care!

---

