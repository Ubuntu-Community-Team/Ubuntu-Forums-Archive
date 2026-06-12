---
title: "Nothing opens anymore"
date: 2007-11-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by eallan on 2007-11-09
I'm a new ubuntu user.
So hello everyone :)

My issue is that on my HP Dv9500t that has ubuntu on it, nothing opens. 

Everything worked fine, I got envy working, compiz, etc. And basically seemingly randomly everything stopped opening under my user. I cacn use everything in the failsafe gnome log on. Other than that though i get the "starting ____" taskbar thing and nothing opens. 

System monitor, firefox, pidgin, nothing.

Thanks in advance.

---

### Post by eallan on 2007-11-12
Anybody have any ideas? :( Ubuntu is useless now i'd rather not do a clean install...

---

### Post by dabl on 2007-11-12
My vote is for an X server problem of some kind.

Before you throw in the towel and reinstall the OS, see if you can uninstall and reinstall your video driver.
:)

---

### Post by alex2035 on 2007-11-12
have a look at this thread [http://ubuntuforums.org/showthread.php?t=587905](http://ubuntuforums.org/showthread.php?t=587905) about freezes , lockups and strange behaviours on 7.10, you might find something for thought.

---

### Post by dabl on 2007-11-12
Hmmmm -- skimmed it, saw many complaints about all kinds of issues, some of which are not obviously related to others .....

I've been running Kubuntu Gutsy 64-bit since they released the RC -- and for 3 weeks prior to that I ran Tribe 5.  The only serious problem I observed was strigi -- the closest thing to a Linux virus I've seen.  :)

The claims of "freezes" and "crashes" are mostly just the X server -- true kernel panics are pretty rare, and my skim of your link didn't turn up any.  You can tell the difference between a system crash and an X server failure by doing the following on your "frozen" keyboard:

Alt-SysRq    r  s  e  i  u  b

Hold down Alt and SysRq, and then push the other letters one at a time, in sequence.  If it shuts down gracefully, it wasn't "crashed".  And if that's the case, then you can focus your attention on the video driver, the keyboard configuration, and related I/O functions.

I think IP v6 is behind some of the browsing problems -- it hasn't bothered me, but it can be a problem for some ISPs.  strigi just needs to be un-installed, IMHO.

I'm running a combination of 1 PATA hard drive, 4 SATA drives, an Asus CD/DVD drive and a floppy drive, and an Nvidia 7900 GS card.  I have compiz running great, and VMWare Player 2.0 running my Win XP virtual machine.  I have a Logitech Quickconnect STX, an Epson Perfection scanner, and a SD card reader, plus an Epson printer, all connected (sometimes) to the USB ports, plus an NTFS-formatted 8GB thumb drive that I mount as a disk drive.  It all works -- I've left it up for 3 and 4 days at a time, and I'm no guru, so I'm not buying into a theory that there's something seriously wrong with Gutsy -- at least not on my 2006-vintage hardware.  Other folks may have true compatibility problems -- that can happen.  And I don't use wireless, which seems to be kind of a little nightmare of its own, based on what I read.  :)

---

### Post by crjackson on 2007-11-12
> The only serious problem I observed was strigi -- the closest thing to a Linux virus I've seen. 
If you disable indexing using one of the gui settings applets (can't remember right now) doesn't this turn it off?  That's one of my first tweaks.

> Alt-SysRq r s e i u b
Hold down Alt and SysRq, and then push the other letters one at a time, in sequence. If it shuts down gracefully, it wasn't "crashed". And if that's the case, then you can focus your attention on the video driver, the keyboard configuration, and related I/O functions.
Wow, this is a cool trick.  I'll file this one away for future use.

> I think IP v6 is behind some of the browsing problems
I haven't personally had any problems with this, but I'm  planning on turning it off just to avoid future isues.  Thanks for you input.  Informative and useful as always.

---

### Post by dabl on 2007-11-12
> **crjackson said:**
> If you disable indexing using one of the gui settings applets (can't remember right now) doesn't this turn it off?



At the time (Tribe 5) I just marked the strigi package for removal, and clicked "apply".  Although here's a funny thing -- I just now checked and it's baaaaaaaaaaaaaaack!  :rolleyes:


> 

Wow, this is a cool trick.  I'll file this one away for future use.



Save your pencil:

_R_aising _S_kinny _E_lephants _I_s _U_tterly _B_oring

:biggrin:

---

### Post by eallan on 2007-11-25
I installed my video drivers with envy. I suppose i could try them again.

Any idea what this could be?

I'd reinstall but installing it on my 9500t was enough of a problem... 

Any ideas as to what this could be? 

I logged in to failsafe and reinstalled GDM and it worked again. However it's started doing it again with no "reason".

I didn't install or change anything to make it happen again. Ugh. It's so frustrating.

---

### Post by eallan on 2007-12-02
No one can help? 

Should i try reinstalling gnome? 

Reinstalling Ubuntu won't be easy as it was a huge pain in the *** the first time. I'd love to know what caused this too...

---

### Post by Ehtetur on 2007-12-02
When software on my system don't properly start, it usually something with dbus.
The next time it happens on your system, if you can get to a terminal - either gnome-terminal or ctrl-alt-F2 - enter this command to restart dbus:
> sudo /etc/init.d/dbus restart
See if that doesn't do the trick...

Did your initial ubuntu install go okay?

If restarting dbus doesn't fix it and ubuntu installed without problems, then it could besome kind of xorg/video driver issue - especially if you don't see the problems in failsafe.

---

### Post by eallan on 2007-12-11
It's not really a matter of "the next time" because it's still happening :). It doesn't come and go. It happens and then i can't fix it.

I can't even get into the terminal under my user name. Failsafe gnome is the only place i can run programs. Good call on it being a xorg issue. Would running envy and letting it autoconfig under failsafe help?

The install went kind of smooth. It worked after a couple tries with no variation in procedure. Occasionally it wouldn't boot into the live cd, then it just "did". I think i'll have to go with a reinstall but It's not exactly easy to get it to install in the first place ;).

---

### Post by eallan on 2007-12-15
I would stand for any help right now. Even how to reinstall it. I cannot boot into the live CD on my HP dv9500t. Anyone have any hep?

I can't figure out how to fix the X.org or the Xsession thing that is likely causing the problem. Especially if fail safe works.

---

