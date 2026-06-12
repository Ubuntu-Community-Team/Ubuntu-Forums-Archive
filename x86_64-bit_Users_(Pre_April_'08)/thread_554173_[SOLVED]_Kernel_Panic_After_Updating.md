---
title: "[SOLVED] Kernel Panic After Updating"
date: 2007-09-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by Yellow Pasque on 2007-09-18
I fired up my system tonight and everything proceeded as normal. I then used update manager to install 204 updates, including a kernel image. After doing that, it told me a restart was required, so I finished what I was working on, closed my programs and restarted.

Now I get a kernel panic on boot (Attempting to kill init).

Any ideas?


OS: Gutsy Tribe 5, fully updated (as of this morning)
Hardware: Athlon X2 4800 Brisbane, 2 GB Patriot DDR2-667, MSI K9AG Neo2 mobo (AMD 690G chipset), M-audio Revolution 5.1 sound card

---

### Post by Kilz on 2007-09-18
> **Temüjin said:**
> I fired up my system tonight and everything proceeded as normal. I then used update manager to install 204 updates, including a kernel image. After doing that, it told me a restart was required, so I finished what I was working on, closed my programs and restarted.

Now I get a kernel panic on boot (Attempting to kill init).

Any ideas?


OS: Gutsy Tribe 5, fully updated (as of this morning)
Hardware: Athlon X2 4800 Brisbane, 2 GB Patriot DDR2-667, MSI K9AG Neo2 mobo (AMD 690G chipset), M-audio Revolution 5.1 sound card

](*,) You are experiencing one of the realities of running DEVELOPMENT versions. Things break, an update can make things worse. This is why they have warnings all over that gutsy shouldn't be used on production machines. 
Development versions should only be used for testing , never for your machine you count on to work. You should also have a FIRM understanding of how to troubleshoot a broken system. Not when it breaks post "any ideas?".

---

### Post by Yellow Pasque on 2007-09-18
Well, I was wondering if anyone else running Gutsy64 had this problem. I'm guessing I'm not the only one.

---

### Post by Yellow Pasque on 2007-09-21
> **Temüjin said:**
> Well, I was wondering if anyone else running Gutsy64 had this problem. I'm guessing I'm not the only one.

Apparently, I am. :P

So far, I've done a new Feisty64 install on another HD and I'm in the process of backing up the personal files that I've added/changed since a few weeks ago. I'd really like to get my Gutsy install back up though, because it was perfect until I installed the most recent (at the time) round of updates.

Is there any way I can copy a new Gutsy kernel over the old one? I'm hoping it was just file corruption that brought that install down.

Thanks.

---

### Post by Yellow Pasque on 2007-09-21
Never mind. I got impatient and decided to set up a new gutsy64 installation after getting all the data I needed off the old install. I've gotten really good at doing these installs now.

I'm still not sure what caused the panic. I have a feeling it had something to do with the 2.6.22-11 kernel, since I've seen a few reports of people reporting kernel panics after they updated. The new 2.6.22-12 kernel is running smoothly for me,

Note to Kilz: In my profile, above every post I make, it says "Gutsy Testing User". I KNOW what a development version is, and I obviously had other disks/OS's to recover from. I actually work in a Solaris environment at my office, and thus, my home box is for leisure. So quit banging your head on the wall and stay out of any threads I make in the future if you don't have something helpful to add. Thanks. (/me tosses you an icepack for that bump on your head)

---

### Post by typogenerator on 2007-09-22
I gotta reply to Kilz as well. I'm running Gutsy on my test system and Feisty on my other, in case you're wondering. Plus, I develop software for a living, and when things are in development, and when they break (they will), only an arrogant know-it-all doesn't reach out to the rest of the development community for assistance. That's the whole point--you don't just say, well, darn, this broke. I guess I'll turn it off.

I don't mean to just go off on you and I know I never post here, but the truth is, I want to go off on **you **and the rest of the posters here who reply to users with nothing more than snide or sarcastic remarks -- that's no help and only fosters the kind of ill will you find on other sites. 

Go do a little research on what Ubuntu is about. You can't tell me that your comment here (and elsewhere no doubt) are helpful, sharing or any of that other good stuff. If you can only be condescending, don't do it here. 

Really, though, no offense.

---

### Post by rwood on 2007-09-30
same problem here with kernel panic 
first time i cant even start in rescue. been testing for a coulple years 
with lots of problems solved with the help from forums

---

### Post by jocko on 2007-10-01
Have you tried following [these instructions]("http://ubuntuforums.org/showthread.php?t=306424") to fix it?
It will give you acces to your system from a live session.
In case something went wrong with your latest kernel upgrade, maybe one more upgrade will fix it, at least if there is a newer version in the repos.
And if there are no new kernels available, maybe reinstalling one of the older ones will help (look for linux-image* in /var/cache/apt/archives).

Good luck.
And kilz: Ubuntu's philosophy is "humanity towards others", not "arrogance towards others"

---

### Post by Kilz on 2007-10-01
> **Temüjin said:**
> 
Note to Kilz: In my profile, above every post I make, it says "Gutsy Testing User". I KNOW what a development version is, and I obviously had other disks/OS's to recover from. I actually work in a Solaris environment at my office, and thus, my home box is for leisure. So quit banging your head on the wall and stay out of any threads I make in the future if you don't have something helpful to add. Thanks. (/me tosses you an icepack for that bump on your head)
The forum is open to all, make a post and anyone can post to it. 
Every word I post is an attempt to help someone. You personally may not be the person I help with that message if I can keep one more beginner away from using development versions.

> **typogenerator said:**
> I gotta reply to Kilz as well. I'm running Gutsy on my test system and Feisty on my other, in case you're wondering. Plus, I develop software for a living, and when things are in development, and when they break (they will), only an arrogant know-it-all doesn't reach out to the rest of the development community for assistance. That's the whole point--you don't just say, well, darn, this broke. I guess I'll turn it off.

I don't mean to just go off on you and I know I never post here, but the truth is, I want to go off on **you **and the rest of the posters here who reply to users with nothing more than snide or sarcastic remarks -- that's no help and only fosters the kind of ill will you find on other sites. 

Go do a little research on what Ubuntu is about. You can't tell me that your comment here (and elsewhere no doubt) are helpful, sharing or any of that other good stuff. If you can only be condescending, don't do it here. 

Really, though, no offense.
and 
> **jocko said:**
> 
And kilz: Ubuntu's philosophy is "humanity towards others", not "arrogance towards others"

It is hard to read into words and detect emotion on a forum. 

Those that think they have might want to read the above again.

Ubuntu is about making releases just work for people. The forums are about helping others. You personally may not be the "others" I help with that message if I can keep one more beginner away from using development versions.
Ubutnu is Not having people who just started using it use development versions. People who dont know that the place to report problems with development versions is the development forum. People who may not post to launchpad with bugs. People with no real idea what they are jumping into when they install a development version. Because the General sections (like this one) are for releases. Gutsy is not released yet.

---

