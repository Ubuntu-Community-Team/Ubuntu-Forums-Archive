---
title: "Krazy KDE in Koala"
date: 2009-10-09
forum: x86 64-bit Users
---

### Post by MidnightVelvet on 2009-10-09
Long time Listener, First time Poster *grins* 


**-- Preface --**

To make a long story even longer... I decided to give the 9.04 -> 9.10 upgrade a go, figured it was stable enough and it couldn't be worse than the 4 years I was running Debian SID.

Anyways, started the do-upgrade before I left work one fine evening, only to return and see that the machine had completely frozen.  No huge deal, just a bit of a bummer.   

Rebooting... caused it to fail loading every kernel I had.  (.31 wasn't available, only the previous kernels fro 9.04... none would boot, even in failsafe).

No biggie, I boot off the live CD, chroot to my drive and apt-get update;apt-get upgrade.  Seems the koala bits were already there, it goes on, complains about a few packages.. no biggie.  

Reboot, it comes up, dpkg --reconfigure -a, re-run the update/upgrade and works brilliantly, more or less. 
[B]
-- The actual Issue --  [/B]

I can't log into KDE... *grins* 

e17 I have installed as well and it works like a champ, but it bugs me that KDE ceased functioning.  

From KDM it goes, shows the first drive icon... then never moves past it.

From a command line, startx provides me with a black screen with a mouse pointer.  The only errors given are the following:

(EE) Failed to load module "type1" (module does not exist, 0)
(EE) Failed to load module "freetype" (module does not exist, 0)

Freetype6 is certainly installed.  

Have attempted removing the .kde, any qt related files, and related bits in .local as well as /tmp/kde-user.  
[B]
-- Alternate Issue --[/B]

Alternatly, and one reason I gave this a go is that the kbuildsycoca / kbuildsyscoa4 systems have been since the initial install of 9.04, going bugnuts!

For example:
* 8386 velvet      21   1 1147m 1.0g 5936 R  100 50.5  23:53.31 kbuildsycoca4      *

It's currently taking up 100% of a CPU and 50+ % of Ram, and growing.  Usually this goes on (if I don't kill it) to eating up all Ram and Swap Space until the machine grinds into a very slow doorstop.  It also, never ever seems to finish... 

Other than that, everything seems to work, just figure i'm missing something...
**---**

Soo... anyone have any ideas?  I'm stumped.  Gone through error logs 'etc 'etc till my eyes bleed.  

Have a thought I'd love to hear it!!

**-- Specs --**

HP Workstation xw6400, 
2 Gig Ram,
NVidia NVS 285 Video Card



~Vel

---

