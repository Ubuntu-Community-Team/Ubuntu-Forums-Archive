---
title: "64 Bit without much memory"
date: 2007-09-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by Tiekyl on 2007-09-03
I've been reading peoples oppinions about 32 bit vs 64 bit, and a lot of times I've seen that some things happen slower on 64 bit. I also get the impression that it really depends on how much memory you have. 

I only have 512 mb of memory, but a 64 bit processor. Is there any chance that I would actually *lose* performance in some areas? I read a couple places, i think, that there were some areas that 64 bit used more memory than 32. I've looked for this the best I can, but...does anyone else have any ideas on this?

---

### Post by Applegeek on 2007-09-03
People get really passionate around here when you ask this, but here's what I would _suggest_:

It is so easy to try both on your box, and see what works the best!!

With 512Mb memory, there is no necessity for a 64 bit OS.  However some people report performance gains.  I don't really see it on modest boxes like yours, but what do I know -  I have 34 boxes running Ubuntu and/or XP, some 32 bit, some 64 bit - but I'm not testing every hardware combination available - that would be imnpossible.  If you're just surfing the web and writing emails, 32 bit _should_ be all that is required.  If you want to run high-end video editing or 3d rendering (which you don't want to do with 512MB anyway) then 64 bits is what you need <along with as much memory as you can stuff on your Mobo>.

However, some people see that even on modest boxes, the 64 bit version works much better.

Just try it and see what is best for you.  If this is your _first_ time installing Ubuntu, then I would try the 32 bit version first, just to see what its like, and test your network connection.  Then go for the the 64 bit version once you're familiar with how things work.  But that's me.  Others will suggest you start with 64 bit OS.  Just test and see what is best for you.

Just a head's up if you are testing 64 bit:  If you're wanting to use Flash 9 in your browser, that will require the use of "nspluginwrapper" if you're using a 64 bit browser.  This is a bit buggy at the moment for some people, others are running OK.  Or you can install the 32-bit version of Firefox (runs fine on the 64 bit OS) and then have more stable plugins available.  It will take a bit more time to get the 64 bit system dialed in, but Kilz has some scripts here to make it very easy.

If one version doesn't work out, just install the version that works better for you.

---

### Post by rsambuca on 2007-09-03
While I am not as passionate about it as some, I still suggest jumping in with 64 bit.  Both the 32bit and 64bit versions have their issues.  Neither is perfect, so you may as well take advantage of your processing power.

---

### Post by Tiekyl on 2007-09-03
Okay, thanks guys. I'm downloading the updates for it now. I'll give it a try, I with the way people were talking about it, I couldn't tell if it'd even be worth the CD for my computer. Guess it wont hurt! Thanks! 

(34 boxes??? Wow.)

---

### Post by saru411 on 2007-09-03
if you have a 64 bit processor you should run 64 bit ubuntu. most of the people you run across that say 64 bit is buggy or hard to install havent tried installing 64 bit since pre-edgy. snice feisty fawn has been out i have not seen many issues in this forum about 64 bit not working, or that it runs slower(have never heard of this myself). you will have to do one extra step for installing flash, or you can always install the 32 bit firefox with all the 32 bit plugins you could want on your 64 bit ubunut. find out all about it here [http://ubuntuforums.org/showthread.php?t=202537&highlight=java+flash+firefox](http://ubuntuforums.org/showthread.php?t=202537&highlight=java+flash+firefox)

kilz is the flash/java guru around here. this is his thread and he has a great script that will install everything for you. its absolutely painless. almost every other issue you will run into will be in both 32 and 64 bit ubuntu. for instance wireless cards. you will find the same issue will be in both 32 and 64 bit since the cards used are exactly the same. they dont make different wireless cards for 64 bit processor, or video cards, or sound cards, ect....you get my point. with a little research you should get your install done much faster than most. if you want to use a script/process that you see in the forums and are unsure just post your specs and that you have concerns in that thread...or you could even private message the owner of the thread. anyway just ask with an open mind and you will get all the help you need here.

good luck

---

### Post by Mizzou_Engineer on 2007-09-09
> **Tiekyl said:**
> I've been reading peoples oppinions about 32 bit vs 64 bit, and a lot of times I've seen that some things happen slower on 64 bit. I also get the impression that it really depends on how much memory you have. 

I only have 512 mb of memory, but a 64 bit processor. Is there any chance that I would actually *lose* performance in some areas? I read a couple places, i think, that there were some areas that 64 bit used more memory than 32. I've looked for this the best I can, but...does anyone else have any ideas on this?

The 64-bit versions generally do use a little more memory than the 32-bit versions, but it's not all that much. 32-bit Ubuntu generally takes around 100-120 MB of RAM on my laptop while 64-bit is more like 150-180 MB. 512 MB RAM should be enough for a decent working environment, but I'd also suggest that you spend $30 and pick up another 512 MB of RAM. 1 GB is enough to do most things on 64-bit Ubuntu, with the exception of doing something really ugly like running VMware with a couple of VMs going or running Octave or R on a data set that needs more than 1 GB RAM.

---

### Post by Jouke74 on 2007-09-10
If I am running Xubuntu 64 bit (the lighter version of Ubuntu) I am using about 170 Mb of memory in general.

---

### Post by ubuntukerala1980 on 2007-09-10
try 64 feel the difference :guitar:

---

### Post by stmiller on 2007-09-10
> **Tiekyl said:**
>  Is there any chance that I would actually *lose* performance in some areas? I read a couple places, i think, that there were some areas that 64 bit used more memory than 32. I've looked for this the best I can, but...does anyone else have any ideas on this?

Yeah, it all depends entirely on how the software is written.

[ LAME]("http://lame.sourceforge.net/index.php"), which can compile under 64bit to make a 64bit binary encodes  **slower** than 32bit LAME in a 32bit operating system. This is because the code makes the use of nasm and other things which do not have a 64bit counterpart. But LAME 4 is already in the works which will be 64bit friendly...

and on the other end:

I get about 10FPS *faster* h.264 encodes with 64bit [HandBrake]("http://handbrake.m0k.org/") vs. HandBrake under a 32bit OS. So parts of HandBrake when compiled 64bit can obviously take advantage of 64bit.

---

