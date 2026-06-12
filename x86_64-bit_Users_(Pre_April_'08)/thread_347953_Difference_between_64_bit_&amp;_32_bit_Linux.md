---
title: "Difference between 64 bit &amp; 32 bit Linux?"
date: 2007-01-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by mjrwingnut on 2007-01-28
I have a HP Laptop with a AMD 64 bit CPU. I installed the 64 bit ubuntu but I noticed most of the plugins for firefox and other apps are 32 bit. 

My question is what is the advantage of a 64 bit os verses a 32 bit os.

Thanks for any advice.

---

### Post by kuja on 2007-01-28
Speed. Support for absurd amounts of memory.

---

### Post by compwiz18 on 2007-01-28
If you're new to Linux, you may want to start with 32bit until you get comfortable with the whole deal.  When you feel ready, give 64bit a whirl.

Or, if you're feeling adventurous, give it a shot now.  There are tutorials for most of the common stuff, like Firefox plugins (Flash,Java,etc)

Some of the obscure stuff can be tricky, however.

But the speed boost is nice.

---

### Post by Kilz on 2007-01-28
> **mjrwingnut said:**
> I have a HP Laptop with a AMD 64 bit CPU. I installed the 64 bit ubuntu but I noticed most of the plugins for firefox and other apps are 32 bit. 

My question is what is the advantage of a 64 bit os verses a 32 bit os.

Thanks for any advice.
Thats because the plugins are proprietary, like flash. The people who own the code have to make the 64bit version since the community doesn't have access to it. But the amount of 32bit applications needed is very small. Those that are needed will run just fine on the 64bit os. 

> **compwiz18 said:**
> If you're new to Linux, you may want to start with 32bit until you get comfortable with the whole deal.  When you feel ready, give 64bit a whirl.

Or, if you're feeling adventurous, give it a shot now.  There are tutorials for most of the common stuff, like Firefox plugins (Flash,Java,etc)

Some of the obscure stuff can be tricky, however.

But the speed boost is nice.

Why on earth would anyone advise someone to install a 32bit os on 64bit hardware is beyond me.

---

### Post by compwiz18 on 2007-01-28
> **Kilz said:**
> Why on earth would anyone advise someone to install a 32bit os on 64bit hardware is beyond me.

To be honest, I wouldn't have wanted to deal with all the flash/java problems on my first day with Ubuntu.  It is tricky enough with 32bit.  And if it wasn't for your flash/java/firefox32 setup script, I wouldn't be using 64bit right now.

---

### Post by ukrudl3r on 2007-01-28
> **Kilz said:**
> Why on earth would anyone advise someone to install a 32bit os on 64bit hardware is beyond me.

Hauppauge.

---

### Post by mjrwingnut on 2007-01-31
> **compwiz18 said:**
> To be honest, I wouldn't have wanted to deal with all the flash/java problems on my first day with Ubuntu.  It is tricky enough with 32bit.  And if it wasn't for your flash/java/firefox32 setup script, I wouldn't be using 64bit right now.
flash/java/firefox32 setup script????? Never heard of it. What is it??? AND how do I learn how to use it!

Thanks for any help!!!!

---

### Post by incubus on 2007-01-31
mjrwingnut,

Read Kilz's signature, it has the links to his comprehensive HowTos.  I believe Kuja has a program that does everything automagically.  I think it's called simple64 (EDIT: yes, and it's in his signature too).

incubus

---

### Post by RAOF on 2007-01-31
> **Kilz said:**
> ...
Why on earth would anyone advise someone to install a 32bit os on 64bit hardware is beyond me.

Because evil, proprietary stuff sometimes Just Works(tm) on 32bit, and never Just Works(tm) on 64bit.  Some people care.

Others add AMD64 wine-0.9.30 packages to their repositories :).

---

### Post by Kilz on 2007-01-31
> **RAOF said:**
> Because evil, proprietary stuff sometimes Just Works(tm) on 32bit, and never Just Works(tm) on 64bit.  Some people care.

Others add AMD64 wine-0.9.30 packages to their repositories :).

That is the truth, but the proprietary stuff is available. It just takes a little effort. So then its just a matter of some people being lazy ?

Nice to see wine is finely a 64bit package :D.

---

### Post by compwiz18 on 2007-01-31
> **Kilz said:**
> That is the truth, but the proprietary stuff is available. It just takes a little effort. So then its just a matter of some people being lazy ?

