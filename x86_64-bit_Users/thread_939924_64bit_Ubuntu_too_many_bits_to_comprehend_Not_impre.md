---
title: "64bit Ubuntu: too many bits to comprehend? Not impressed"
date: 2008-10-06
forum: x86 64-bit Users
---

### Post by CC_machine on 2008-10-06
Dell Inspiron 6400
Wireless: Intel 3945 - Linux compatible
Graphics: Intel 950 - Linux compatible

everything should work great. i spent extra on this system to make sure it'd all work well out the box.

I just installed ubuntu 64 bit. well, tried to. Ran compiz for a while but every minute or so it'd lock up for 10 seconds at a time - only running Firefox (no flash obviously, only 3-4 tabs) and Pidgin (for MSN, yes, i know, it sucks, but im 16 and need internet messaging). So i enabled metacity again to be on the safe side... Locked up just now. while i was typing a message to a friend, it locked up. Completely frozen. capslock or numlock don't work and i cant ctrl+alt+f1,f2 etc to get to a terminal. nothing. it's been "installing" for an hour now (frozen for ~20 minutes). Ubuntu normally installs in 10-20 minutes!! what the hell?

i need my work done TODAY. this ain't good, my other installations are all broken by my own fault mind you, but this 64bit issue is a massive issue. Typing this from my buddies' 64bit Windows Vista laptop (hey, it WORKS!)

---

### Post by soxs on 2008-10-06
Did you check the md5 sum of your cd image (check cd integrity when inserting disc, this option will check the disc)?
Did you try to use the laternate installer?
Did you allready ran a memtest?
What version of ubuntu do you use?

Edit: Where did you get the statements from being linux compatible? (i didn't look up myself, but I am just curious :-P )

---

### Post by peakshysteria on 2008-10-06
Sounds like a bad disc yes. You shouldn't have any trouble like this with your install. Try to turn off compiz to see if things are better without. Get [Compiz switch]("http://forlong.blogage.de/entries/pages/Compiz-Switch") for easy on/off'ing of Compiz.

---

### Post by saru411 on 2008-10-06
I'm a little confused about the current state of your computer. Obviously an integrated graphics card like the Intel you chose will not run Compiz well,if even at all. Next, I'm confused about what a 64bit O/S has to do with your problems. You haven't even tried installing a 32bit O/S to compare your issues(at least it wasn't mentioned in your post). When you say your install is frozen, What are you talking about? Are you reinstalling? Why are you asking for help with an installation that is currently being written over by your current install?

Please calm down, figure out where you are in the installation and then post a thread asking SPECIFIC questions so that we can HELP you. You also shouldn't be putting out False Alarms by doing 10 different things to "fix" something. If you break something you should undo what you did to break it. Trying something else on top of something else just causes more problems by making it difficult to troubleshoot your system.

---

### Post by soxs on 2008-10-06
> **saru411 said:**
> I'm a little confused about the current state of your computer. Obviously an integrated graphics card like the Intel you chose will not run Compiz well,if even at all. Next, I'm confused about what a 64bit O/S has to do with your problems. You haven't even tried installing a 32bit O/S to compare your issues(at least it wasn't mentioned in your post). When you say your install is frozen, What are you talking about? Are you reinstalling? Why are you asking for help with an installation that is currently being written over by your current install?

Please calm down, figure out where you are in the installation and then post a thread asking SPECIFIC questions so that we can HELP you. You also shouldn't be putting out False Alarms by doing 10 different things to "fix" something. If you break something you should undo what you did to break it. Trying something else on top of something else just causes more problems by making it difficult to troubleshoot your system.

I doubt this has *ANYTHING* to do with 64 bit, but usually people who switch, will always think that it could be architecture related... which is rarely to never the case (exceptions: flashplayer-nonfree, realplayer)

---

### Post by jespdj on 2008-10-07
There are more people with Dell laptops complaining that WiFi doesn't work with their Intel 3945 card. Look in the [Dell Ubuntu Support forum](http://ubuntuforums.org/forumdisplay.php?f=342). (My Intel 4965 WiFi card has never given me any problems).

What makes you think your problems have anything to do with the 64-bit version of Ubuntu?

---

### Post by Thelasko on 2008-10-07
I have an Intel 965 graphics card and I can run minimal Compiz fine.  I haven't tried the spinning cube since Feisty, but the Intel cards are capable.  The old drivers were not capable of video playback and Compiz simultaneously but they have come a long way.

I don't think the Intel card is a problem.  Just make sure your driver is "intel" and not "i810" or "i915", those are obsolete.

---

### Post by saru411 on 2008-10-09
> **soxs said:**
> I doubt this has *ANYTHING* to do with 64 bit, but usually people who switch, will always think that it could be architecture related... which is rarely to never the case (exceptions: flashplayer-nonfree, realplayer)

Notice that I said,
> I'm confused about what a 64bit O/S has to do with your problems

Now also notice I said, 
> You haven't even tried installing a 32bit O/S to compare your issues

Compare is the key term, meaning you compare one verse the other for compatibility. I HIGHLY DOUBT his issue is 64bit related but we will never know. He decided to make a rant instead of troubleshooting his installation.

---

### Post by soxs on 2008-10-09
> **saru411 said:**
> He decided to make a rant instead of troubleshooting his installation.

Purging your system and performing a clean install is faster than troubleshooting a unknown problem, especially if you set up a seperate home partition and a shellscript, which will install all packages you had installed before ;-)
If it was my primary machine, I would do the same...

---

### Post by saru411 on 2008-10-09
> **soxs said:**
> Purging your system and performing a clean install is faster than troubleshooting a unknown problem, especially if you set up a seperate home partition and a shellscript, which will install all packages you had installed before ;-)
If it was my primary machine, I would do the same...

I agree with you 100% but most inexperienced users 1.) didn't install using a separate home partition(I highly recommend doing this) and/or 2.) don't know how to make a shell script(which I doubt most of us even know all of the programs we have installed on our systems). Since the poster of this thread has yet to return our ranting back and forth fixes nothing. Therefor, I would like to stop this silliness and move on. Take care and best of wishes

---

