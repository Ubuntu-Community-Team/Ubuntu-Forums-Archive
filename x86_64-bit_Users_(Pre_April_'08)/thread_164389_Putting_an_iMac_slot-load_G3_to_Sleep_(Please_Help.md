---
title: "Putting an iMac slot-load G3 to Sleep (Please Help!)"
date: 2006-04-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by Doobie9 on 2006-04-22
I have Ubuntu 5.10 Breezy installed on a slot-loading iMac. 700 Mhz, 768 megs of Ram.

Now, this is a smaller post than my last one that addresses just this issue (I've fixed most of the other ones myself). 
I have Ubuntu 5.10 Breezy installed on a slot-loading iMac. 700 Mhz, 768 megs of Ram.

Now, this is a smaller post than my last one that addresses just this issue (I've fixed most of the other ones myself). 

I need to know how to put this computer into full sleep and monitor sleep. I've looked all over these forums and all over the internet for a solution. I've checked the Wiki, and there's no mention of it. Now, maybe I'm using the wrong search terms. But I don't think so. Do any of you know how to fix this issue for me? I'd really appreciate some help.
I need to know how to put this computer into full sleep and monitor sleep. I've looked all over these forums and all over the internet for a solution. I've checked the Wiki, and there's no mention of it. Now, maybe I'm using the wrong search terms. But I don't think so. Do any of you know how to fix this issue for me? I'd really appreciate some help.

---

### Post by imacQ on 2006-04-22
i don't think this issue was ever resolved in breezy](*,) ; however, i think that dapper :-D  (still beta tester mode) has energy settings which can be set for mac sleep. official dapper release in june.

---

### Post by Doobie9 on 2006-04-22
Hmm. Does dapper fix it now? Could I download and install just the relavent dapper packages?

Or just update it to dapper? I think you do something with apt-get... not sure.

---

### Post by jxself on 2006-07-05
[QUOTE=imacQ]i think that dapper ... has energy settings which can be set for mac sleep.[/QUOTE]

It seems to work only somewhat.

I have installed Ubuntu 6.06 LTS ("Dapper Drake") onto a slot loading 400MHz iMac DV (specs here: [http://support.apple.com/specs/imac/iMac_Slot_Loading.html](http://support.apple.com/specs/imac/iMac_Slot_Loading.html))

The screen does indeed shut off after the time specified in "Put display to sleep when computer is inactive for:" (System -> Preferences -> Power Management.)

A couple of minutes later, though, the CRT turns back **on**. There is still no image though; just the black screen and (now) the glow produced by the now-live CRT.

I'd (obviously) like for the screen to remain off. I'm not sure where to look for why it doesn't stay that way.

System -> Preferences -> Screensaver is disabled ("Activate screensaver when session is idle" is not checked.)

I'd also like to be able to implement full system sleep (complete with the pulsating power light on the front), but one thing at a time...

---

### Post by Doobie9 on 2006-09-01
> **jxself said:**
> 
I'd also like to be able to implement full system sleep (complete with the pulsating power light on the front), but one thing at a time...

So would I. It seems like the kind of problem you fix with a kernel patch + rebuild, although I wouldn't know how to make that happen. It's a shame, too, because the computers of that generation are starting to get too old to run the latest Mac OS so they're going to need a good 'buntu substitute for those who absolutely need the latest OS and standards. ](*,)

I wish I could find out some more about this issue, it affect many other macs as well and it's the only thing preventing me from dual-booting my own computer.

---

