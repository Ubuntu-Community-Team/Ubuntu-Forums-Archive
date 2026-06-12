---
title: "[SOLVED] flash with nspluginwrapper crashes entire computer"
date: 2008-01-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by nfriedly on 2008-01-15
This is a fairly new install of ubuntu x64 and I installed flash player with nspluginwrapper  and it worked great for about a week. but yesterday and today, flashplayer has completely crashed my computer after having it open for so much time. (typically less than a few minutes of interaction, but not immediately)

What happens is that artifacts of whatever flash movie is playing covers the entire screen for about 3 seconds then it goes blank. The system is completely unresponsive at this point, the capslock key doesn't even light up on the keyboard when I press it. I have to reboot and pick back up where I left off.

It's happened with different flash movies from 5-10 different websites including youtube and a few different company intro movies.

Do you guys have any recommendations on fixes, or maybe where I can find log files that would tell me what is going wrong?

about:plugins tells me this:
Shockwave Flash

    File name: npwrapper.libflashplayer.so
    Shockwave Flash 9.0 r115

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

---

### Post by Kilz on 2008-01-16
[Go here, get r48 release install script, run it. ]("http://ubuntuforums.org/showthread.php?t=476924")

---

### Post by Yellow Pasque on 2008-01-16
Yeah, I've noticed that r115 and Ubuntu don't seem to like each other (at least they didn't when 115 was beta). I'm running Arch Linux (64-bit of course) and I've had no issues.

---

### Post by Kilz on 2008-01-16
> **Temüjin said:**
> Yeah, I've noticed that r115 and Ubuntu don't seem to like each other (at least they didn't when 115 was beta). I'm running Arch Linux (64-bit of course) and I've had no issues.

I have scripts that install both on that post, but I recommend r48. It is more stable imho, especially for Kubuntu for some reason. I also suggest people having issues use r48. How do you like Arch?

---

### Post by nfriedly on 2008-01-16
> **Kilz said:**
> [Go here, get r48 release install script, run it. ]("http://ubuntuforums.org/showthread.php?t=476924")

Yep, that seems to have done it. I've been hitting flash sites left and right for about 40 minutes and no trouble yet.

Thanks!

---

