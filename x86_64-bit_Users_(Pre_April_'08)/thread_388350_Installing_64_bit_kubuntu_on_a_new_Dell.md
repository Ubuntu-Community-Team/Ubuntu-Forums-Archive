---
title: "Installing 64 bit kubuntu on a new Dell"
date: 2007-03-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by matt_feliks on 2007-03-19
Hi everyone,

I've ordered a Dell Inspiron 6400 and am planning to install kubuntu. As I understand it, the Intel Core 2 Duo processor is 64-bit which means I've the option of installing 64-bit kubuntu or the 32 bit version.

I am new to linux but willing to put in a bit of time to get things running smoothly. After looking through the forums the opinion seems mixed as to whether this is wise for a new user.

Here's a more detailed spec. If you have any other general comments about compatability etc (eg. with nVidia) then please tell me.

Intel® Core™ 2 Duo Processor T5600 (1.83 GHz, 2 MB L2 cache, 667 MHz FSB)
1024MB 667MHz Dual Channel DDR2 SDRAM
160GB (5,400 rpm) Sata Hard Drive
256MB NVIDIA® GeForce™ Go 7300 TurboCache™

Thanks for your time.

---

### Post by sdman on 2007-03-19
Well I just started out myself and am willing to learn like yourself. I have read alot of opinions but think the more people that jump on the band wagon the better 64 bit systems will get introduced faster. Alot of people are new to c2d it seems just a waste to put this rocking processor on 32bit system it wasnt meant for. It all depends on how much time you want to devulge into getting the workarounds.

---

### Post by matt_feliks on 2007-03-19
I'm guessing "workarounds" means I'm going to have to fix them everytime I update the kernel ;)

At the moment I'm thinking I'll give regular 32 bit a try and familiarise myself with kubuntu before moving on to 64 bit in a few weeks time. That way I'll probably appreciate the 64bit architecture more anyway.


Matt

---

### Post by in_flu_ence on 2007-03-19
For general use, you probably will not see much gain out of the 64bit anyway. If you are new, 32bit might be great in order for you to know kubuntu inside out. I guess you can always come back to try 64bit, say, in 6 month time or when feisty is out.

---

### Post by Kilz on 2007-03-19
> **matt_feliks said:**
> I'm guessing "workarounds" means I'm going to have to fix them everytime I update the kernel ;)

At the moment I'm thinking I'll give regular 32 bit a try and familiarise myself with kubuntu before moving on to 64 bit in a few weeks time. That way I'll probably appreciate the 64bit architecture more anyway.


Matt

No, once you install a work around for the few pieces of proprietary software its done. 

Sadly we get more and more FUD dealing people without a clue dealing misinformation when someone asks about the amd64 bit version.

---

### Post by enopepsoo on 2007-03-19
I find that I generally need to update my video drivers after kernel upgrades (I use the envy script).  Once this has been done I need to run vmware-config.pl to get my vms back.

---

### Post by dptxp on 2007-03-20
I am using 64 bit. Go for it, form your own opinion.
THose who suggest 32 bit (without offence to them) are like
suggesting Windows users to stick to 32 bit XP snd wait for
5 years to use Vista 64 bit.

---

### Post by Kilz on 2007-03-20
> **enopepsoo said:**
> I find that I generally need to update my video drivers after kernel upgrades (I use the envy script).  Once this has been done I need to run vmware-config.pl to get my vms back.

But that isnt a something specific to the 64bit version. Recompiling kernel modules is something all versions must do.

---

### Post by in_flu_ence on 2007-03-20
> **dptxp said:**
> I am using 64 bit. Go for it, form your own opinion.
THose who suggest 32 bit (without offence to them) are like
suggesting Windows users to stick to 32 bit XP snd wait for
5 years to use Vista 64 bit.

There is no offence on this. I do recommend people to go for 64bit if they have the time for a few tweak. However, for an absolute newbie with no prior knowledge of linux, I think they may find it easier to adapt to the linux world with the current 32bit ubuntu especially for people who just want a stable desktop out of the box. There are a large community out there that doesn't really know much about computers. Let alone the difference in 32bits and 64bits. so one step at a time for them.:P

Anyway, for those who had taken the "30days" trial of our wonderful ubuntu OS. You are most welcome and recommended to try our 64bit OS if your hardware meets the requirement. It works great with some tweak.

'Can't wait to see the stable version of 64bit feisty coming in months time.

---

### Post by Kilz on 2007-03-20
> **in_flu_ence said:**
> There is no offence on this. I do recommend people to go for 64bit if they have the time for a few tweak. However, for an absolute newbie with no prior knowledge of linux, I think they may find it easier to adapt to the linux world with the current 32bit ubuntu especially for people who just want a stable desktop out of the box. There are a large community out there that doesn't really know much about computers. Let alone the difference in 32bits and 64bits. so one step at a time for them.:P

Anyway, for those who had taken the "30days" trial of our wonderful ubuntu OS. You are most welcome and recommended to try our 64bit OS if your hardware meets the requirement. It works great with some tweak.

'Can't wait to see the stable version of 64bit feisty coming in months time.

I disagree that we should "dumb down" for people. That the 64bit version is in fact very stable out of the box. That there is no need to run the 32bit for 30days.
That while you may have meant well, some of what you are saying is FUD.

---

### Post by in_flu_ence on 2007-03-20
No offense to scare new users from trying 64bit. I make my correction. 64bit OS is stable out of the box. I should however use the word "integration" out of the box. For the "stable" desktop, i meant integrating various libraries and plugins to get things working smoothly (e.g. firefox with flash and java). The 32bit version is currently having better integration due to lots of proprietary stuff not being opensourced. No fault of the open source community because there are alot of alternative software that work in the similar way.

The "30 day" trial is by no mean a "must" step for new users. It just simply mean that it will be easier to get on with the essential learning before tweaking (and maybe breaking the system).

Maybe it is as said mostly FUD. But the topic of whether 64bit should be installed has appeared many times mean that there is a certain "barrier" that people want to overcome before plunging into an experience. I really do hope new users to have the first experience as perfect as possible so that they will not turn back to windows and make another 'wait'.

For current WinXP users, I think if you are pondering if you should upgrade to Windows Vista for its 64bit processing, you will certainly having a similar thought about using the 64bit Linux OS. Most of you will probably be concerned about compatibility of software, etc and want to make sure you can have best software capability. Then you will have to concern about your choice properly.

While I should encourage people to go 64bit to make a better market to build better drivers etc, the final choice of which will still lie on the end-users hand.

I don't mean to offend anyone or "dumb down" for people. I simply brings up my own experience being a previous windows user for the past years.

That's why I really wish the new feisty will have much better capability in 64bit computing after the few major partnership recently and I can encourage the whole world to dump 32bit and go 64bit.
At this time, I will encourage some to go 64bit while others on 32bits depending on their past experience and needs.:)

---

### Post by FrozenFOXX on 2007-03-20
I recommend the 64-bit install to anyone with a 64-bit processor.  Increasing the installed base is the only way to force its priority to raise.

On top of that most users are actually a lot smarter than they think.  I've had more than a few friends who thought they wouldn't be able to handle Linux if it wasn't point-n-click.  Lo and behold a week later they were rocking Slackware like it was old news.  64-bit Ubuntu is *considerably* easier.


Just point people at the support forum, sign them up for an account, make sure they know where the IRC chatroom is and how to get into it if they have an emergency (or maybe they just work better that way), and give them the benefit of the doubt if they say they really want to try something new.  If it was identical there'd be no point in changing OS...people know this subconsciously, even if they wouldn't admit to it consciously.

---

