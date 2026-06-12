---
title: "Ubuntu vs Windows Vista"
date: 2006-12-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by in_flu_ence on 2006-12-28
I might be a new user so bear with me if I might have gotten wrong facts.

At the moment, I have tried using Ubuntu Edgy 32bit and 64bit but it seems that the 32bit is much more stable in terms of hardware support and compatible software (drivers, plugins etc).

I am just wondering that since Windows Vista is focusing very much on 64bit computing. Will it make ubuntu fall into the lag behind the support of 64bit? Just my fear because I do love to use the 64bit capability for my workstation applications while not missing the fun of the well patched home pc for my multimedia entertain and web surfing.

Thanks

---

### Post by pseudonym on 2006-12-28
> **in_flu_ence said:**
> I am just wondering that since Windows Vista is focusing very much on 64bit computing. Will it make ubuntu fall into the lag behind the support of 64bit? 
I should think that the opposite will be the case. The brutal truth is that 64-bit computing on the desktop won't pick up overall until it picks up on windows. But more 64-bit software development overall will mean more 64-bit software development for linux. All things consideed, though, I don't think we're doing too badly now :)

---

### Post by in_flu_ence on 2006-12-28
If software development relies on the development in Windows, won't it seem as though we are always tailing behind Windows in some sense?

Of course, I do foresee that 64bit development will go mainstream in Linux in future. However, it looks, to me, that we are at the 'waiting' stage. Waiting for some breakthrough in Windows before planting it back to Ubuntu.

It will be a pity that Linux develops 64bits first for the use in server while we have to lag behind in 64bit for home computing.

---

### Post by pseudonym on 2006-12-28
> **in_flu_ence said:**
> If software development relies on the development in Windows, won't it seem as though we are always tailing behind Windows in some sense?

Of course, I do foresee that 64bit development will go mainstream in Linux in future. However, it looks, to me, that we are at the 'waiting' stage. Waiting for some breakthrough in Windows before planting it back to Ubuntu.
I think you are confusing technical development with user-base development. There's no reason to assume that 64-bit Linux will be technically inferior to 64-bit Vista once that's been around for, say, a year. Indeed, if history is anything to go by, the reverse will be true (eg. you can't tell me the 'Aero' desktop didn't rip off all the desktop eye-candy development done over years by especially KDE).

But there's every reason to expect that once 64-bit desktops have gone 'mainstream' that developers like Adobe and whatnot, and maybe even some game developers, will be more inclined to support 64-bit Linux - to at least the extent they do now in the 32-bit world. Simply because what user base there is, will be there.

It's all governed by the playing out of market forces. More demand equals more pressure to meet the demand. and the way things are right now, the bigggest mover and shaker in the desktop demand-driving stakes is windows. But Linux will follow in its niche market wake, like it always has, and hopefully even grow a little in the desktop area (it *will* keep growing in the corporate/server arena). This is entirely separate from how good Linux is technically compared to windows, though.

---

### Post by in_flu_ence on 2006-12-28
Don't take it offended. In fact, I had all my systems installed with ubuntu. It is just that there had been alot of 'marketing' from windows about their windows vista and the stringent hardware specs to fit it while that had been this 64bit forum which had alot of issues regarding support to 64bit linux. That's why I want to clear some doubt.

Certainly, I have confidence in using linux particularly ubuntu for current desktop environment. I have all my hardwares recognised through a clean install. This is not possible in XP or even in other linux distros.

---

### Post by pseudonym on 2006-12-28
> **in_flu_ence said:**
> Don't take it offended. 
I'm not offended at all. I sincerely hope you weren't offended by anything I wrote, either. :) I was merely pointing out that the take-up of 64-bit technology on the desktop will be largely driven by windows, seeing as MS has by far the greatest market share in this sector.

This is no bad reflection on Linux, just an economic reality.

> **in_flu_ence said:**
> It is just that there had been alot of 'marketing' from windows about their windows vista and the stringent hardware specs to fit it while that had been this 64bit forum which had alot of issues regarding support to 64bit linux. That's why I want to clear some doubt.
It will be interesting to see how much MS push 64-bit Vista compared to 32-bit. I don't think they will have a choice if they want to differentiate the new product from XP. And the more they push 64-bit, the more the desktop market in general goes 64-bit. And that can only be good for us :)
Then it just comes down to the software developers.

---

### Post by kleeman on 2006-12-28
This analysis by Eric Raymond (esr) is relevant to the discussion here:

