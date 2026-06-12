---
title: "So what is the main advantage of 64-bit?"
date: 2007-02-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by AceRimmer on 2007-02-01
Just curious.  I was redoing my rig so I threw 6.10 x86-64 on there last night.  What advantages with this have over running the standard version?

---

### Post by glabouni on 2007-02-01
AFAIK you should experience a little performance boost that you may not even notice along with other advantages such as unavailable packages, non-working stuff and such.

> **When does the new 64-bit platform arrive?**

According to the table, the 64-bit hardware standard arrived in 2005, and the 64-bit operating system arrives in 2008. The high end selects the hardware, the low end selects the operating system. When the high end encounters the old platform's memory limit they create a market for a new hardware platform, and when the old platform falls off the low end the market migrates to a new standard software platform.

The new 64-bit hardware standard did indeed arrive in 2005, when high end users first demanded more than 4 gigabytes or RAM in sufficient numbers for x86-64 systems to show up at retail outlets like Fry's.[12] This hardware decision is already entrenched.

If the historical pattern repeats, three years after 64-bit hardware arrives, the market will adopt a new standard operating system. This places the obsolescence of the Win-32 API in 2008, because after 2008 even low-end systems will come standard with more than 4 gigabytes of memory, ruling out 32-bit processors with 32-bit operating systems for new purchases.[13] Users demand an operating system that can use all the memory in their machine, and when every machine has more memory than the old operating system can access, users move to a new standard OS that can cope with more memory.

**What will the new 64 bit operating system be?**

The three contenders are Windows-64, Linux, and MacOS X. The winner still could be any of them. Just as the hardware decision was uncertain in late 2003, the operating system remains is uncertain in late 2006.

As the new 64-bit systems hit the low end, the S-curve of 64-bit adoption will go close to vertical. This is the last chance to capture 50% market share, when the largest surge of new users decides upon a software platform to go with their new hardware. This doesn't mean a platform can wait until the last minute to get its act together, this is when the decision becomes irreversible. Network effects will already be strongly influencing adoption decisions when 64-bit "crosses the chasm" and acquires the high volume to be found at the low end. That will simply confirm the market's decision. It is already too late to introduce a new contender into the 64-bit race.