Nice to see wine is finely a 64bit package :D.
Exactly.

---

### Post by leona on 2007-01-31
Ok, this will probably get me into trouble but, I saw someone suggest they install 32bit then later install 64bit when they get used to Linux, I fully support that, I SO wish I had done that.

I'm finding there are just too many [problems / bugs]("http://www.ubuntuforums.org/showpost.php?p=2041756&postcount=116") with 64bit, so I wonder, is it possible to reinstall with 32bit? what would I need to do (without loosing data / personal settings etc), I have /home as a seperate partition, if that helps.  I'm sorry but untill there is 100% support for 64 bit I don't feel its viaable (for a novice user anyway).

---

### Post by Kilz on 2007-01-31
> **leona said:**
> Ok, this will probably get me into trouble but, I saw someone suggest they install 32bit then later install 64bit when they get used to Linux, I fully support that, I SO wish I had done that.

I'm finding there are just too many [problems / bugs]("http://www.ubuntuforums.org/showpost.php?p=2041756&postcount=116") with 64bit, so I wonder, is it possible to reinstall with 32bit? what would I need to do (without loosing data / personal settings etc), I have /home as a seperate partition, if that helps.  I'm sorry but untill there is 100% support for 64 bit I don't feel its viaable (for a novice user anyway).

Just a question, were you expecting a Linux install where you didnt have to do any setup? I looked at the list of problems you have. The only one that is 64bit, and could be avoided on 32bit is "I can't print from my 32 bit Firefox browser, thats really annoying.".

Mounting a network in fstab is a pain in 32bit also your first time
Expect to loose your wifi if you change the router with any linux version
VMware is always a pain, you can have setup problems regardles of version
java chat rooms are going to be a problem in 32bit because they use the exact same java-firefox setup that the firefox32 uses.
Dont expect setting up usb perfirals to be easy just because you change to 32bit

In short what you think may be a soultion/cause of the problem may not be. Expect to have to actualy do some setup regardles of what version of linux you install. Those that tell you that 32bit is a dream and you never have to do any setup are telling you _LIES_.

---

### Post by kuja on 2007-01-31
Leonoa, I feel like taking a crack at a few of the problems, maybe what I have to say might useful to you :)

With the smbfs mount, try first mounting, and then copying the resulting line from /etc/mtab into /etc/fstab. 
I don't know much about wireless, but I wonder how well it would work to drop the key, and lock yourself down with a good firewall? (Sitting here and thinking I can see the potential security problems (that is, chance of someone nearby intercepting the data), hum, probably not a good enough idea, then again, anything critical will likely only pass over an ssh or https protocol right?) Anyway, Kilz is right, Wirelss is just one big PITA, no matter what version of Linux you use. 
Rather than using VMWare Player, why not try VMWare Server, its better anyway, and still doesn't cost a penny. There's a good howto on setting it up in the ubuntu wiki.
Hmm, looks like you had actually resolved the Java problem - keep in mind that java is cross-platform and acts the same on the 32-bit arch. If you're not happy with Java 5 you can also try Java 6.
As for USB, it's odd that it's not detecting it, I hope it works for you in 32-bit if you go that route, but the odds really aren't all that likely.

If you're not willing to try any of these ideas, or they don't work for you:

It's good that you kept your /home partition, just don't format it or select it when you're installing at all. Select the same username you used before when doing the install. After the install, add a line like this to your /etc/fstab file: 
*/dev/<device> /home ext3 defaults 0 2 *
Where <device> is the device corresponding to your home partition.

---

### Post by leona on 2007-01-31
> **Kilz said:**
> Just a question, were you expecting a Linux install where you didnt have to do any setup? I looked at the list of problems you have. The only one that is 64bit, and could be avoided on 32bit is "I can't print from my 32 bit Firefox browser, thats really annoying.".
......
 Those that tell you that 32bit is a dream and you never have to do any setup are telling you _LIES_.

And anyone who says Linux can be installed/used by the average Windows user is also **lying** IMHO!

> **kuja said:**
> Leonoa, I feel like taking a crack at a few of the problems, maybe what I have to say might useful to you :) .....

Hi there, thanks both of you for your replies and not totally running me off the road :) .  Some good and valid points here.

My view when I wrote this that was they maybe the 64bit was maybe less well developed / tested, maybe it used API's that where not stable, where as the 32bit was likely to be more heavily tested and bug fixed, I didn't know if the fstab problem was a 64bit thing or a general Ubuntu thing (as exactly the same line works fine on a Suse machine).

