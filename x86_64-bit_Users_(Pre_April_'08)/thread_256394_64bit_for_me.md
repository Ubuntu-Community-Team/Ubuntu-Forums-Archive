---
title: "64bit for me?"
date: 2006-09-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by dracule on 2006-09-12
I bought a new laptop and was curious about if I should really do the 64bit. How much more performance do you get out of it?

specs: AMD TL-52 X2 turion64 processor
       Nvidia Go GeForce 6150 (posted to see if Nvidia driver will work)
       1 gb ram

I want to browse the web without an extreme amount of crashes, use open office, xgl, gimp, and watch dvd's. If the 64bit doesn't support those things, then ill just go with the 32 bit. I had Ubuntu on a different computer and am fairly knowledged about Linux, but never looked into a 64bit OS untill my laptop.

---

### Post by kuja on 2006-09-12
Shouldn't have any trouble using 64-bit for those scenarios. One sidenote about browsing the web though, it can require a little work to get certain plugins working. As per watching video, outside of dvds, watching things encoded with certain proprietary codecs (namely wmv, probably mov), requires you to install a 32-bit player. None of this is difficult however, and doesn't take more than a few minutes to set up.

As per performance in 64-bit land. For most applications you won't see much difference. In specialized areas, mainly things involving extreme math stuff, multimedia encoding/processing/design, you can see a significant boost in performance upwards of 20% or more depending on the application used.

---

### Post by incubus on 2006-09-13
dracule,

Kilz has packaged a distribution of firefox32 for amd64 that works very well. Everything is set automagically (although I just read his script and installed things by myself). In fact, I'm using firefox32 right now and haven't had any problems -- flash, real player, quicktime, and java plugins are working in amd64.

Funny that I think I never had all these plugins in any 32bit installation before (I never cared for installing them), so for me it was an improvement.

Performance is a tricky topic. I won't even give my opinion there. Since you have a good knowledge of linux, I would give it a try so you can see by yourself. If you start to get frustrated with amd64, you know it won't take more than a night to install Ubuntu x86.

incubus

EDIT: Oh, I should mention that there still are no w32codecs available for amd64 (that is probably implied by the package name). Although this is perhaps a matter of time, people have been reluctant to recompile and distribute it for 64bit because it's illegal in the first place. To me that just means I can't play WMV files. That's Ok in my case, but I know it can be a big deal for many other users.

---

### Post by dracule on 2006-09-13
Dont you need the w32codecs for dvd's?

---

### Post by Kilz on 2006-09-13
> **dracule said:**
> Dont you need the w32codecs for dvd's?

No libdvdcss enables reading encripted dvds and there is a way to install that. There is a way to install w32codecs, and a 32bit mplayer to play the wmv and wma files , everything else is available in a 64bit version. Check out the sticky.
But if you install my Firefox script with the mplayer plugin it automaticly installs w32codecs and the 32bit mplayer. Link in my signature.

---