After the S-curve flattens out again, undecided new users will no longer be a significant influence on market share, and the largest platform will leverage its network effect advantage to consolidate the market. As 32-bit systems fall off the low end, the new 64-bit software platform will rapidly become entrenched.
[http://www.catb.org/~esr/writings/world-domination/world-domination-201.html](http://www.catb.org/~esr/writings/world-domination/world-domination-201.html)

---

### Post by Kilz on 2007-02-01
> **glabouni said:**
> AFAIK you should experience a little performance boost that you may not even notice along with other advantages such as unavailable packages, non-working stuff and such.


[http://www.catb.org/~esr/writings/world-domination/world-domination-201.html](http://www.catb.org/~esr/writings/world-domination/world-domination-201.html)

Do you even run a 64bit system and a 64bit OS? 

My advice to the original poster is to click on the names of people who reply to this topic and see where they post. If you dont see the 64bit forum, consider where the information is comming from.

> **AceRimmer said:**
> Just curious.  I was redoing my rig so I threw 6.10 x86-64 on there last night.  What advantages with this have over running the standard version?

Depending on what applications you are running you can see a 30% increese in performance. Things that do number crunching like encoding, ripping, multimedia editing, 3d graphices and rendering are common high number crunching applications. For most of the rest you will get a small boost. You will be able to address over 4 gigs of ram. 
But you may have to do some setup and follow a few howto's if you want to run proprietary  applications. Nothing to hard.

---

### Post by AceRimmer on 2007-02-01
> **Kilz said:**
> Do you even run a 64bit system and a 64bit OS? 

My advice to the original poster is to click on the names of people who reply to this topic and see where they post. If you dont see the 64bit forum, consider where the information is comming from.



Depending on what applications you are running you can see a 30% increese in performance. Things that do number crunching like encoding, ripping, multimedia editing, 3d graphices and rendering are common high number crunching applications. For most of the rest you will get a small boost. You will be able to address over 4 gigs of ram. 
But you may have to do some setup and follow a few howto's if you want to run proprietary  applications. Nothing to hard.


So would I see an increase when running a 32-bit Windows app in Wine if it is ripping a DVD ala DVDShrink?

---

### Post by kuja on 2007-02-01
No. 32-bit apps won't see any improvement. In that respect, have you tried other things like K3b (1.0 preview 1 or later), dvd::rip, etc? You really would see a marked improvement doing things like encoding, afterall.

---

### Post by Evil@heart on 2007-02-01
So I am running a 64 bit setup.  I couldn't run Window Xp x64 because their is not really much option on antivirus, support, or a good deal of plugins.  Now, in making the switch I find much of the same is true.  I can't help but feel like a large enough number of people run 64 bit systems that their is a wave of 64 bit support on it's way.  Anybody got an idea of when? In particular Shockwave and the such?

---

### Post by Kilz on 2007-02-01
> **AceRimmer said:**
> So would I see an increase when running a 32-bit Windows app in Wine if it is ripping a DVD ala DVDShrink?

You might want to try k9copy, its basically a linux version of DVDShrink. The GUI is close. Its a 64bit application and will have speed improvements. I will tell you that DVDShrink was the last thing I was running under wine until I found k9copy. You are better off using native applications than windows apps under wine. You always lose some performance running things under wine.

---

### Post by feld on 2007-02-01
> **Kilz said:**
> You might want to try k9copy, its basically a linux version of DVDShrink. The GUI is close. Its a 64bit application and will have speed improvements. I will tell you that DVDShrink was the last thing I was running under wine until I found k9copy. You are better off using native applications than windows apps under wine. You always lose some performance running things under wine.

Really? I beg to differ. In many ways Wine is faster than Windows.

[http://wiki.winehq.org/BenchMark-0.9.5](http://wiki.winehq.org/BenchMark-0.9.5)

Remember, Wine Is Not an Emulator

Running things natively in Linux is more preferable though.

---

### Post by Kilz on 2007-02-01
> **feld said:**
> Really? I beg to differ. In many ways Wine is faster than Windows.

[http://wiki.winehq.org/BenchMark-0.9.5](http://wiki.winehq.org/BenchMark-0.9.5)

Remember, Wine Is Not an Emulator

Running things natively in Linux is more preferable though.

But Im not basing the loss of performance based on what wine can do vs windows. Im basing it on what 32bit wine can do vs native linux applications.

---

### Post by hizaguchi on 2007-02-02
> **Evil@heart said:**
> So I am running a 64 bit setup.  I couldn't run Window Xp x64 because their is not really much option on antivirus, support, or a good deal of plugins.  Now, in making the switch I find much of the same is true.  I can't help but feel like a large enough number of people run 64 bit systems that their is a wave of 64 bit support on it's way.  Anybody got an idea of when? In particular Shockwave and the such?
I wouldn't get my hopes up on it happening anytime soon. :)  Until a couple months ago we couldn't even get an updated Flash for 32 bit Linux.  There's a really great how-to linked from one of the stickies at the top of this section that will help you install a 32 bit Firefox and plugins though, and (in KDE at least) it even puts in an option in the right-click context menu that lets you open the current website in Firefox32.  I thought having to use a 2nd browser for Flash-based pages would be a pain, but after using it for a while I actually prefer it this way because I can view the content I want easily but I don't have tons of flashing banner ads and huge Flash content loading on news sites and stuff.

Back to the original question, I think the main advantage is for processor-heavy applications.  I don't notice a huge difference unless I'm ripping a CD or solving a Sudoku puzzle with Octave.  Outside those situations where it does make a noticeable difference though, there is always the benefit of knowing that you're getting the most you possibly can out of your hardware.  If you don't care about that kind of thing, and if you don't run the kinds of programs that really benefit from the 64 bit OS, then you'd might as well go with the standard 32 bit Ubuntu.  But really, for me, 64 bit hasn't been much of a hassle at all and I'd probably run it anyway just because I can. :)

---

### Post by AceRimmer on 2007-02-02
Is 64 bit Feisty supposed to have any level increased support or are we stuck waiting on others to provide the proper software in 64 bit?

---

### Post by ghandi69_ on 2007-02-02
I would say the main advantage of 64 bit is that your processor is able to compute 64 bits of data per clock cycle as opposed to 32 bits per clock cycle.  It also theoretically allows your system to support and use up to 6,000,000 GB of RAM. :D

---

### Post by koshcu on 2007-02-02
The major advantage of 64bit to me is that I can use all 8G of the ram in my box. I do database devel work and since going to this new box my work has gotten vastly faster. Many things that took 20 mins or so to do on my athlon xp 3200 with 2G of ram now take a few seconds on my dual Opteron 2218s with 8G of ram. 

For many people 64bit does not offer much to them. However, if you actually need large amounts of memory, 64bit pays off in a huge way. Kind of how multiple cpu cores also gives a huge benefit to certain work loads. If you don't load your system down very much then multiple cpus won't help you very much. However if you tend to have multiple cpu bound processes running at the same time then many cores has a great impact.

---

### Post by Ocxic on 2007-02-02
I'll say this, I upgraded from a P$ 3GHz w/HT to a dual caor 64bit AMD 3800 2GHz and as it stands my AMD runs at 1GHz normaly, and it's just as fast as my P4, even more so when it runns at full speed.

---

### Post by Kilz on 2007-02-02
> **AceRimmer said:**
> Is 64 bit Feisty supposed to have any level increased support or are we stuck waiting on others to provide the proper software in 64 bit?

Dont hold your breath waiting on the Ubuntu developers to make Ubuntu 64bit "just work".  It also isnt as bad as you are making it out to be. There is only a 1% difference in avilable packages between the 32 and 64 bit versions.

---

### Post by JAPrufrock on 2007-02-02
As far as I can see, the main advantage is that it just plain seems like the right thing to do.  I installed 64bit Dapper on an AMD, and installed everything I need, including, flash, mplayer, java, etc.  On another AMD I started to install 64bit Edgy, but had some conflicts with mplayer and mplayer plugin, so I switched to 386i Edgy.  

I must admit that I can't really tell if there's a speed difference between the two.  But here's the thing- I just "feel better" when I'm using 64 bit software on a 64 bit machine.  Go figure...

---

### Post by Shay Stephens on 2007-02-03
No no no.  You all have it wrong.  The main advantage to 64bit is being able to complain that there are no programs or hardware to take advantage of the awesome power of 64bits.

64 bits is the pot of gold at the end of the rainbow, something to eternally strive for, but never reach it's delicious gooey center...hahahaha

---

### Post by Kilz on 2007-02-03
> **JAPrufrock said:**
> As far as I can see, the main advantage is that it just plain seems like the right thing to do.  I installed 64bit Dapper on an AMD, and installed everything I need, including, flash, mplayer, java, etc.  On another AMD I started to install 64bit Edgy, but had some conflicts with mplayer and mplayer plugin, so I switched to 386i Edgy.  

I must admit that I can't really tell if there's a speed difference between the two.  But here's the thing- I just "feel better" when I'm using 64 bit software on a 64 bit machine.  Go figure...

Why on earth you did that when Dapper is still available and is a long life release is beyond me. I think its just something that comes with experience. Sometimes the newest version of a linux distribution isnt the best choice. Im starting to feel good about staying with Dapper. Its very stable now and there are still 2 years of patches/upgrades left in its life.
Its kind of like when a new windows is released, the smart people wait for the first service pack before installing it. By then all the little bugs get fixed.

> **Shay Stephens said:**
> No no no.  You all have it wrong.  The main advantage to 64bit is being able to complain that there are no programs or hardware to take advantage of the awesome power of 64bits.

64 bits is the pot of gold at the end of the rainbow, something to eternally strive for, but never reach it's delicious gooey center...hahahaha
lol, that or to be able to complain "64bits isnt ready, I installed the 32bit version". To me thats like buying a 8 cylinder car and pulling out 4 of the spark plug wires.

---

### Post by maxamillion on 2007-02-03
I run 64-bit simply out of personal pride ... I can't seem to bring myself to own a 64-bit processor and run a 32-bit OS. For the basic desktop use, does it matter? ... no, not really. I think 64-bit in its current state is best geared for servers and high performance workstations, but then again I remember the days of Gnome 1.x so, even in its current state, 64-bit is incredible when put in perspective.

---

### Post by BIGtrouble77 on 2007-02-03
I'm actually still running 64bit Dapper on my main machine.  The only thing I could not get installed was AIGXL- which is something I just wanted to play with, not permanently use.  I'd also would have liked to have the more recent versions of gnome, but as it stands things are working amazingly well. 

Getting a 64bit ubuntu build working is not hard at all.  You just have to realize that some apps run better in 32bit and there's about a million howto's explaining how to do that.   I've been running problem free with the same install I configured 2 months before Dapper was released.  I install most stuff from the repos, manually installed a few .debs and built several packages for performance (like blender, conky, pan).  

These comments saying that 64bit isn't supported well yet are just entirely wrong.

---

### Post by JAPrufrock on 2007-02-03
> Why on earth you did that when Dapper is still available and is a long life release is beyond me. I think its just something that comes with experience. Sometimes the newest version of a linux distribution isnt the best choice. Im starting to feel good about staying with Dapper.

In hindsight I probably should have installed 64 bit Dapper in both boxes, since the first one worked so well, but I wanted to try out Edgy.

---

### Post by russell.h on 2007-02-12
I'm running 32bit Edgy, is there some way to upgrade to 64bit?

Would copying my home directory over to a new install migrate most of my settings and whatnot?

The nvidia driver still works on 64bit right? I have to confess to having a love affair with compiz....

---

### Post by kuja on 2007-02-12
> **russell.h said:**
> I'm running 32bit Edgy, is there some way to upgrade to 64bit? No.

> **russell.h said:**
> Would copying my home directory over to a new install migrate most of my settings and whatnot? Yes.

> **russell.h said:**
> The nvidia driver still works on 64bit right? I have to confess to having a love affair with compiz.... Yes.

---

### Post by ndefontenay on 2007-02-12
When I bought my new PC, I've been offered an amd64 or an intel. I wanted amd so I took it. 64 bit makes me feel special.

But I also had the feeling I've been screwed when I saw windows was running 32 bit...

Now with Linux I finally got the opportunity to use my hardware at best.

I'm not new at Linux but I'm not a genius. So far, installing all the missing applications on 32 bit (to get flash working with firefox32) has not been a problem.

I'm not missing any applications because it does not exist on 64 bit. They are all here.

Finally, I think that because I own a 64 bit processor, I have to support the momentum.

There is support when there are users. There are users when there is support. Usually support win and wait for users. It's up to us to make a difference.

---

### Post by FrozenFOXX on 2007-02-12
In the worst case you can always do things the Gentoo way:  SOURCE!  :lolflag: 


But seriously, I was thinking about dropping back to 32-bit Edgy just to make life a little easier and realized that in reality it only takes you a couple extra minutes of your time to fix something that may be "broken" in 64-bit.  Given the extra processing punch I say that's a Good Thing.  Will you notice?  Maybe, maybe not, but you'll know that when it CAN be increased you'll already be set (encoding movies, some games, graphic apps, and the fun of building things from source).

---

### Post by ndefontenay on 2007-02-12
Sadly, like all good things, we don't realize it when it's under our nose.

Those who are on 64bit Linux will notice the boost when they get back to 32!

Just like someone on 32bit Linux change for Vista. but this is not just obvious, it would be a counter cultural shock!

---

### Post by agamotto on 2007-02-13
GoogleEarth runs very snappy with 64-bit!

---

### Post by JAPrufrock on 2007-02-13
> **FrozenFOXX said:**
> In the worst case you can always do things the Gentoo way:  SOURCE!  :lolflag: 


But seriously, I was thinking about dropping back to 32-bit Edgy just to make life a little easier and realized that in reality it only takes you a couple extra minutes of your time to fix something that may be "broken" in 64-bit.  Given the extra processing punch I say that's a Good Thing.  Will you notice?  Maybe, maybe not, but you'll know that when it CAN be increased you'll already be set (encoding movies, some games, graphic apps, and the fun of building things from source).

Smart move!  I installed 32-bit edgy on one 64-bit box, and now I want to switch to 64-bit dapper.  Problem is I had set up a dual boot and now I will have to re-install both XP and Ubuntu.  Maybe someday, on a slow weekend....

---

### Post by capecove on 2007-06-05
IMHO, I love dedicating a hard drive to a single OS install. With the low cost of HDD's now a days, this is a pretty realistic setup for me.

---

### Post by jrocket on 2007-06-06
> **ndefontenay said:**
> When I bought my new PC, I've been offered an amd64 or an intel. I wanted amd so I took it. 64 bit makes me feel special.

But I also had the feeling I've been screwed when I saw windows was running 32 bit...

Now with Linux I finally got the opportunity to use my hardware at best.

I'm not new at Linux but I'm not a genius. So far, installing all the missing applications on 32 bit (to get flash working with firefox32) has not been a problem.

I'm not missing any applications because it does not exist on 64 bit. They are all here.

Finally, I think that because I own a 64 bit processor, I have to support the momentum.

There is support when there are users. There are users when there is support. Usually support win and wait for users. It's up to us to make a difference.

Yes.  Exactly what he said.  I also got a new pc and I wanted a 64bit dual core AMD.  I got it with 32 bit windows, which wasn't a huge deal since I bought it planning on removing windows and running linux as the only os.  I installed 64bit Feisty to see what all the Ubuntu fuss was about, and I love it.  I knew that since I had a 64bit cpu I wanted to take advantage of it, I really didn't care if I saw an increase in performance or not.  Using the ndis wrapper I have flash working in 64bit firefox, and I have experienced no problems by running 64bit instead of 32bit.  I honestly don't know why everyone's so scared to run 64bit instead of 32bit.  If you have a 64bit cpu, run a 64bit os.  Why let a perfectly good cpu go to waste?  I really don't see what's difficult about it.

Meh, anyways, perfectly satisified 64bit Feisty user here.

---

### Post by ©TriMoon® on 2007-06-06
I agree on the arguments about using your hardware to the extends its capable of.

There is in my case also another reason to run the 64-bit version:
The 32-bit version doesn´t even boot from the DVD, so im unable to install it !
It keeps restarting after a message about APIC/ACPI....

Yes ubuntu seems a nice distro sofar but still has its edges that need work...

---

### Post by fakie_flip on 2007-06-06
Is it possible to get decreased performance in most apps with the 64 bit version?

---

### Post by ©TriMoon® on 2007-06-06
> **fakie_flip said:**
> Is it possible to get decreased performance in most apps with the 64 bit version?

Its always possible to get decreased performance, depending on system-load, independent of bit class...
But its not logical that a 64bit cpu would be slower as a 32bit with same MHZ...

---

### Post by russell.h on 2007-06-06
I think it would be *possible* to get decreased performance, but only if there were something very wrong with the compiler, or if the program was written separately in assembly for both 32 and 64 bit. Needless to say nearly all programs are compiled with gcc (even if it is a scripting language the interpreter is probably written in C or C++) which doesn't suffer from that problem, so I would say that realistically you should never see a performance hit in an individual program from using a 64 bit version.

One example of where you *might* (and I'm not really sure) see an issue would be in some proprietary driver which has a poorly written 64 bit version.

And at any rate, with normal programs (not sure about drivers, although I know its true of my printer driver) you can install and run a 32 bit program on your 64 bit OS, so its really not an issue.

---

### Post by fakie_flip on 2007-06-06
Does the 64 bit version of an os such as vista or linux need more memory than the 32 bit version to run good?

---

### Post by kuja on 2007-06-06
> **fakie_flip said:**
> Does the 64 bit version of an os such as vista or linux need more memory than the 32 bit version to run good?

With regards to "decreased performance", in a way yes. The 64-bit version takes significantly more memory to run. Then again, this isn't much of a problem as the 64-bit version supports significantly more memory :popcorn:

---

### Post by fakie_flip on 2007-06-06
> **kuja said:**
> With regards to "decreased performance", in a way yes. The 64-bit version takes significantly more memory to run. Then again, this isn't much of a problem as the 64-bit version supports significantly more memory :popcorn:

How much more memory does it take? Maybe I am better off using the 32 bit version of Ubuntu.

---

### Post by notquitemichael on 2007-06-06
i've tried both the 64 and the 32 bit version of ubuntu and i'm running the 32bit now by
choice. this is because i just want an easy to setup / alter desktop jobby and the
performance of my machine is good enough for me not to want to be knee deep in
tutorials.
that said 64bit is well supported on ubuntu with flash and java all sorted :D and there
is a lot of forumn support should you decide to venture into the world of 64bit.

---

### Post by kuja on 2007-06-06
> **fakie_flip said:**
> How much more memory does it take? Maybe I am better off using the 32 bit version of Ubuntu.
I'd guess around twice as much? Hypothetical average person would be good on about 1 gig, People like me might need more like 2 gig.

---

### Post by fakie_flip on 2007-06-06
> **notquitemichael said:**
> there
is a lot of forumn support should you decide to venture into the world of 64bit.

I'm using 64 bit and I've got just about everything working. I ran into a few problems but 99% of them are solved.

---

### Post by scourge on 2007-06-07
> **kuja said:**
> I'd guess around twice as much? Hypothetical average person would be good on about 1 gig, People like me might need more like 2 gig.

I didn't notice anything like that when I switched from 32-bit. I can have a lot of applications running at the same time, and the RAM usage is still under 500MB. I'd say 1GB is more than enough for 64-bit Ubuntu.

What do you base the "twice as much" guess on? At least in most applications which are written in C, integers are still 32 bits in size, characters are 8 bits, etc. Some things like pointers do take twice as much space, but overall the difference in memory consumption shouldn't be that huge.

---

### Post by kuja on 2007-06-07
Maybe it's just me then, though I could never get myself under about 250mb of ram in use in 64-bit. I presentlyl average in the high 600's in use, easily pushing it well over a gig, but then again, maybe it's just me.

---

### Post by ©TriMoon® on 2007-06-15
> **scourge said:**
> I didn't notice anything like that when I switched from 32-bit. I can have a lot of applications running at the same time, and the RAM usage is still under 500MB. I'd say 1GB is more than enough for 64-bit Ubuntu.

What do you base the "twice as much" guess on? At least in most applications which are written in C, integers are still 32 bits in size, characters are 8 bits, etc. Some things like pointers do take twice as much space, but overall the difference in memory consumption shouldn't be that huge.

perhaps he made a link between memory usage and bit-width? :D
Anyway logicaly speaking it should be the otherway around. Less memory needs for 64bit vs 32bit because of the dbl-width commands available to 64bit cpus (reduction in code size in some cases)....

---

### Post by scourge on 2007-06-15
> **©TriMoon® said:**
> perhaps he made a link between memory usage and bit-width? :D

Well, as I said some things (like pointers) that used to take 32 bits (4 bytes) of RAM take 64 bits (8 bytes) in a fully 64-bit environment. So there is a link, it's just not that significant in most cases.

> Anyway logicaly speaking it should be the otherway around. Less memory needs for 64bit vs 32bit because of the dbl-width commands available to 64bit cpus (reduction in code size in some cases)....

Surely you mean executable (binary) size, not code size? It's true that 64-bit CPUs can perform some tasks with one instruction that previously required two or more instructions. But that shouldn't affect memory consumption.

---

### Post by Ocxic on 2007-06-16
well either way, I've noticed that my computer now needs a swap partition, after switching to 64-bit, I have a gigabyte of ram, and that used to be plenty when i had 32-bit system.

---

### Post by Rui Pais on 2007-06-16
> **Ocxic said:**
> well either way, I've noticed that my computer now needs a swap partition, after switching to 64-bit, I have a gigabyte of ram, and that used to be plenty when i had 32-bit system.

```
$ uname -m
x86_64
```

and:
```
$ free -m
             total       used       free     shared    buffers     cached
Mem:          1004        973         30          0         42        469
-/+ buffers/cache:        461        542
Swap:         2219          0       2219
```
1G RAM,  2G Swap Used: 0 (running 2 users, one with gnome other with e17, using firefox and swiftweasel,  thunderbird, codeblocks and some heavy math apps, a lot of terminals and gnuplots terms... here)

:)

---

### Post by markp1989 on 2007-10-02
My desktop supports 64bit, would it be a good idea for me to switch?

will i see a performance increase?

i have my /home in a seperate partition, so i can keep all of my settings/programs right?

the desktop im talking about is mentioned in me sig

---

### Post by John.Michael.Kane on 2007-10-02
> **markp1989 said:**
> My desktop supports 64bit, would it be a good idea for me to switch?
> In the end you the user will have to make the choice of what is right for you,and your needs.

The above quote from thread below
[Please Read First Advantages and Disadvantages of 64bit. (Plus install Guides)]("http://ubuntuforums.org/showthread.php?t=368607")


> **markp1989 said:**
> will i see a performance increase?
Depends on.
1) The Task
2) The program eg: The way it's written.

> **markp1989 said:**
> i have my /home in a seperate partition, so i can keep all of my settings/programs right?
Most members in the section say that clean installing, and backing up files before doing so is the best route, As there is no clean upgrade path from 32bit to 64bit.

> **markp1989 said:**
> the desktop im talking about is mentioned in me sig
One note on your config. Please post the output of the command below, As this will you to find out if your processor has the Intel 64 support
```
 sudo lshw -C cpu
```

---

### Post by markp1989 on 2007-10-02
> **SD-Plissken said:**
> The above quote from thread below
[Please Read First Advantages and Disadvantages of 64bit. (Plus install Guides)]("http://ubuntuforums.org/showthread.php?t=368607")



Depends on.
1) The Task
2) The program eg: The way it's written.


