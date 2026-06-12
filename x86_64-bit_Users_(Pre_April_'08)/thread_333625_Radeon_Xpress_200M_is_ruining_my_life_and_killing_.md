---
title: "Radeon Xpress 200M is ruining my life and killing Dapper! (can't boot)"
date: 2007-01-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by Fruhwirth on 2007-01-07
Hello,

I am so stupid but not as stupid as the ATI Xpress Radeon 200M.

I have spent weekend after weekend after weekend trying to get the fglrx driver to work with the 200M. Direct Rendering simply will not work, no matter what I try. The stupid little glxgears barely  move, not to mention [how how poorly GoogleEarth has performed]("http://bbs.keyhole.com/ubb/showthreaded.php/Cat/0/Number/692015/page//vc/1") since I installed Ubuntu.  I tried [all this]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide") a dozen or more times but "direct rendering=" always, always says No in glxinfo.  Just this morning I discovered that there is a much newer driver than the one in the guide.  Argh.  I'm so dumb, but not as dumb as the 200M.

But that's the least of my worries now, for I have really fouled things up. While trying to update to the 8.32.5 fglrx drivers I have created the following boot error.

This is what I get when I try to load Dapper:

   * INIT: cannot execute "/etc/init.d/reS"
   * INIT: Entering runlevel: 2
   * INIT: cannot execute "/etc/init.d/re"

And then it just sits there, dead as a doornail.  There is no information above those three lines. I've become a bit of an Ubuntu bandit in the last two or three months since i installed, but fixing this is way out of my league.  For all practical purposes, I'm still a total newb.  I can follow instructions like a master chef, but if I begin to follow the wrong instructions (which is probably what I did to create this problem) I'm lost without a map and I don't even know it as I'm going along.

I have integrated ATI Radeon Xpress 200M on AMD64, 1.8 ghz, Ubunta Dapper. I have 128 of RAM out of 500 set aside for UMA video memory.

So I have two questions: 

1. How can I fix Dapper without reinstalling everything? i don't have a backup drive.

2. Is there a definitive guide on the fglrx driver, with the 200M on dapper?  There is so much info on this card with this driver that a newb has no idea who to trust/who to follow.

---