[http://www.catb.org/~esr/writings/world-domination/world-domination-201.html](http://www.catb.org/~esr/writings/world-domination/world-domination-201.html)

His claim is that the 64bit 32bit nexus will be the deciding factor in the desktop wars between windows and linux. He makes the point that getting Windows working well on 64bit is by no means guaranteed given the realities of M$ and the huge unwieldy codebase. Interesting read.....

---

### Post by solarwind on 2006-12-28
Actually, I agree with the above posts as well. Linux had, has and always will have better multitasking and 64 bit abilities than any garbage microsoft puts out. If something is not working out for you (in particular), don't hesitate to post and we'll try to help.

---

### Post by in_flu_ence on 2006-12-28
That's an interesting read.

---

### Post by blitze on 2006-12-30
Haven't done my reading yet but I'll give my 2 cents given I have tried both.

Vista 64 is not anyway near ready for prime time.  Driver support and on XP64 sucks but I will grant Vista 64 one thing, good 32bit compatability.

That being said, Vista 64 will be driven by MS and their DRM stalwarts because if you want HDVD or BlueRay to work it will only be supported on Vista64.  Vista 64 is laidened with DRM through and through in a way that will seriously hamper personal computing the way we understand it (hardware doing millisecond checks with each other to verify DRM compliance).

I have therefor chosen to forget Vista64 and look at Ubuntu 64.  Currently I am running Feisty 64 and with good results.  The kernel 2.6.20 has some issues on loading that I have filled a bug report on.  This issue is with the Ali chipset I run on and SATA/USB (seems to hang between these to loadings) but this was not an issue with kernel 2.6.17 on Edgy.

All my hardware is supported including my Echo Gina3G.  I have realtime kernel support for audio purposes that I can not get under Vista (audio isn't supported for my hardware yet and even when it is Vista's new audio subsystems are in user space and slow).  Nvidia drivers for my 7600GT run well but Compiz is still a work in progress and when I lauch programs/windows using Compiz I get the window top burrying under my top screen bar.

Quake 4 runs no problem and I have had Red Orchestra running under Wine but the current version of wine isn't working for me with that program yet.

All in all, I think Linux 64 is far more ready on the desktop than Windows 64 but there are still apps I want on Linux I can't get like Reaper for Audio and also some other commercial apps I use for work.  I hope the move to 64bit computing and the DRM crap being rammed down our throat under Windows Vista is a great boon for Linux as a viable alternative and the MPIAA and RIAA can go and get F-ed for all I'm concerned (main pushers for DRM along side MS who wants to control digital content delivery).

---

### Post by blitze on 2006-12-30
Just finished reading World Domination 201.  Great read and very valid.

I hope for our sake we can implement a means to ensure Linux becomes a major player on the 64bit desktop bacause the alternative for computing will make me want to switch off and go without.

---

### Post by kleeman on 2006-12-30
> **blitze said:**
> Haven't done my reading yet but I'll give my 2 cents given I have tried both.

Vista 64 is not anyway near ready for prime time.  Driver support and on XP64 sucks but I will grant Vista 64 one thing, good 32bit compatability.

That being said, Vista 64 will be driven by MS and their DRM stalwarts because if you want HDVD or BlueRay to work it will only be supported on Vista64.  Vista 64 is laidened with DRM through and through in a way that will seriously hamper personal computing the way we understand it (hardware doing millisecond checks with each other to verify DRM compliance).

I have therefor chosen to forget Vista64 and look at Ubuntu 64.  Currently I am running Feisty 64 and with good results.  The kernel 2.6.20 has some issues on loading that I have filled a bug report on.  This issue is with the Ali chipset I run on and SATA/USB (seems to hang between these to loadings) but this was not an issue with kernel 2.6.17 on Edgy.

All my hardware is supported including my Echo Gina3G.  I have realtime kernel support for audio purposes that I can not get under Vista (audio isn't supported for my hardware yet and even when it is Vista's new audio subsystems are in user space and slow).  Nvidia drivers for my 7600GT run well but Compiz is still a work in progress and when I lauch programs/windows using Compiz I get the window top burrying under my top screen bar.

Quake 4 runs no problem and I have had Red Orchestra running under Wine but the current version of wine isn't working for me with that program yet.

All in all, I think Linux 64 is far more ready on the desktop than Windows 64 but there are still apps I want on Linux I can't get like Reaper for Audio and also some other commercial apps I use for work.  I hope the move to 64bit computing and the DRM crap being rammed down our throat under Windows Vista is a great boon for Linux as a viable alternative and the MPIAA and RIAA can go and get F-ed for all I'm concerned (main pushers for DRM along side MS who wants to control digital content delivery).
That sounds broadly consistent with esr's argument. His claim is that Linux is much better positioned for 64bit in the area of drivers because most of them just require a recompile of open source code while windows has a ton of closed proprietary crud which each vendor has to change to 64bit....

---

### Post by in_flu_ence on 2006-12-30
pretty much consistent with esr's report. I agree on the point about using open source technology especially in driver development.

Just a wild thought. Since Apple is based on UNIX which is quite similar in some sense to Linux, do you think that the Linux community can 'partner' with Apple in some way in terms of driver development? I suppose Apple does alot of driver development themselves to make sure 3rd party hardwares are compatible with APPLE computers.

I shall wait for the real 64bit Linux in future.:P

It just make me wonder again in another sense. Is it wise to have AMD chip then since we cannot maximise the capability in any case? Probably even the new Intel chips.

---