Most members in the section say that clean installing, and backing up files before doing so is the best route, As there is no clean upgrade path from 32bit to 64bit.


One note on your config. Please post the output of the command below, As this will you to find out if your processor has the Intel 64 support
```
 sudo lshw -C cpu
```

i know that my cpu supports 64bit, the output form the command you gave me is below 

  *-cpu                   
       description: CPU
       product: Intel(R) Celeron(R) D CPU 3.20GHz
       vendor: Intel Corp.
       physical id: 4
       bus info: cpu@0
       version: Intel(R) Celeron(R) D CPU
       slot: Socket 775
       size: 3200MHz
       capacity: 4GHz
       width: 64 bits
       clock: 133MHz
       capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall nx x86-64 constant_tsc up pni monitor ds_cpl cid cx16 xtpr lahf_lm

---

### Post by John.Michael.Kane on 2007-10-02
Only reason I asked for you to post the output of that command is there are two version of the celeron D one with the Intel64, and the Execute Disable Bit, and those without. In your case it looks like your hardware is golden.

At any rate if you have other questions don't hesitate to ask.

---

### Post by markp1989 on 2007-10-02
> **SD-Plissken said:**
> Only reason I asked for you to post the output of that command is there are two version of the celeron D one with the Intel64, and the Execute Disable Bit, and those without. In your case it looks like your hardware is golden.