Not being able to print from the 32 bit browser is a real bug bare, I know I could launch the 64 bit browser and do the stuff I need to then print it, then go back to my 32bit one for general surfing.  Maybe if it was possible to launch the 64 and 32bit browsers at the SAME time it resolve my problem.

I do realise I hae to do some config. Its not a problem, I mean you have to spend time setting up windows, just not to the level you have to with Linux, but again its ok, as long as there is a good how to and usually there is and I have to say Kilz you 64 bit scripts and howto's where a god send! 

I have the 32 bit version installed on my notebook and I don't seem to come across the same problems / bugs, yes I got the Java one, cos that's common to all flavors of Ubuntu, same with the wifi issue, so you are right there are bugs in both.

I'm not sure what the answer is, except going back to college / uni and study software / hardware engineering and write my own device drivers / applications :(

Thanks

---

### Post by RAOF on 2007-01-31
> **leona said:**
> And anyone who says Linux can be installed/used by the average Windows user is also **lying** IMHO!

...

On the other hand, **Windows** can't be installed by the average windows user :).

---

### Post by Kilz on 2007-01-31
> **RAOF said:**
> On the other hand, **Windows** can't be installed by the average windows user :).

Some people think they are when they use a restore disk. But in reality they are using a ghost image of a system set up by the computer manufacturer with all the problems, bugs, and drivers already worked out for them.
I remember trying to install Windows on a computer that didnt have a restore disk once. It was a total nightmare. Hunting down the hardware that was in it, then all the drivers. Lucky I had another functional computer to do it.

---

### Post by Titi on 2007-02-01
i didn't know there was such a big difference between 32bit and 64bit. the sticker on my computer says "AMD 64 Athlon" so i just installed the AMD64 version of ubuntu. i didn't even know it was faster or anything. 
also, i did not have any troubles so far i think. the flash plugin for firefox was no problem at all, just had to copy the right files to the right folder. i haven't installed the java plugin. maybe i should follow the howto :)

---

### Post by leona on 2007-02-01
> **RAOF said:**
> On the other hand, **Windows** can't be installed by the average windows user :).
haha, like it, ya that's true also, I've never used a 'restore' disk, always installed from CD.
> **Titi said:**
> i didn't know there was such a big difference between 32bit and 64bit. the sticker on my computer says "AMD 64 Athlon" so i just installed the AMD64 version of ubuntu. i didn't even know it was faster or anything. 
also, i did not have any troubles so far i think. the flash plugin for firefox was no problem at all, just had to copy the right files to the right folder. i haven't installed the java plugin. maybe i should follow the howto :)

And this will be where you'll run into problems, because Sun haven't produced a 64bit plugin, so no java in your 64bit browser, so then you'll have to install a 32bit browser, and this is where all the 'fun' starts!

---

### Post by hakan69 on 2007-02-01
Hi
leona writes:
*then you'll have to install a 32bit browser, and this is where all the 'fun' starts!*
I installed Swiftfox (32 bit) and plugins with Automatix, I had to add a path to the systempath, but after that it has worked without problems.
Regads/Hakan

---

### Post by Kilz on 2007-02-01
> **leona said:**
> And this will be where you'll run into problems, because Sun haven't produced a 64bit plugin, so no java in your 64bit browser, so then you'll have to install a 32bit browser, and this is where all the 'fun' starts!

Since he installed flash, and there is no 64bit flash. He either has a 32bit browser installed , or did the harder trick of getting the nspluginwrapper installed.

---

