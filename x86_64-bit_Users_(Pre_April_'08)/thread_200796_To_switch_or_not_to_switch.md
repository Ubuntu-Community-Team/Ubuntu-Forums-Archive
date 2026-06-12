---
title: "To switch or not to switch?"
date: 2006-06-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by Xordan on 2006-06-20
Hi, I'm currently running 64-bit gentoo, but with ubuntu seeming to be quite nice I'm wondering about switching to ubuntu, mainly because I don't really have time for the compile times on gentoo any more, I need my PC a lot and don't like to leave it on overnight.

The biggest question I have is, how easy is it to set everything up on ubuntu for amd64? In gentoo, most things work great out of the box. Wine compiles 32-bit and is pre-configured to work, I have flash and java in my 32-bit firefox which took about 5 min to set up and I have a 32-bit mplayer which can play music which needs the 32-bit winlib package. 

Will I be able to just click install these things like on gentoo, or will I need to make some effort to get things to work just how I want? 

Thanks.

Edit: Reading a few other posts, it seems that ubuntu isn't really very good with out-of-the-box amd64 support. Maybe I'll wait for this to be improved to a level that I have now with gentoo before switching. Am I wrong with this opinion?

---

### Post by JoWilly on 2006-06-20
There is a sticky thread on top of this 64bit section that shows the apps that do not work out of the box with the workarounds (look into the posts too as the author did not update all the info in his first post, i.ex : 32bit flash/realplayer/etc... on firefox64 with the nspluginwrapper is still missing in the first post, you'll find it on the 2nd or 3rd page and also in other threads in this section).

Generally, you will install 32bit deb packages with "dkpg -i --force-architecture".

64bit works well and it is very easy to get everthing to work perfectly. Have a look at the above mentioned thread, and decide for yourself if it is too complicated for you or not.

EDIT: the xgl/compiz info is also outdated in the sticky. There is no difference in installing xgl on 64bit or 32bit; its very easy, you just need to add the right repo (raof's is best) to your apt sources list.

---

### Post by Xordan on 2006-06-20
Complexity isn't a problem, 5 years of gentoo usage has solved that. :P It's time which I can't afford to lose. As long as it's not going to take me hours to set things up then I see no reason why not to make the switch. I'll take a read of that thread and of the wiki and then decide. Thanks for your help!

---

### Post by JoWilly on 2006-06-20
[quote=Xordan]Complexity isn't a problem, 5 years of gentoo usage has solved that. :P It's time which I can't afford to lose.[/quote]

hehehehe... I beleive so :)

I also was a gentoo user for years before making the switch to ubuntu. Dapper64 definitely won't be a problem for you as everything can be fixed quickly and easily.

---