At any rate if you have other questions don't hesitate to ask.


ok thankyou for your help, i read that page, and im going to install 64bit feisty on my box, ill report back here with results

---

### Post by John.Michael.Kane on 2007-10-02
> **markp1989 said:**
> ok thankyou for your help, i read that page, and im going to install 64bit feisty on my box, ill report back here with results

One note I would install the 64bit version on a separate partition.At least until you are sure you want to run it as the main OS.

---

### Post by markp1989 on 2007-10-02
> **SD-Plissken said:**
> One note I would install the 64bit version on a separate partition.At least until you are sure you want to run it as the main OS.

does compiz fusion run on 64bit. because i love compiz fusion

---

### Post by John.Michael.Kane on 2007-10-02
> **markp1989 said:**
> does compiz fusion run on 64bit. because i love compiz fusion

Not sure if it works under feisty 64 there might be guides for feisty,however. Gutsy 64bit seems to have that option available.

---

### Post by gtrtx on 2007-10-03
> **markp1989 said:**
> does compiz fusion run on 64bit. because i love compiz fusion

I'm running Trevino's CF repo's under Feisty64 with no probs whatsoever.

---

### Post by Rui Pais on 2007-10-03
hi,
about the home partition. 
What i do is install 64bits version on a separate partition and then from a console (no user logged with GUI) or from a liveCD copied the 32 home partition (with **cp -a**) for the 64b installation home. 

