---
title: "Anyone managed to get Direct2Drive games working with WINE? (TryMedia Protection)"
date: 2007-10-30
forum: Wine
---

### Post by carlosjuero on 2007-10-30
Just wondering if anyone has had experience getting games from Direct2Drive to run via WINE?

The way Direct2Drive 'protects' the purchase is by using a TryMedia 'activation' scheme (via GameSpy network/IGN Network) - I have managed to install Empire Earth 2 (D2D version) just fine, but when it starts it trys to activate the TryMedia via a locally routed web service call (I think it installs an IE plugin, but I can't find it on my Win 2k VM); The Mozilla plug-in for WINE doesn't have the ability to display this pseudo web page though, and thus the game never gets past activation.

I have tried installing on a Win 2K Virtual Machine and activating it; then I searched out any registry keys that were different and changed them accordingly, and I added the TryMedia folder that was under Local Settings\Application Data on the Win2k box to my WINE /windows/profile/all users/application data/. The folders contained a .lsn file which is the TryMedia liscence, but the launch of the game is still stymied by this bloody activation.

Thus I was wondering if any gurus here have managed to figure a way to tell the TryMedia thing that the license file exists and it shouldn't try for activation anymore.

Thanks in advance for any info.

---

### Post by cogadh on 2007-10-30
I don't think games bought through D2D can be installed with Wine. Every time I have seen that mentioned with games in Wine's AppDB, they have a garbage rating.

---

### Post by carlosjuero on 2007-10-30
Yeah, I am thinking that too - the only thing holding it back is the TryMedia protection schema; if there was a way to allow WINE to emulate it then everything would work fine :/

---

### Post by cogadh on 2007-10-30
It's the one great disadvantage of Wine, it doesn't work well with most copy protection schemes. Unfortunately, those schemes are not usually publicly documented in a way that would allow the Wine devs to code for them. That kind of documentation would allow too many people to figure out how to defeat the copy protection.

---

### Post by carlosjuero on 2007-10-30
> **cogadh said:**
> It's the one great disadvantage of Wine, it doesn't work well with most copy protection schemes. Unfortunately, those schemes are not usually publicly documented in a way that would allow the Wine devs to code for them. That kind of documentation would allow too many people to figure out how to defeat the copy protection.
Yeah, I figure it would be something like that. It would be nice if they would come out with a wrapper that would work with WINE or other Linux 'interpreter' programs though - that way they wouldn't have to release full source, just something that works properly with WINE (Since WINE is Open Source they could figure it out without releasing code to WINE couldn' they?)

Ah well, It was an experiement - if I could just figure out how to have IE actually mesh with the install routine then I think it would work.

---

