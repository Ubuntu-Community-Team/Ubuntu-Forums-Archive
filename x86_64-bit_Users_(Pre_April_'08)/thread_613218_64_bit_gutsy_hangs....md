---
title: "64 bit gutsy hangs..."
date: 2007-11-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by crypticmystic on 2007-11-14
Just wanted to pipe in with another "64 bit Gutsy hangs"..  Actually I had slew of problems installing 64 bit Gutsy on my somewhat new Shuttle XPC with a duo care Intel that had been running 7.04 32 bit like a charm for the last 6 months...

Presented for information, but no ubuntu result was found (I ended up loading debian which worked first try no problems)...

0. gutsy 64 bit ran "live" like a charm. well a slow charm due to all the CD accessing, but like a charm...

1.  my default video screen is 640x480..  Oddly enough the grapical installer is simply to large to view on screen and there doesnt' appear to be a scroll to get the the "okay" buttons..  so I physically can't install on my machine... Fascinating..  I ended up having to switch to the textual installer...

2.  It didn't like installing over 32 bit 7.04...  It would install and then upon reboot, it would crash in grub..   I had to get a freaking windows disk and run fixmbr (gparted didn't help)..  Best I can guess is the old 32 bit grub that was there confused the 64 but grub and death to machine..  I guess I would have to recommend if possible for people to do this before trying to install 64 bit ubuntu on anything other than a completely fresh disk drive.

3. after fixing that major aggrevation by fixmbr and wiping my entire disc and reformatting it so that I knew would be formated by 64 bit unbuntu (which shouldn't make a difference)  I was able to install... eventually...    Upon booting up I get the desktop and within minutes (sometimes 1 sometimes 2 but never more than 5).... crash / lock....  not even enough time to look around the system...

I am sorry to say that while I am running 32 bit gutsy like a charm on my laptop..  I eventually gave up on ubuntu for my 64 bit machine (After trying assort boot options I could find here in the forums) and loaded 64 bit debian which loaded easily is has been rock solid...   Not a plug for debian, but more to say that it seems like my machine isn't flakey at least..  Just confusing to ubuntu somehow..

I understood that debian and ubuntu are pretty closely related, but clearly ubuntu tries to do more auto detection, so I presume my system has some quirk that confused 64 bit 7.10    Unfortunately this is a pretty important work machine that needs to run 64 bit linux (as all my customers do) so I won't be able to retry 7.10 for a while..

---

