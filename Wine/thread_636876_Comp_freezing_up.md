---
title: "Comp freezing up"
date: 2007-12-10
forum: Wine
---

### Post by Valok on 2007-12-10
So I'm trying to get WoW working via wine, but whenever I try and open a wine window, my entire computer freezes up and I need to reboot.  

I do have ubuntu installed via WUBI, could that be causing the problem?

---

### Post by cogadh on 2007-12-10
It is likely a sound problem. There have been several people on the forums with similar issues and they all seem to go away when they either disable or remove their sound card. Its not really clear why it happens, we haven't really gotten any info that might point to a common sound card or configuration as the cause. Try disabling or removing your sound card and see if the problem still occurs. If it doesn't, then maybe we can figure out why the sound seems to cause a conflict.

---

### Post by Valok on 2007-12-10
Thanks for the tip, I'm at work now but I'll try it once I get home.

---

### Post by Psykotik on 2007-12-10
If you run avant-window-navigator, [look there]("https://bugs.launchpad.net/awn/+bug/157179").

---

### Post by mpince on 2007-12-11
I'm having the same problem as Valok. I installed WINE and I can't even run notepad or the config for it-- or it will freeze. The mouse pointer won't move at all.

I disabled my onboard sound in the BIOS and that didn't help. I also tried using OSS rather than ALSA under multimedia system selector.

I'm also using wubi (but not avant-window-navigator).

Any suggestions would be great.

---

### Post by Valok on 2007-12-11
yeah those are the same exact symptoms Im having with the mouse not moving and all.  And unless Avant Window Navigator comes stock with the WUBI 7.04 then I'm not using it.

I don't know too much about how things in Ubuntu really work so I don't claim this to be a right answer......but.  Could our problem be due to the fact that both WUBI and WINE are "tricking" (so to speak) windows into allowing their own programs to work.

I'm in the process of taking my WUBI install into a full dedicated partition install, and once that is up and running Ill try WINE again and post my results here.

---

### Post by cogadh on 2007-12-11
There is no trick to it, Wine is just a compatibility layer, essentially the same as any other library already in Linux. The only difference is Wine uses an executable binary to access those libraries, rather than use the system directly. 

Wubi on the other hand, may be an issue because it is essentially a virtual disk, similar to one of the Ubuntu Live CDs. I'm not sure how that would interact with Wine, but in theory, all it should really mean is slightly slower disk access. I could see it causing a problem if you don't have sufficient RAM. Running an app in Wine increases your RAM usage to the point that there isn't enough to keep the virtual system running...

However, that's just a random guess, I've never actually used Wubi and my experience with virtual disks has never involved the simultaneous use of Wine.

---

### Post by Valok on 2007-12-11
Well to try and eliminate at least one factor, I'll report back here once I get a full install with its own partition going later on today.  I have a hunch that it might be the fact that we are using WUBI.  Both having the same symptoms and all.

---

### Post by Valok on 2007-12-12
> **cogadh said:**
> It is likely a sound problem. There have been several people on the forums with similar issues and they all seem to go away when they either disable or remove their sound card. Its not really clear why it happens, we haven't really gotten any info that might point to a common sound card or configuration as the cause. Try disabling or removing your sound card and see if the problem still occurs. If it doesn't, then maybe we can figure out why the sound seems to cause a conflict.


How would I go about disabling my sound so I can test if that is the problem with WINE?

---

### Post by cogadh on 2007-12-12
If your sound device is built into your motherboard, then go into your BIOS settings and you should be able to just disable it. If you sound device is an actual sound card, it's probably easiest to just physically remove it from the PC temporarily.

---

### Post by Valok on 2007-12-12
I do have on board sound, but Im pretty sure thats disabled cuz I got a new sound card a while ago.  Ill try both and report back once I get home and test it in a few hours.

---

### Post by cogadh on 2007-12-12
Ah, if you have both an on board and an off board sound card and the on board *is not* disabled in BIOS, that could be the source of the problem. I recommend you defintely start with that, rather than removing the off board card.

---

### Post by Valok on 2007-12-12
Good call, I'll ensure that the on board sound is disabled.  If it isnt, maybe it has to do with the other problem I was having which was that my sound only would work on every other boot up.

---

### Post by Valok on 2007-12-12
Well I disabled the on board sound (which actually fixed a couple other errors I was having) but WINE is still freezing my system when I try to do anything with it, including winecfg.

---

### Post by Valok on 2007-12-12
Alrighty I just took my sound card out and now WINE is working.  Now that I can get WINE to work, how do I go about working WINE and having sound?

---

### Post by cogadh on 2007-12-12
There's the million dollar question. At least now we have confirmation of the source of the problem in Wine. This is a long shot, by try configuring Wine, especially the sound settings, then re-install the card and see if Wine still locks up.

---

### Post by Valok on 2007-12-12
All righty, Ill have to play around with it.  

When I first went to the sound settings, it said I needed to install some drivers and that it had pre-selected some for me, should I DL those seleected drivers?

---

### Post by cogadh on 2007-12-12
No, just select the ALSA driver and apply the changes.

---

### Post by Valok on 2007-12-12
There are no check boxes next to either ALSA driver nor OSS Driver.

The only check box is next to NAS driver.

However, when I went into the audio section of WINE, my terminal reported back a bunch of error messages.  Not sure if those are of any importance, but if they are I can post them.

---

### Post by mpince on 2007-12-12
I don't understand. I disabled my sound card from the BIOS and I'm still having the same issue. No other sound card here.

Is there a place inside ubuntu to disable hardware as well?

---

### Post by cogadh on 2007-12-12
> **Valok said:**
> There are no check boxes next to either ALSA driver nor OSS Driver.

The only check box is next to NAS driver.

However, when I went into the audio section of WINE, my terminal reported back a bunch of error messages.  Not sure if those are of any importance, but if they are I can post them.
That's odd. I've never actually run Wine without my sound hardware enabled, but you should have the option to choose ALSA, OSS, NAS or JACK. I really wonder if your Wine install is screwed up somehow. Try doing a complete uninstall/purge/reinstall of Wine:
```
sudo apt-get remove --purge wine
sudo apt-get install wine
winecfg
```

> **mpince said:**
> I don't understand. I disabled my sound card from the BIOS and I'm still having the same issue. No other sound card here.

Is there a place inside ubuntu to disable hardware as well?
If you disabled it in BIOS, then there should be nothing else to disable, as far as Linux is concerned, you don't actually have any sound hardware anymore. You should also try the complete uninstall/purge/reinstall.

---

### Post by Valok on 2007-12-12
Ill give that a re install once I get home.  I think the version I am running at the moment is something .9.50 or something of the like.  I also didn't have the "JACK" option.  Any who, Ill reinstall and see what happens.

---

