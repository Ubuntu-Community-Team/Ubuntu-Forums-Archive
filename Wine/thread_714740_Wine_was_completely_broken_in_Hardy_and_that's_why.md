---
title: "Wine was completely broken in Hardy and that's why the backports took long"
date: 2008-03-04
forum: Wine
---

### Post by YokoZar on 2008-03-04
**PLEASE IGNORE THIS THREAD IT APPLIES TO HARDY BETA AND NOT THE RELEASED HARDY.  If a moderator could unstick it, that would be helpful.**


We're still narrowing down the cause of the segfaults in Hardy.  Some possibilities:

[list][*]Wine code (patches that might be related are going into 0.9.57 and will be coming soon)
[*]Fontforge (a change in its build system was causing Wine's marlett font to not build right since fontforge was upgraded)
[*]GCC (Hardy's GCC version recently got updated and the packages there are built with the latest rather than a forced old version like Gutsy.  Since newer GCC versions are generally faster than older ones, we tend to prefer them.  However, certain newer GCC versions have been breaking Wine's copy protection support, so we may still have to use an old one.)
[*]Something even stranger (Wine seems to run if compiled locally but not within pbuilder or the build daemon.)[/list]
You can track this bug (and it's *10* duplicates here: [https://bugs.launchpad.net/bugs/191575](https://bugs.launchpad.net/bugs/191575))

Anyway, this is where I've been spending my time lately.  I didn't want to just plop out a 0.9.56 release on all arches without making sure it wouldn't cause sudden catastrophic segfaults for some people, so I waited until now.


**PLEASE IGNORE THIS THREAD IT APPLIES TO HARDY BETA AND NOT THE RELEASED HARDY.  If a moderator could unstick it, that would be helpful.**

---

### Post by happyhamster on 2008-03-04
Good luck. And thanks for the heads up.

---

### Post by Sukarn on 2008-03-04
Wine 0.9.56 seems to be in the winehq repos now, and working fine for me, although I only tested opening one application in it since 0.9.55 from hardy repos would just segfault

---

### Post by Patriot1776 on 2008-05-11
So this is why Wine 0.9.46 can't be run in Hardy yet.  I need to use Wine 0.9.46 to be able to play my Source-engine games (Portal, HL2, TF2).

---

### Post by David1000 on 2008-05-11
Thanks.  Good to know it is not just me.  Spent a day trying to get wine to run before looking at Ubuntu Forums.

How will we know when the fixes are completed?

---

### Post by Mr_Congeniality on 2008-05-11
will compiling wine from source under hardy make Wine work?  I never got a chance to try in the 2 horus I had hardy installed.

---

### Post by Sukarn on 2008-05-12
You guys revived an old thread.

The hardy repository has got wine 0.9.59 in it, and the winehq hardy repository has got 1.0-rc1 at the moment.

---

### Post by cogadh on 2008-05-12
I was gonna say, isn't this thread in relation to pre-Hardy release problems? AFAIK, the only problem that might still remain is the font issue.
> **Patriot1776 said:**
> So this is why Wine 0.9.46 can't be run in Hardy yet.  I need to use Wine 0.9.46 to be able to play my Source-engine games (Portal, HL2, TF2).
Why do you need 0.9.46? All the games you mention work fine in the current versions of Wine. They certainly work much better than they did in version 0.9.46.

---

### Post by Patriot1776 on 2008-05-12
> **cogadh said:**
> I was gonna say, isn't this thread in relation to pre-Hardy release problems? AFAIK, the only problem that might still remain is the font issue.

Why do you need 0.9.46? All the games you mention work fine in the current versions of Wine. They certainly work much better than they did in version 0.9.46.

Somebody said however that when they upgraded beyond 0.9.46, their FPS rates went in the toilet, and my FPS rates were in the toilet too when I tried installing The Orange Box in Linux and running using Wine 0.9.59.

My system hardware is a Pentium D at 3.4 GHz, 2 GB system memory, nVidia GeForce 7300 GT with 256 MB onboard video memory.  FPS rates are awesome when running these games in a pure Windows environment, and in the crapper in Linux with the current versions of Wine.  Such a wide discrepancy in performance is unacceptable in my view.

The same person said downgrading to 0.9.46 restored his FPS rates.  That's why I'm wanting to downgrade to 0.9.46.

---

### Post by cogadh on 2008-05-12
Performance issues with Source-based games likely has more to do with your Wine configuration or your game configuration than the fact that you are using a newer version of Wine. If you are getting poor performance, then I would expect that you are either not configuring Wine or the game correctly at all, or configuring them based on info in an out-of-date how to. Since 0.9.46, there have been so many fixes added to Wine that specifically address problems running Steam and Source-based games that using some of the configuration tweaks that were required back when 0.9.46 was out actually *hurt* performance now. 

Then again, the problem could also be Hardy. With Gutsy, using 0.9.59 on a machine with a P4HT 3.0GHz, 2GB RAM and a GeForce 7600GS 256MB, I get HL2 performance that is equal to or better than Windows (up to 80+ FPS in Linux, 60+ FPS in Windows). My specs are certainly not exactly the same as yours, but they are comparable, the only major difference is the OS.

---

### Post by Patriot1776 on 2008-05-12
I'm thinking more its the fact I upgraded to Hardy then, because the only other Windows game I'm trying to run is Dawn of War: Dark Crusade and nothing seems to have changed performance-wise between Gutsy and Hardy.  It ran just as a fast on 0.9.59 as it did when I was running it on 0.9.49 under Gutsy.  I'll keep an eye here on the Wine forums for word then that Hardy's problems concerning wine have been fixed, or the wine developers have come with good workarounds for Hardy that correct things, and re-install version 0.9.59 then.

---

### Post by rofthorax on 2008-07-26
> **Patriot1776 said:**
> Somebody said however that when they upgraded beyond 0.9.46, their FPS rates went in the toilet, and my FPS rates were in the toilet too when I tried installing The Orange Box in Linux and running using Wine 0.9.59.

My system hardware is a Pentium D at 3.4 GHz, 2 GB system memory, nVidia GeForce 7300 GT with 256 MB onboard video memory.  FPS rates are awesome when running these games in a pure Windows environment, and in the crapper in Linux with the current versions of Wine.  Such a wide discrepancy in performance is unacceptable in my view.

The same person said downgrading to 0.9.46 restored his FPS rates.  That's why I'm wanting to downgrade to 0.9.46.

JULY 2008 JULY 2008 JULY 2008 Okay I'm updating this thread, to show this is not an old topic.. It is still relevant.. 

Yep Wine 0.9.46 is the only version I can run Guild Wars with a reasonable frame rate, I'm soon to be releasing a video demonstrating the sluggishness, It's not associated with 8.04, but just the fact that I can't get 0.9.46 for 8.04, has me wanting to go back to 7.10.. This best get this fixed or you will have fewer people adopting 8.04 LTS.

All Wine's post 0.9.46 (which was a standard install with Gutsy) seem to do some sort of IO blocking, as if it was trying to load in a portion of the scene, and it blocks all operation until that is achieved, leading to indefinite stalls in UI feedback.  0.9.46 DOES NOT DO THIS.. Also the shadow rendering looks as if the developers of Wine tried to do soft shadows and failed, I've seen such shadows in poorly designed shots in blender using the shadow buffer lights. 

I wish the Wine dudes would make a version of wine that permits people to switch between copies, or at least do some sort of static linking of the binaries and permit people to use whatever version of wine that is suitable. For example, Battlefield Vietnam will not work with 0.9.46, but it will work with later versions. If I have Wine installed for Guild Wars, I can't play BFV unless I deinstall 0.9.46 and install 0.9.60 or such.. And if I wan to go back to Guild Wars, I have to deinstall wine and reinstall 0.9.46.. It gets old.. 

But with Hardy, it is not even possible, unless one hacked it to work.. 

I'm amazed as to how this could pass by the wine developers.. It seems many people are having the same problem. Maybe that jump to 1.1.1 was a bit too quick..

---

### Post by rofthorax on 2008-07-26
> **cogadh said:**
> Performance issues with Source-based games likely has more to do with your Wine configuration or your game configuration than the fact that you are using a newer version of Wine. If you are getting poor performance, then I would expect that you are either not configuring Wine or the game correctly at all, or configuring them based on info in an out-of-date how to. Since 0.9.46, there have been so many fixes added to Wine that specifically address problems running Steam and Source-based games that using some of the configuration tweaks that were required back when 0.9.46 was out actually *hurt* performance now. 

Then again, the problem could also be Hardy. With Gutsy, using 0.9.59 on a machine with a P4HT 3.0GHz, 2GB RAM and a GeForce 7600GS 256MB, I get HL2 performance that is equal to or better than Windows (up to 80+ FPS in Linux, 60+ FPS in Windows). My specs are certainly not exactly the same as yours, but they are comparable, the only major difference is the OS.


Try Guild Wars on wine 0.9.46 then try 0.9.59 or later.. I've found messages about this problem at the Guild Wars wiki. I tried all sorts of optimizations to the OS, only to find that it's a problem with Wine..  Bugs may have gotten fixed, but software doesn't always get better, it gets different sometimes, take for instance Vista..

---

### Post by rofthorax on 2008-07-26
> **David1000 said:**
> Thanks.  Good to know it is not just me.  Spent a day trying to get wine to run before looking at Ubuntu Forums.

How will we know when the fixes are completed?

This is an old thread I just replied to some people with older messages.. Oops.. I am feeling your pain.. 

I want 0.9.46 for Hardy..

---

### Post by Patriot1776 on 2008-07-26
There any thread I can read up on then about going back to Gutsy then anytime I want?  I'm seriously considering it.

---

### Post by YokoZar on 2008-07-26
> **rofthorax said:**
> Yep Wine 0.9.46 is the only version I can run Guild Wars with a reasonable frame rate, I'm soon to be releasing a video demonstrating the sluggishness, It's not associated with 8.04, but just the fact that I can't get 0.9.46 for 8.04, has me wanting to go back to 7.10.. This best get this fixed or you will have fewer people adopting 8.04 LTS.You can generally install old packages into newer Ubuntu versions and still have them run.  Seriously, just plop the Gutsy deb into Hardy and try it.

> I wish the Wine dudes would make a version of wine that permits people to switch between copies, or at least do some sort of static linking of the binaries and permit people to use whatever version of wine that is suitable. For example, Battlefield Vietnam will not work with 0.9.46, but it will work with later versions. If I have Wine installed for Guild Wars, I can't play BFV unless I deinstall 0.9.46 and install 0.9.60 or such.. And if I wan to go back to Guild Wars, I have to deinstall wine and reinstall 0.9.46.. It gets old.. 
This idea has been floated before, and generally it's not worth the effort implementing such a feature and the complicated UI it would require compared with simply fixing the regression.

---

### Post by mc4man on 2008-07-26
> I want 0.9.46 for Hardy..  as posted should be no problem, just did the other day to test something. If you've built a ver. on hardy or otherwise installed it's build-deps you'll get a dep error 'libldap2-dev', simply remove and install 0.9.46.

---

### Post by Patriot1776 on 2008-07-26
> **mc4man said:**
> as posted should be no problem, just did the other day to test something. If you've built a ver. on hardy or otherwise installed it's build-deps you'll get a dep error 'libldap2-dev', simply remove and install 0.9.46.

Uh what do I have to do get 0.9.46 running in Hardy?  I just removed libldap2-dev and the package installer is still saying libldap2 isn't satisfiable.  Can I just install libldap2 and use it straight then?  (Is of course running Hardy, 8.04.1)

---

### Post by Patriot1776 on 2008-07-26
> **YokoZar said:**
> You can generally install old packages into newer Ubuntu versions and still have them run.  Seriously, just plop the Gutsy deb into Hardy and try it.

Didn't work for me, or am I trying the wrong one?  I tried the generic WineHQ deb for 0.9.46 and I got the libldap2 error.  What's the specific name of the deb I'm looking for?  Online Ubuntu package search is being a douchebag and not wanting to work at the moment.

---

### Post by mc4man on 2008-07-26
i'm sorry, forgot to add, there is no libldap2 in hardy, just a -dev. You need to install libldap2 from the gutsy repo. The easiest way is a direct download and install. The ubuntu .package site has been very hard to connect to lately, I'll edit in a link asap.

edit; packages.ubuntu.com can't be accessed atm, found the proper version here
[https://launchpad.net/ubuntu/gutsy/i386/libldap2/2.1.30-13.4](https://launchpad.net/ubuntu/gutsy/i386/libldap2/2.1.30-13.4)
So to confirm - remove the hardy version of libldap2-dev and install the libldap2 package from above (you don't need the -dev to install 0.9.46)

---

### Post by Patriot1776 on 2008-07-26
Alright, now I'll try re-installing the Orange Box in Linux and see if it works better.  If the framerate's awesome but the colors are screwed up, I'll look somewhere else.

---

### Post by Patriot1776 on 2008-07-27
> **mc4man said:**
> i'm sorry, forgot to add, there is no libldap2 in hardy, just a -dev. You need to install libldap2 from the gutsy repo. The easiest way is a direct download and install. The ubuntu .package site has been very hard to connect to lately, I'll edit in a link asap.

edit; packages.ubuntu.com can't be accessed atm, found the proper version here
[https://launchpad.net/ubuntu/gutsy/i386/libldap2/2.1.30-13.4](https://launchpad.net/ubuntu/gutsy/i386/libldap2/2.1.30-13.4)
So to confirm - remove the hardy version of libldap2-dev and install the libldap2 package from above (you don't need the -dev to install 0.9.46)

Thanks MUCH for that.  Wine 0.9.46 is installed and the Orange Box games are now working!  My framerates are through the roof, even with resolutions set to 1280 x 1024, what my computer is truly capable of with the hardware it has.  I think that needs to be stickied somehow for the newbies who were like me, installing Hardy and now wanting to play their Source-engine games in Linux.  Until the wine developers fix this blatant issue, 0.9.46 is the only option for Linux players of HL2 (EP 1+2), TF2, and Portal.

Sorry if it seems off-topic, but when I set everthing up to run Portal truly full-screen, my keyboard ceased to function when the game got there.

---

### Post by aoanla on 2008-07-27
> **Patriot1776 said:**
> I think that needs to be stickied somehow for the newbies who were like me, installing Hardy and now wanting to play their Source-engine games in Linux.  Until the wine developers fix this blatant issue, 0.9.46 is the only option for Linux players of HL2 (EP 1+2), TF2, and Portal.

Not at all, actually. I'm running Hardy 64-bit with Wine 1.1.0, and Source-engine games work perfectly. Indeed, I just played TF2 with it an hour ago...
You did *try* newer versions of wine before concluding that because 0.9.59 had problems, the later versions must also be broken, didn't you?

---

### Post by Patriot1776 on 2008-07-27
The repositories are up to version 1.0.0.  No debs yet for 1.1.0 right?

---

### Post by aoanla on 2008-07-27
> **Patriot1776 said:**
> The repositories are up to version 1.0.0.  No debs yet for 1.1.0 right?

Debs for 1.1.0, 1.1.1 and 1.1.2 exist in the budgetdedicated repo.

Indeed, I just got 1.1.2 installed between my original comment and this one.

---

### Post by Patriot1776 on 2008-07-27
*sighs* Just tried 1.1.2 and apparently the IO blocking that rofthorax was alluding to has not been fixed.  My framerate in Portal went back in the garbage.  I'm going back to 0.9.46 and probably staying there for good, or at least until the next wine-dev release, but I'm not holding my breath.  How important is the IO blocking?  Is there a way to turn it off?

aoanla, your framerates are not in the toilet with 1.1.0/1.1.2 like mine are?  Is it truly because you're using the 64-bit version and I'm using the 32-bit version?

---

### Post by aoanla on 2008-07-27
> **Patriot1776 said:**
> *sighs* Just tried 1.1.2 and apparently the IO blocking that rofthorax was alluding to has not been fixed.  My framerate in Portal went back in the garbage.  I'm going back to 0.9.46 and probably staying there for good, or at least until the next wine-dev release, but I'm not holding my breath.  How important is the IO blocking?  Is there a way to turn it off?

aoanla, your framerates are not in the toilet with 1.1.0/1.1.2 like mine are?  Is it truly because you're using the 64-bit version and I'm using the 32-bit version?

My framerates are fine with 1.1.2, and were with 1.1.0. Are you sure this is the IO blocking at issue?
Out of interest, do you have an ATI or an nVidia card? I'm using nVidia at the moment, and I had nothing but grief with my old ATI card and Wine - mainly due to ATI's shoddy drivers, rather than any Wine problem.

---

### Post by dmn_clown on 2008-07-27
> **YokoZar said:**
> This idea has been floated before, and generally it's not worth the effort implementing such a feature and the complicated UI it would require compared with simply fixing the regression.


(S)He could also download the source release for 0.9.46, compile (her)himself and use WINEPREFIX to use something outside of the default .wine for that particular version.  It'd be a PITA to rename the wine executables to allow for more than one version of wine in but it is doable.

---

### Post by Patriot1776 on 2008-07-27
> **aoanla said:**
> My framerates are fine with 1.1.2, and were with 1.1.0. Are you sure this is the IO blocking at issue?
Out of interest, do you have an ATI or an nVidia card? I'm using nVidia at the moment, and I had nothing but grief with my old ATI card and Wine - mainly due to ATI's shoddy drivers, rather than any Wine problem.

I'm starting to really wonder if I'm a special case or something, because I just installed the latest restricted nVidia drivers, I'm running a GeForce 7300 with 256 MB of video RAM.

After installing the drivers, framerate was still in the garbage.  And something else I've been forgetting to point out, and this was happening as far back as 0.9.59, the colors have been screwed up too.  Maybe that's a confirmation I've got a video driver problem.

---

### Post by aoanla on 2008-07-27
> **Patriot1776 said:**
> I'm starting to really wonder if I'm a special case or something, because I just installed the latest restricted nVidia drivers, I'm running a GeForce 7300 with 256 MB of video RAM.

After installing the drivers, framerate was still in the garbage.  And something else I've been forgetting to point out, and this was happening as far back as 0.9.59, the colors have been screwed up too.  Maybe that's a confirmation I've got a video driver problem.

Hrm. Just to check though, are you using the -dxlevel 81 option for running Source games? DirectX 9 has always been slow for Source-engine games in Wine, and I don't think 0.9.46 implemented enough of DX9 to cause any problems...

---

### Post by Patriot1776 on 2008-07-27
Do I put that in the command-line right after 'wine' but before the program I'm asking it to run?  I'm assuming yes.

---

### Post by Patriot1776 on 2008-07-27
> **aoanla said:**
> Hrm. Just to check though, are you using the -dxlevel 81 option for running Source games? DirectX 9 has always been slow for Source-engine games in Wine, and I don't think 0.9.46 implemented enough of DX9 to cause any problems...

That did it right there!  SOLVED!  Now it's running the way it should!

---

### Post by RealG187 on 2008-08-25
> **rofthorax said:**
> I want 0.9.46 for Hardy..

Install these two debs found in the zip at:
[http://ifile.it/zvacfdy](http://ifile.it/zvacfdy)

---