This keep all my settings and documents (on both versions) and never had any problem (OpenOffice give a warning about profile, but just say yes and it goes away harmless). Of course i keep big files like photos from digicam, videos, etc on a separated partition to avoid space waste.

---

### Post by markp1989 on 2007-10-03
> **Rui Pais said:**
> hi,
about the home partition. 
What i do is install 64bits version on a separate partition and then from a console (no user logged with GUI) or from a liveCD copied the 32 home partition (with **cp -a**) for the 64b installation home. 

This keep all my settings and documents (on both versions) and never had any problem (OpenOffice give a warning about profile, but just say yes and it goes away harmless). Of course i keep big files like photos from digicam, videos, etc on a separated partition to avoid space waste.

I installed 64bit and it works fine, i couldnt get compiz fusion to work, so i installed beryl, i noticed an increase in speed with recordmydesktop, i have not tested any other cpu intensive programs yet.

---

### Post by MarkieB on 2007-10-05
2 questions:

1. Isn't it possible to just install the 'generic' [64-bit] kernel rather than reinstalling the whole OS?

2. In view of the freezes with the generic kernel, tell me as a core 2 duo man, is my computer working with both cores when I boot to the 386 kernel? So that, aside from no higher-precision calculations, my computer is working relatively fast as it multi-threads applications to both cores as/when they have free capacity? I ask, as it looked as though system monitor was showing just 1 cpu

