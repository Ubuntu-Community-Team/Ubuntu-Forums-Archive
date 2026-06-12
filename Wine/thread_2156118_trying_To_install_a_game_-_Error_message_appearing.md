---
title: "trying To install a game - Error message appearing. Please help"
date: 2013-06-20
forum: Wine
---

### Post by WaterwineFear on 2013-06-20
Hi all, So i have family who use linux and after being moaned at to get on board i decided i would give it a go, Got a brand new laptop and installed Ubuntu on it yesterday so i know it's the most up to date version.
I already have wine etc downloaded so i can open .exe files etc, However when i try to download any games i have on hard disk i am having trouble. I have already googled how to install "xxx" game on ubuntu but get so many varied resuts im really not sure where to begin. 

I am brand new to ubuntu so i really dont quite have a technical grasp on the whole system yet so i would appreciate some simple answers.(even though i know they can only be so simple)
Im not looking for anyone to hold my hand type thing through the process, Just looking for some decent pointers. To start with i keep getting seperate errors for different games so i shall stick with one at a time and hopefully somebody can help me. Here goes.

So i am trying to install command and conquer the first decade. When i put the disk in i go to the DVD sig at the side of the page and click The autorun.exe file ,I get the install window up (looks good so far) I select run in wine and recieve this message  shortly after the installshield wizard loads up  " an error -5006 : 0x8000ffff has occured while running the setup, Please make sure you have closed any other applications and this is the only set up running, If the error still persists please contact ea. Now i can select detail and when i do i get this 
" >kernel.serviceprovider/cpp(109)"
and then a whole list of othe "kernel errors, sorry i would list them but it isn't letting me copy and paste and there must beover 100 there. 

Now i was having different errors earlier, with seperate games, however i know for a fact that the game disk here is in working order etc as i was playing it on a different PC not too long ago at all. 
Im really baffled by it all and dont even know where to start here. Can anyone advise me on what to do? Cheers

---

### Post by Mark Phelps on 2013-06-20
Sorry to break the news to you, you're being new to Linux, but Wine is not the miracle cure some folks claim.  It is a hack of Windows DLLs that were rewritten to replace Windows system calls with Linux system calls.  The experience running stuff in Wine ranges from outstanding (when the app/game is rated Platinum) to disastrous (when the app/game is rated Garbage).

BEFORE you try to install anything using Wine, you can save yourself a lot of grief if you go to the WineHQ website and look up the app/game you want to install.