### Post by John Jason Jordan on 2007-02-02
> **Kilz said:**
> Since he installed flash, and there is no 64bit flash. He either has a 32bit browser installed , or did the harder trick of getting the nspluginwrapper installed.
I agree that getting Flash installed via nspluginwrapper can be a bit tricky. It took me a bit of fiddling and a lot of patience waiting for someone to tell me the next thing to try. I do now have Flash 9 working just fine in 64-bit Firefox 2.0. Kilz' howto's for using 32-bit Firefox instead are another alternative, but if you want to get it working in 64-bit Firefox, here's the thread:
[http://ubuntuforums.org/showthread.php?t=341727](http://ubuntuforums.org/showthread.php?t=341727)
Regarding Java, I have long had Java working just fine in 64-bit Firefox. It's been so long I don't even remember how I did it or where the instructions are.

---

### Post by ghandi69_ on 2007-02-02
> **Kilz said:**
> Some people think they are when they use a restore disk. But in reality they are using a ghost image of a system set up by the computer manufacturer with all the problems, bugs, and drivers already worked out for them.
I remember trying to install Windows on a computer that didnt have a restore disk once. It was a total nightmare. Hunting down the hardware that was in it, then all the drivers. Lucky I had another functional computer to do it.

I'm going to have to disagree with you here.  I've built my own computer for a while now and have been installing free version of XP Pro the university gives to the students (Vista just became available... free of charge, although I dont plan on using it thanks to ubuntu)

Anyway, I've installed a non restore disk for XP pro dozens of times without any of the problems you mentioned.

---

### Post by Kilz on 2007-02-02
> **ghandi69_ said:**
> I'm going to have to disagree with you here.  I've built my own computer for a while now and have been installing free version of XP Pro the university gives to the students (Vista just became available... free of charge, although I dont plan on using it thanks to ubuntu)

Anyway, I've installed a non restore disk for XP pro dozens of times without any of the problems you mentioned.

It all depends on what you install it on. I used a windows 2000 disk on an old compaq. It was a nightmare.

---

### Post by Lil_Eagle on 2007-02-03
Yeah, what I remember most about installing windoze was:

1)   Trying to read the tiny little letters and number on the sticker stuck on the back of the PC so I could then type the random 25 characters into the computer.  Otherwise it wouldn't install.

2)  Hunting for all of the driver and application CDs.  (Where did I put that damn disc?)

3)  Having to wait every time it booted to update the anti-virus and nagging me to upgrade to the pro version of the firewall.

What I worry about now?  How can I break the computer now so I can learn more about Linux.  Seems the only way I learn is for things to be broken and have to fix them.  Do I hear someone calling in the background "install feisty!"?

The problems with the 64-bit are nothing compared to the problems you have daily with windoze.  If you really want to compare the 32-bit to the 64-bit, the best way is to install them both!  Then do your own tests.  If you're like me, you'll find that the 32-bit version works better "out of the box" but still needs tweaking.  The 64-bit version needs more tweaking, but it "feels right".

---

### Post by #Reistlehr- on 2007-02-03
after a while, you get used to windows, cause i could find any drivers i need in under 10 minutes for 64-bit windows, and i cant get half my stuff installed on nix lol.. 

i never want to have ms on a home computer again, but it honestly makes everything so much easier... im just used to it i guess.

---

### Post by Kilz on 2007-02-03
> **#Reistlehr- said:**
> after a while, you get used to windows, cause i could find any drivers i need in under 10 minutes for 64-bit windows, and i cant get half my stuff installed on nix lol.. 

i never want to have ms on a home computer again, but it honestly makes everything so much easier... im just used to it i guess.

What you said is correct "**after a while, you get used to windows**". People sometimes forget that at one time they had problems with Windows and everything was hard. Then over time they learned how to do things and where to find the things they needed.
When switching to Ubuntu or any other Linux distro, it takes time. You have to learn a lot, just like you did with Windows. I dont remember exactly how long it took to get everything setup on my first install. It must have took a week or so. But now after almost a year I know a lot more. I setup my brothers comp in 2 hours.

---

### Post by #Reistlehr- on 2007-02-03
> **Kilz said:**
> What you said is correct "**after a while, you get used to windows**". People sometimes forget that at one time they had problems with Windows and everything was hard. Then over time they learned how to do things and where to find the things they needed.
When switching to Ubuntu or any other Linux distro, it takes time. You have to learn a lot, just like you did with Windows. I dont remember exactly how long it took to get everything setup on my first install. It must have took a week or so. But now after almost a year I know a lot more. I setup my brothers comp in 2 hours.

i consider myself an average user, tis being my third day using linux. i guess i cause problems on purpose, just so i can learn. i did the same thing with windows. 

like yesturday, beryl+aiglx+nvidia were set up, but i couldnt remember how, so i put the image back on, so i could go back and figure it out (although i kind of regret it now lol :) )

---

### Post by rsambuca on 2007-02-03
I have both installed on my system, and frankly, I don't know where this "speed boost" people are talking about is.  Realistically, unless you are doing some heavy video transcoding or large image manipulation, you won't notice much of a difference other than  a few milliseconds here, maybe a few seconds there.  Not a big deal for most users.

---

### Post by nesf on 2007-02-03
> **#Reistlehr- said:**
> i guess i cause problems on purpose, just so i can learn. i did the same thing with windows.