---

### Post by Rui Pais on 2007-10-05
> **MarkieB said:**
> 2 questions:

1. Isn't it possible to just install the 'generic' [64-bit] kernel rather than reinstalling the whole OS?
never tried, but i think it will not work. It's not only a different kernel compilation, modules/drivers will all be compiled for 64b but would be called by 32 bits apps that couldn't understand them (the opposite may work, but no point in running 32bits kernels under a 64bits OS)
> 
2. In view of the freezes with the generic kernel, tell me as a core 2 duo man, is my computer working with both cores when I boot to the 386 kernel? So that, aside from no higher-precision calculations, my computer is working relatively fast as it multi-threads applications to both cores as/when they have free capacity? I ask, as it looked as though system monitor was showing just 1 cpu
it depends on SMP option enabled on your kernel or not.
If you are using Dapper, the 386 version don't have it, you need to install the -686 version of linux-image. If you are using Feisty, just go with the -generic one, it's a 686 compilation with SMP enabled.
You can confirm by running on a command line:
```
uname -a
```
somwhwre on output must appear a SMP.

---

### Post by r!ots on 2007-10-16
hey.
i recently bought an asus x51r laptop with an Intel Core Duo T2450 processor. i thought it is a 64-bit processor but when i did

 ```
sudo lshw -C cpu
```

