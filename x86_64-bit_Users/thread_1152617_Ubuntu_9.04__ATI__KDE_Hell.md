---
title: "Ubuntu 9.04 / ATI / KDE Hell"
date: 2009-05-08
forum: x86 64-bit Users
---

### Post by dh003i on 2009-05-08
I'm in Ubuntu 9.04 / ATI / KDE hell. When I upgraded, my Catalyst drivers were working "ok" (with problems with me not being able to get full 2048x1536 resolution no matter what I did, thanks to xrandr BS). 

After I upgraded, I got just an awful black screen with a 1/2 square inch random color mess as a "cursor". So I got rid of the Catalyst drivers; both using apt-get purge and by then manually deleting every occurence of fglrx on my system.

Then I tried the radeonhd drivers (from apt-get); got KDM login manager, and logged in, with a variety of failure/success for resolution depending on whether I left xorg.conf blank or used my old radeonhd xorg.conf file. 

But no matter what, KDE was buggy junk when logging in; it looks ok, and I can move that plasmoid thing around; but then when a terminal window pops up, I lose all window borders, and really can't do much of anything. WTF! (pardon me, this just really blows; after I get this working, I'm not upgrading again so early).

So, I try following [the RadeonHD guide here]("https://help.ubuntu.com/community/RadeonHD#Updating%20The%20Driver/Source"). I get up to the **git clone** step, then I get the following error:

```
**# git clone git://anongit.freedesktop.org/mesa/drm**
Initialized empty Git reposidtory in /home/davidjheinrich/source/drm/.git/ 
fatal: Unable to look up anongit.freedesktop.org (prot 9418) (Name or service not known)
```

What the heck?

What should I do? (at this point, I'm thinking just doing a fresh install of Ubuntu 9.04, while leaving my /home/ partition alone and not re-formatting it, may be easiest). Arg. 

Also, what about Canonical support? Is it worth the $250, are they going to be able to guide me through the problem, or am I just going to get stuck spending $250 with nothing worthwhile to show for it?

---

### Post by Yellow Pasque on 2009-05-08
You don't need to build drm modules with Jaunty (the Ubuntu devs wisely chose to patch the Ubuntu kernel so that Jaunty would support DRI and 2D acceleration on newer Radeon cards "out-of-the-box"). That guide is a bit outdated and I did update it last week, but didn't save the changes for some reason (*sigh). I guess I'll try again...

If it makes you feel better, I also had a terrible time with Catalyst/fglrx on my Kubuntu 9.04 test install with a RadeonHD 4550. I wouldn't hold out hope that paying Canonical would fix it. It was the first time I tried fglrx in a while, and it was a quick reminder of why I don't use those drivers. Unfortunately, they're the only option if you want 3D acceleration right now. [http://www.phoronix.com/scan.php?page=article&item=amd_r600_700_guide&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_r600_700_guide&num=1)

BTW, the git command works fine for me. You were connected to the internet, right?
```
$ git clone git://anongit.freedesktop.org/mesa/drm
Initialized empty Git repository in /home/dan/drm/.git/
remote: Counting objects: 37424, done.
remote: Compressing objects: 100% (15720/15720), done.
remote: Total 37424 (delta 29253), reused 27569 (delta 21326)
Receiving objects: 100% (37424/37424), 11.83 MiB | 490 KiB/s, done.
Resolving deltas: 100% (29253/29253), done.
```

---

### Post by dh003i on 2009-05-08
ok, maybe that's it ;-) Pinging google doesn't work:

```
** # pint 216.239.51.104**
connect: Network is unreachable
```

Great, another thing 9.04 broke. It was working fine in 8.10. It was plugged in through the surge-protector (cable modem => router => surge protector => computer), and I tried plugging the router directly to the computer; no difference. 

Plugging that same ethernet port on my router into my laptop, internet works fine and the port's indicator light on the router lights up (doesn't light up when connect to comp). What's going on?

Edit: Fixed network issue upon reboot. I don't know what was going on. I put a stronger dust-filter in front of the 2 intake fans in the front of the case, and over the intake vents for the PSU; BIOS readings didn't suggest much more heat. Could that have been why?

---