That's the best way to get to grips with any OS imho. :)

---

### Post by Kilz on 2007-02-03
> **rsambuca said:**
> I have both installed on my system, and frankly, I don't know where this "speed boost" people are talking about is.  Realistically, unless you are doing some heavy video transcoding or large image manipulation, you won't notice much of a difference other than  a few milliseconds here, maybe a few seconds there.  Not a big deal for most users.


There are benchmarks that show it depends on what applications you use. In my case I like 3d design, I can cut a few hours off of a complex rendering using 64bit.

---

### Post by rsambuca on 2007-02-03
Are you sure that is the correct link?  I have seen it before, but it is comparing Intel to AMD, isn't it?

Edit:  I see you have removed the link now.  In any event, you just back-up what I said.  Unless you are doing heavy duty stuff, you won't notice a difference.  3d rendering is some of the most cpu intensive stuff you can do.  Yes, definitely in your case you should use 64 bit OS and apps.

---

### Post by Kilz on 2007-02-03
> **rsambuca said:**
> Are you sure that is the correct link?  I have seen it before, but it is comparing Intel to AMD, isn't it?

Edit:  I see you have removed the link now.  In any event, you just back-up what I said.  Unless you are doing heavy duty stuff, you won't notice a difference.  3d rendering is some of the most cpu intensive stuff you can do.  Yes, definitely in your case you should use 64 bit OS and apps.

Yes I removed it when I realized it wasn't the link I thought it was.
I find encoding is another thing that 64bit is good for, and lots of people rip cd's.

---

### Post by compwiz18 on 2007-02-03
And compiling: the kernel takes 45 minutes on my 1.8ghz 64bit, while 1.5hours on 32bit on the same computer.

---

### Post by Rui Pais on 2007-02-04
> **compwiz18 said:**
> And compiling: the kernel takes 45 minutes on my 1.8ghz 64bit, while 1.5hours on 32bit on the same computer.

45mn/1,5h compile a kernel? Hardware isn't all for speed burst ;)

if you really want speed compiling kernels try to remove modules you don't need (the ones for hardware that you don't have) and check carefully the options that you really need (like kernel debugging or security options that you may not be using at all)

My kernel compile time are 7-8mn, on 64b 7-12mn on 32b, depending on small variations on configuration. 
Definitely better then any versions vs another :lol:



Edit: 
btw, another one here that don't see much speed burst. Using both versions of edgy, now.
Some cpu intensive apps runs faster, but some 32bites apps, like firefox32, takes longer to start and don't seems to be so responsiveness... but both, faster and slower, are just very small effects. On a blind test i'm sure i couldn't say which one was the 64bits.

---

### Post by compwiz18 on 2007-02-04
Yeah - I could compile the kernel that small, but I don't want to plug some random hardware in sometime and not have it work because the kernel wasn't compiled with support for it.  Now that you mention it though, I have a .config from a compile I did for LFS that has only minimal support...maybe I'll hunt it down and try it for a speed boost.

---

### Post by Rui Pais on 2007-02-04
> **compwiz18 said:**
> Yeah - I could compile the kernel that small, but I don't want to plug some random hardware in sometime and not have it work because the kernel wasn't compiled with support for it.  Now that you mention it though, I have a .config from a compile I did for LFS that has only minimal support...maybe I'll hunt it down and try it for a speed boost.

well mine are really slim yes, but i just give my times for a comparison between my 32b and 64... not tring to convince you to go for such a light thing (i keep a default ubuntu kernel for the cases where i need to plug some new hardware, anyway), but just to check some stuff that you proabily wont use and keep compiling for nothing. 

Examples: Ubuntu defaults for a lot of kernel debugging code. Once you compile a kernel and it's running fine you can recompile without such stuff (most of those things are for developers not for users anyway). 
Are you sure you could get your hands on some really high speed network? or digital video processing, scientific instrumentation? i remove those things cause for myself i don't need it. I remove too all modules for bizarre filesystems, amiga, macs one, unixs, plan9, cause i'll won't need them for sure. I don't use SELinux why compile it?... 

Anyway even in the remote case that i need something of that i can recompile then or use the default kernel? why do it all the time? ;)

---

### Post by compwiz18 on 2007-02-04
I compile my own for ndiswrapper support (ndiswrapper doesn't work on 64bit on default install of Edgy for some reason) and I've remove debugging support, etc.  I think it is a bit faster without that.

---

