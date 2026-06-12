---
title: "Major questions about going to 64-bit"
date: 2006-12-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by agamotto on 2006-12-15
I have been looking around in this and other forums discussing 64-bit linux, and I am almost as confused as I started!  <grin>  I am looking to upgrade from my Athon 2400 32-bit machine into a 64-bit environment.

I need advice on the following:

1.  What hardware has been successful for you?  Please mention vendors, if ready-made style systems, or what components if it is a roll-own system.

2.  What software just plain doesn't work under the 64-bit version of Ubuntu so far?

3.  Is it worth the upgrade, or should I just wait another calendar year to give the 64-bit market time to mature?

4. What do people really mean when stating that they are running the 32-bit version on their 64-bit machines?  You are using the 32-bit version because it works better, or because there isn't a 64-bit version of your program/app available yet?

Thanks in advance



My main reason in posting is that I have sent emails to a few large vendors, such as Cyberpowerpcs, and their response is pretty much 'we don't know anything about linux.'

---

### Post by eriefisher on 2006-12-15
Well I have tried the Dapper 64bit live disc on my Compaq presario V5000 laptop with a AMD Turion64 and everything seemed to work except the wireless. It was detected but I don't have a wireless set up here so I don't know for sure. Hope this is some help.

---

### Post by Blindraven on 2006-12-15
I installed Edgy the other day, I have not used linux since - what, a 2.4 kernel using slackware.

I am far from an expert, or evan mediochre user, I have extremely little knowledge of anything and the command use of linux is way over my heead - But I "can" tell you this.

I am running an am2 4200+(64) - using a 7600gt (foxcon) and ddr2 (1 gig samsung) - And aside from firefox crashing every 2 minutes, I could barely tell you this was a beta release.

As I said in a thread last night, If I (complete idiot) can work my way around this install, surely anyone else can.

I used some program called Automatix 2 to get me started, it had a huge amount of 64bit applications that I was able to just point-click to download and it did the rest for me.

Even Frostwire (32bit) installed and worked successfully(was it supposed to, considering its a 32bit app?).

So all in all, I say go for it, and again - why settle for less?

Hope this helps.
Tony.

---

### Post by Chenzo on 2006-12-15
I am very new to linux. I had been running 32 bit breezy, and about two weeks ago I upgraded to 64 bit edgy.  I've had my fair share of problems, and probably spent as much time getting linux running as I have using it (although 80% of my headaches come from ATI, NOT 64 bit) but I have everything I want running by now.  While 64 bit has caused some problems, they have not been too difficult to solve and I can't say it was any more troublesome than 32 bit.  I would also agree to start with Automatix2, if not just for the swiftfox browser and plugins. 

If I can get everything I need running in a week with almost 0 linux experience, I'm sure you would be ok.

FYI: 64 bit edgy on an amd 3000+, radeon X800.

---

### Post by cocteau on 2006-12-15
> **agamotto said:**
> 
1.  What hardware has been successful for you?  Please mention vendors, if ready-made style systems, or what components if it is a roll-own system.

I use an AMD 3200+ 64 bit CPU and the average no-name default installed onboard netcard and what not. It works like a charm. I use an external soundcard Edirol UA25 which works in 'advanced' (their wording, not mine) mode out of the box. And a ATI 9600 XT card with dual head monitors. The ATI drivers are a little funky though. OpenGL works fine in games under Cedega but not in OpenGL screensavers on the desktop. I have no idea why.

> **agamotto said:**
> 2.  What software just plain doesn't work under the 64-bit version of Ubuntu so far?

There should be a sticky in the 64bit section describing what software can cause trouble. I haven't found anything that's not troublesome anyway, like VST plug ins. Other people will tell you differently but I haven't had any problems worth mentioning. Stuff that aren't available in pure 64bit can be installed as 32bit and run with very little performance loss.

> **agamotto said:**
> 3.  Is it worth the upgrade, or should I just wait another calendar year to give the 64-bit market time to mature?

Well, I would suggest to create a small partition and try it out. I don't think that any advice can beat actually trying stuff out for yourself.

I have found that edgy doesn't really work for me. There was some problems with Anjuta so I've decided to wait a while. Dapper is working smoothly in 64 bit.

> **agamotto said:**
> 4. What do people really mean when stating that they are running the 32-bit version on their 64-bit machines?  You are using the 32-bit version because it works better, or because there isn't a 64-bit version of your program/app available yet?

The 64bit CPUs are capable of running in 32bit mode to ease transition into the 64bit world. It is perfectly possible to install a 32bit OS if you have a 64bit CPU. It is also possible to install 32bit apps in a 64bit OS. Some people claim that the 32bit works better. It is especially stuff like Flash and Java that is mentioned but it is possible to install a 32bit version of firefox under Ubuntu and run both Flash and Java and some other stuff. Search for a post by Kilz on these forums and look in his signature. He's made a killer howto on how to set it up and its just so simple.

---

### Post by agamotto on 2006-12-16
Thanks for the info so far!  So, it seems that I should at least be able to run one of the 32-bit x86 Ubuntu distros on the new machine, if I just have too much trouble with the 64-bit.  Coolies.  The only question I can think of that I forgot to ask - 

Is anyone running their 64-bit Ubuntu on a AM2 motherboard?  I don't yet quite understand the difference between socket 939 and AM2 - and the whole dual-processor concept...

---

### Post by Kilz on 2006-12-17
> **agamotto said:**
> Thanks for the info so far!  So, it seems that I should at least be able to run one of the 32-bit x86 Ubuntu distros on the new machine, if I just have too much trouble with the 64-bit.  Coolies.  The only question I can think of that I forgot to ask - 

Is anyone running their 64-bit Ubuntu on a AM2 motherboard?  I don't yet quite understand the difference between socket 939 and AM2 - and the whole dual-processor concept...

A 32bit operating system is not the cure all as some people suggest. There are instances of users with 64bit hardware having problems running the 32bit os.

---

### Post by tszanon on 2006-12-18
> **agamotto said:**
> Is anyone running their 64-bit Ubuntu on a AM2 motherboard?  I don't yet quite understand the difference between socket 939 and AM2 - and the whole dual-processor concept...

I'm running Ubuntu on an AM2 motherboard. No problems at all with Ubuntu, but the motherboard is a piece of garbage.

The difference between 939 and AM2 is simply the memory: 939 works with DDR memory, and AM2 works with DDR2 memory. Both sockets can handle dual-core processors, so no change there. Just remember that they're not compatible: you can not insert a AM2 processor in a socket 939, nor put a socket 939 processor in a socket AM2.

---

### Post by cthippo on 2006-12-19
Running Dapper on a dual Opteron / Tyan K8WE system here and the basics worked pretty smoothly from the get-go.  I had to use the alternate install to get my video cards (dual 7800GTs) to work, but since then I got the correct drivers and life has been good.  I had a few hardware issues, notably my X-fi sound card, but that is a linux issue rather than a 64 bit issue, and I got around it by enabling on-board sound.  Biggest headache (now solved) was getting Opera to work, but I finally got that going tonight.  

  Is 64 bit better?  Honestly, i couldn't tell you as I'm migrating from 64 bit windows.  There is a thread on here that offers some pretty good stats saying that it is, but as the wise man said there are lies, damn lies and statistics.  I'm still working towards profiencieny with it, but so far I like it :mrgreen:

---

