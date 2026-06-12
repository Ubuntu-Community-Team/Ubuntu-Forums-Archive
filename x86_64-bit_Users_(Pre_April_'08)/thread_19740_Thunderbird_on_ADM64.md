---
title: "Thunderbird on ADM64"
date: 2005-03-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by DougZ on 2005-03-13
Has anyone managed to get Thunderbird working on the AMD64 version of Warty?

Just installed and I'm really disappointed to have to go from using the latest version on Windows to an older version of Thunderbird that doesn't even work.

Well it works, as long as you never, ever, EVER try to write mail.  The second I click the button to send it just silently dies and "goes away".

I've tried searching the web forums to find a way to get it to work, or update it, or something, but no luck.

Any ideas?

---

### Post by FluffyElmo on 2005-03-13
I have it working under Hoary. For Warty try adding the backports repository to your sources list, they have a more recent versions of Thunderbird (and many other packages).

[http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/)

---

### Post by DougZ on 2005-03-13
Yeah, I upgraded to Hoary, which looks great btw, and it works fine.  Which is all I wanted.  Can't live without my e-mail. Sad really.

Did lose sound completely though after the upgrade.  :sad:

---

### Post by FluffyElmo on 2005-03-13
Hoary is definitely a step up from Warty. Glad your e-mail troubles are gone. 

Can't help with the audio, myself I just tried the different output subsystems under *System->Preferences->Multimedia Systems Selector* until one worked:)

---

### Post by bored2k on 2005-03-13
[QUOTE=DougZ]Yeah, I upgraded to Hoary, which looks great btw, and it works fine.  Which is all I wanted.  Can't live without my e-mail. Sad really.

Did lose sound completely though after the upgrade.  :sad:[/QUOTE]
 The input source you select in there [gstreamer-properties] must be the same youre media player is using. So if youre on ESD and like vlc, you would need to download esd plugin for vlc and make it use esd sound. Same on gxine, beep-m-p, xmms, etc.

I had that problem and now I get fully working multiple sounds [I'm on the default ESD, I Just made my apps use it].

---