The page below is from that website -- and, as you can see from the rating, it is Silver -- which is not good:  [http://appdb.winehq.org/objectManager.php?sClass=application&iId=3328]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=3328")

Generally, while an app can work to some degree with a Silver rating, any game needs a Gold or better to be useful.

You should read through the Test Results on that page.  There may be some hints that are useful in getting the game to work.

The sorry fact of the matter is that the best environment for playing Windows games -- is Windows.

---

### Post by howefield on 2013-06-20
Thread moved to the "*Wine*" forum.

---

### Post by WaterwineFear on 2013-06-20
> **Mark Phelps said:**
> Sorry to break the news to you, you're being new to Linux, but Wine is not the miracle cure some folks claim.  It is a hack of Windows DLLs that were rewritten to replace Windows system calls with Linux system calls.  The experience running stuff in Wine ranges from outstanding (when the app/game is rated Platinum) to disastrous (when the app/game is rated Garbage).

BEFORE you try to install anything using Wine, you can save yourself a lot of grief if you go to the WineHQ website and look up the app/game you want to install.

The page below is from that website -- and, as you can see from the rating, it is Silver -- which is not good:  [http://appdb.winehq.org/objectManager.php?sClass=application&iId=3328](http://appdb.winehq.org/objectManager.php?sClass=application&iId=3328)

Generally, while an app can work to some degree with a Silver rating, any game needs a Gold or better to be useful.

You should read through the Test Results on that page.  There may be some hints that are useful in getting the game to work.

The sorry fact of the matter is that the best environment for playing Windows games -- is Windows.

Yes i realize it isnt a miracle and i thought some "newbies" may have been over selling it, wow i didnt even know about the silver and gold rating thanks for pointing it out to me.
Do you know anything about the error? or any app/program that may run them well?
it really is a shame, i do like linux and would hope i could use it properly, (i already have the harddrive 100% linux lol)
Might not have been the smartest move, but i just decided it "was for the best".

I shall read through them and see if there is anything there cheers for your advice.

---

### Post by Mark Phelps on 2013-06-20
> **WaterwineFear said:**
> ...I  do like linux and would hope i could use it properly ...

Well basically, you CAN use it properly -- just not to play Windows games.

One of the hardest things for folks to come to terms with when they "move" to Linux is that it is not a free version of Windows; instead, it is a free Alternative to Windows.

The more you try to replicate Windows in Linux, the more disappointed you will become.

Game limitations (and other things like BIOS updates and hardware firmware updates) are among the reasons that many folks keep a Windows installation around in dual-boot mode --- 'cause there are just some things that are routine in Windows that are impossible in Linux.

---

### Post by WaterwineFear on 2013-06-20
> **Mark Phelps said:**
> Well basically, you CAN use it properly -- just not to play Windows games.

One of the hardest things for folks to come to terms with when they "move" to Linux is that it is not a free version of Windows; instead, it is a free Alternative to Windows.

The more you try to replicate Windows in Linux, the more disappointed you will become.

Game limitations (and other things like BIOS updates and hardware firmware updates) are among the reasons that many folks keep a Windows installation around in dual-boot mode --- 'cause there are just some things that are routine in Windows that are impossible in Linux.

Yeah linux is great, but it's lacking in some departments, I wonder why They cant just match upto windows in some apects sometimes as im sure they would be more than capable :)
There are some great aspects geared towards programming and i love the fact it is open source as well, I can see why people would keep a dual boot. 

Thanks for your help :)

---

### Post by Mark Phelps on 2013-06-21
>  I wonder why They cant just match upto windows in some apects sometimes as im sure they would be more than capable

It's not really Windows that's the problem, instead, it's the software vendors and hardware vendors that rely on specific hardware features and drivers for their products to work well.  Since their market is over 90% Windows and probably no more than 1% Linux, and given the costs of hardware and software development for both are about the same, which market do you think they're going to actively support?

Even companies like AMD, that have a strong history of actively supporting Linux have fallen off recently.  As an illustration: I can use hardware accelerated drivers on my AMD 4290 not only in Win7, but also in Win 8 -- as AMD recently resurrected their driver support for this chip; but in Linux, I am relegated to the open-source drivers because AMD dropped Linux driver support for this chip last summer.

---

### Post by WaterwineFear on 2013-06-25
> **Mark Phelps said:**
> It's not really Windows that's the problem, instead, it's the software vendors and hardware vendors that rely on specific hardware features and drivers for their products to work well.  Since their market is over 90% Windows and probably no more than 1% Linux, and given the costs of hardware and software development for both are about the same, which market do you think they're going to actively support?

Even companies like AMD, that have a strong history of actively supporting Linux have fallen off recently.  As an illustration: I can use hardware accelerated drivers on my AMD 4290 not only in Win7, but also in Win 8 -- as AMD recently resurrected their driver support for this chip; but in Linux, I am relegated to the open-source drivers because AMD dropped Linux driver support for this chip last summer.

Yeah, Windows is such a big company with so many users that i suppose it would have to be their primary customer base.
Im still having issues dowloading the game by the way, still cant get it to work.Im actually pretty dissapointed, But i suppose linux will just have to be a better "security based" OS, and windows better "in general" if that makes any sense. 
Dont get me wrong , I love linux, Just started using it, however it obviously has its flaws, But it also has it's good points, which in my opinion are the security aspects and the fact that it is open source and easy to upgrade, (however lets say for arguments sake windows was "better", that would be why you pay for it) But apart from that, i have not seen any major bonuses to using linux. 

If anyone can actually help me with downloading the game i would appreciate it, I still just get my hea around it.

---

### Post by WaterwineFear on 2013-06-28
So can anybody tell me how to install games to a linux OS,  apart from using Wine and crossover ? 
is there a way? I would hate to not be able to use some of my games i have here.. :) Thanks

---

### Post by Mark Phelps on 2013-06-28
> **WaterwineFear said:**
> So can anybody tell me how to install games to a linux OS,  apart from using Wine and crossover ? 
is there a way? I would hate to not be able to use some of my games i have here.. :) Thanks

There is also Play On Linux (which some folks refer to as POL) -- which can help with installation problems.

But, the simple fact of the matter is that Windows games are not written to run in Linux, so some intermediary software (in this case, WINE) MUST be used.

As I've said, Linux is not a free VERSION of Windows.

---

### Post by WaterwineFear on 2013-06-28
> **Mark Phelps said:**
> There is also Play On Linux (which some folks refer to as POL) -- which can help with installation problems.

But, the simple fact of the matter is that Windows games are not written to run in Linux, so some intermediary software (in this case, WINE) MUST be used.

As I've said, Linux is not a free VERSION of Windows.

Il look it up. Yes i have tried with wine it does not seem to help.
No, i realize linux is not a free version of windows, I had windows 8 on this pc and deleted it for ubuntu,Perhaps rather foolishly.
I was just asking if there was a way to install my games on linux as i could not seem to do it.

---