i got the following output:

> 
  *-cpu                   
       description: CPU
       product: Intel(R) Core(TM) Duo CPU      T2450  @ 2.00GHz
       vendor: Intel Corp.
       physical id: 4
       bus info: cpu@0
       version: 6.14.12
       serial: 0000-06EC-0000-0000-0000-0000
       slot: Socket 478
       size: 800MHz
       capacity: 1995MHz
       width: 32 bits
       clock: 133MHz
       capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pni monitor est tm2 xtpr
       configuration: id=0
     *-logicalcpu:0
          description: Logical CPU
          physical id: 0.1
          width: 32 bits
          capabilities: logical
     *-logicalcpu:1
          description: Logical CPU
          physical id: 0.2
          width: 32 bits
          capabilities: logical


as it doesn't say anything about 64-bit i fear that i thought wrong and actually it's not.

at the moment i'm using feisty32bit but i wanted to change to gusty64bit once it's out but that's not possible with my cpu, is it?

---

### Post by rsambuca on 2007-10-16
The Core Duo chips like yours are 32bit.  The Core 2 Duos are 64bit.

---

### Post by barkej on 2007-10-17
> **Kilz said:**
> You might want to try k9copy, its basically a linux version of DVDShrink. The GUI is close. Its a 64bit application and will have speed improvements. I will tell you that DVDShrink was the last thing I was running under wine until I found k9copy. You are better off using native applications than windows apps under wine. You always lose some performance running things under wine.
I second k9copy.

---

### Post by rsambuca on 2007-10-17
> **barkej said:**
> I second k9copy.

Why in the world would you jump in on a thread and comment on a post that is over 8 months old?? :)

---

### Post by russell.h on 2007-10-17
It was only 9 hours old when he commented. The big time gap was a few posts back.

---

### Post by rsambuca on 2007-10-17
> **russell.h said:**
> It was only 9 hours old when he commented. The big time gap was a few posts back.

I'm not mad or anything, it's just that the post he quoted was from Feb 1, 2007!!!  That portion of the discussion had ended *months* ago.

---

### Post by russell.h on 2007-10-17
Lol, hmmm I see what you're saying.

---

### Post by flamarro on 2007-10-17
Hi there,
i made this
```
sudo lshw -C cpu
```
 and got this

```
  *-cpu:0                 
       description: CPU
       product: AMD Athlon(tm) 64 Processor 3700+
       vendor: Advanced Micro Devices [AMD]
       physical id: 1
       bus info: cpu@0
       version: AMD Athlon(tm) 64 Processor 3700+
       slot: Socket 939
       size: 2200MHz
       capacity: 3GHz
       width: 64 bits
       clock: 201MHz
       capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow up pni lahf_lm cpufreq
  *-cpu:1 DISABLED
       description: CPU
       vendor: Unknown
       physical id: 5
       bus info: cpu@1
       version: AMD Athlon(tm) 64 Processor 3700+
       slot: Socket 939
       size: 1005MHz
       capacity: 3GHz
       clock: 201MHz

```

I'm now running in 64bit mode, and following some guides as mencioned, the only troubles i had was with flash in firefox, but, as i said, nothing that some guides that has been posted here wont solve the problem. So far so good, i dont have a intense use of my PC, time to time i do, but, as said before, if i have a 64bit processor, better use it if i can.....
Do you think that my machine is a good one to keep with this OS? i ask it because of tomorrow...... I'm now running gutsy beta, but dont know yet if i will upgrade or start a fresh install, and if i do it, what do you think..... stay with 64 isnt it? :)

---

### Post by Kilz on 2007-10-17
> **flamarro said:**
> Hi there,
i made this
```
sudo lshw -C cpu
```
 and got this



