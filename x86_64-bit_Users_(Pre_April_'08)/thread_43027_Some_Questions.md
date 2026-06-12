---
title: "Some Questions"
date: 2005-06-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by Krogen on 2005-06-20
After desperately failing to install ubuntu 32 bit on my PC, I will try to install 64 bit today on my AMD64 PC. Gentoo 32 bit installed fine but then, after a reboot, the whole thing went to... hell. Hard freeze. Tried it 3 or 4 times. Right now I'm running MEPIS which is a simple, fine, high-end distribution but it's not exactly what I'm looking for. 

So... Couple of questions.

1. Will 32bit apps work? I read something about chrooting the environment but, then again, how would I got about doing this? Any good places for walkthroughs?

2. Perfomance. How big is the perforamce gain between 32 bit and 64? Is there any at all for a normal user who likes to browse the web, play some PC games, and uses CAD software (ok, maybe not that normal PC user, lol)?

3. Will Cedega or WineX work? Cedega/WineX is a program for emulating Windows games and applications. I don't care much about Wine itself.

4. Is there anything I should know about the 64 bit version? So far I have read that there is no flash plugin for firefox, which I don't really care about but would like to have it. Anything else?

Thanks so much.

---

### Post by intangible on 2005-06-20
The biggest difference between 32 bit and 64 bit is the amount of addressable memory... shouldn't make a huge difference unless you have more than 4GB of ram.

With native 64 bit programs you may see small improvements some places, and other places maybe a little slower.  From what I understand, most 32 bit programs will run on the AMD 64 with no problems.

If I had a 64 bit processor, I'd be running it on 64 bit OS too :D

Here's a 32 bit chroot howto [http://www.ubuntuforums.org/showthread.php?t=24575](http://www.ubuntuforums.org/showthread.php?t=24575)

Good Luck.

---

### Post by FluffyElmo on 2005-06-20
1. Most 32bit apps have 64bit ports, though you're bound to find some that don't and you'll have to run them in a 32bit chroot. Tthe link provided by intangible is the best for that.

2. Performance. I've found a noticeable increase in video encoding and in some of my Java development. Performance is pretty much indistinguishable for most applications though (they're plenty fast under both). There are also a couple of 64bit ported games (ie Unreal), which might see a small boost as well.

3. I don't use cedaga myself but it reportedly works. The unofficial cedega wiki has instructions: [http://digital-conquest.ath.cx/wiki/index.php/Ubuntu#How_to_install_Cedega_on_AMD64](http://digital-conquest.ath.cx/wiki/index.php/Ubuntu#How_to_install_Cedega_on_AMD64) 

4. In addition to Flash, 64bit is missing some win32 audio/video codecs. Some applications (ie OpenOffice2) that have been problimatic in the past work now, but you may have to spend some more time getting them going. Worst case, pretty much anything can be run in a chroot. For instance if you *need* Flash and all the codecs you can get them working by installing the 32bit versions in a chroot. 

Overall, I've been very happy with the stability and performance of the 64bit version and I don't really mind the odd bit of extra effort needed here and there because I've learned a *lot* from the experience. But you tolerance for frustration may be different than mine so plan accordingly:)

Good Luck!

---

