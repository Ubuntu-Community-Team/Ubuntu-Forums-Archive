---
title: "Wine completely locks up Gutsy"
date: 2008-07-26
forum: Wine
---

### Post by Morat on 2008-07-26
Newbie here, apologies if I'm asking stupid questions. I have recently installed Linux because I was fed up with Windows. Wifey hasn't realised yet!

The kids want to run some educational CDs which were, of course, built for Windows. Hence the need for Wine.

I have gone through the 'Howto: get the latest Wine' sticky but it makes no difference. I have installed all the updates for Gutsy, again with no effect.

If I select [wine]->[configure wine] or I run winecfg, within a couple of seconds the whole machine locks up: mouse freezes, keyboard fails to respond (including ctrl-alt-f2) and my only option is to hit the power switch!

If I can't run winecfg then I have no chance of running any Windows programs.

Any ideas on this? Also, how do I confirm that I actually have the latest Wine?

TIA.

--- Morat.

---

### Post by tye959 on 2008-07-26
Hmm well I would say, uninstall Wine, and then reinstall it again. (Dont have the link handy) There might have been a corrupt file causing your system to lock up. (Just a thought)

---

### Post by aoanla on 2008-07-27
Out of interest, why did you install Gutsy and not Hardy? I'm not sure that Gutsy is getting all the newest releases of Wine built for it anymore, since Hardy is the current release of Ubuntu.

---

### Post by Morat on 2008-07-27
> **tye959 said:**
> Hmm well I would say, uninstall Wine, and then reinstall it again. (Dont have the link handy) There might have been a corrupt file causing your system to lock up. (Just a thought)

I originally installed through a simple "apt-get install wine". This had the same problem of locking up the system. I was then informed by a colleague with more recent Linux experience that the version I had was probably not the latest and I should run through the "how to get the latest wine" on this forum. I've just done that and it still locks the system.

So I suppose effectively, I have already uninstalled and re-installed.

Thanks for the suggestion though.

I also have had a complete lock-up when opening a jpeg with f-spot photo viewer. I suspect that this may be related. Could it be anything to do with my onboard graphics which, I am told, is crap. lshw lists it as a VIA Technologies S3 Unichrome Pro VGA Adapter

--- Morat.

---

### Post by Morat on 2008-07-27
> **aoanla said:**
> Out of interest, why did you install Gutsy and not Hardy? I'm not sure that Gutsy is getting all the newest releases of Wine built for it anymore, since Hardy is the current release of Ubuntu.

Long story! Originally, I did install Hardy but I could not get it to automatically connect to my wireless router on login. My Gutsy live-cd did so I installed that.

---