I'm now running in 64bit mode, and following some guides as mencioned, the only troubles i had was with flash in firefox, but, as i said, nothing that some guides that has been posted here wont solve the problem. So far so good, i dont have a intense use of my PC, time to time i do, but, as said before, if i have a 64bit processor, better use it if i can.....
Do you think that my machine is a good one to keep with this OS? i ask it because of tomorrow...... I'm now running gutsy beta, but dont know yet if i will upgrade or start a fresh install, and if i do it, what do you think..... stay with 64 isnt it? :)

I think its time that we as 64bit owners stop asking if we should run a 64bit os, and instead ask why shouldnt we run a 64bit os.
The reason is because there will be issues regardless of what version you run. The 32bit os isnt perfect. You will still have to battle common things like wireless and video drivers. There is no silver bullet, no easy version to install. If anyone thinks the 32bit version is perfect, they better take a good look at all the other areas of the forums.
In the end you end up with a os that doesnt use the potential of the hardware if you install a 32bit os. Even if you only use that potential part of the time. When you rip a cd, backup a dvd, edit some video, or lots of other jobs you get some performance boost.

---

### Post by jrharvey on 2007-10-17
I run virtualbox on fiesty 64 bit and you would not believe how much faster it is to run both operating systems when ubuntu is 64 bit. On the same machine my 32 bit install was slow and almost unusable just to browse around in XP. Now I have ubuntu 64 and virtualbox runs my programs faster and better than a native install of windows.

---

### Post by DerekInGermany on 2007-10-18
Here is a great article on the advantages of 64bit

[http://www.bit-tech.net/bits/2007/10/16/64-bit_more_than_just_the_ram/1](http://www.bit-tech.net/bits/2007/10/16/64-bit_more_than_just_the_ram/1)

Derek

---

### Post by tomdkat on 2007-10-18
> **Kilz said:**
> I think its time that we as 64bit owners stop asking if we should run a 64bit os, and instead ask why shouldnt we run a 64bit os.
The reason is because there will be issues regardless of what version you run. The 32bit os isnt perfect. You will still have to battle common things like wireless and video drivers. There is no silver bullet, no easy version to install. If anyone thinks the 32bit version is perfect, they better take a good look at all the other areas of the forums.I agree, great post.  :)

Peace...

---

### Post by coskierken on 2007-12-05
First if all, Kilz Thank YOU!!  Your experience and words of wisdom have help.  I installed Ubuntu 64-bit a month ago on an Asus Core 2 Duo with Ati Mobility x1700 and only had a couple of problems.  I had the same problem on 32-bit which I recently decided to go back to for a test.  The machine seems to have more snap to it in 64-bit.  I do quite a bit of dvd ripping and encoding, so I will probably go back to 64 very soon.  The links you gave and instructions will help through the flash and JAVA problems.  I have to build the aticonfig to make the tv out work, though.  I sometimes use the machine to play back mp4s on the tv.   I wish ATI better supported their chipsets in Linux, as we all do, and maybe one day they will.  I keep a dual boot on for now as I quite have not got used to dvd rippers and mp4 encoders in Ubuntu.  I have been working with them and it is all part of the learning process.  I imagine very soon, I will not be using XP at all.  Thanks again!:lolflag:

---

### Post by factotum218 on 2008-02-09
Stumbled upon this thread after installing 7.10-x64 recently. Went the lazy route and installed all the studio packages as well.


From my experience so far everything is tip-top. I noticed a performance boost after swapping out a semron 3800+ to a dual-core 64 3800+ but I am guessing that is from the dual-core and not so much the 64-bitness of everything.

Before this installation I had 32-bit Debian on the same processor. Overall I dont really notice much boost outside of things like compiling like previous posts have stated.

Like what most everyone else has been saying. If you have a 64 run 64. And know that you can always go with 32-bit with no harm done (if your a nancy-boy).  Kidding of course, but yeah, everything seems to work well so far.

---

### Post by bluewhale on 2008-04-12
The best thing I can think of regarding 64 bit Ubuntu would be VMWare. Run multiple 32 or 64 bit OS's and tie each one to it's own core.  At least that's where I'm headed.  XP was just getting too slow, most apps not taking advantage of multiple cores.  

I'm still just a newbie to Ubuntu ( and VMWare as well ) but already I'm able to match the performance of a new XP instalattion, with very little tuning as basically I don't know much about tuning yet.  ](*,)

---

### Post by boyofford on 2008-04-13
I did a fresh install with 32bit gutsy this week(after making a mess of upgrade to hardy beta), 
started using 32 bit again for couple of days then thought might be perfect time to try 64bit(while i didn't have everything setup anyway), so installed 64bit studio 7.10,
Thumbs up! seems definitely noticed speed on clean install and no problems so far on installing stuff, just check forum for problems before going ahead, flash was simple following instructions on here.

I agree with what someone said above,, if you can use 64bit you should, otherwise its a waste! the more people use it the more problems will be solved and as ubuntu64bit becomes more and more stable it will convert more of the people currently having 32-bit ms os on 64bit computers. bought a 64bit computer from dell, no option for 64bit windows vista!

---

