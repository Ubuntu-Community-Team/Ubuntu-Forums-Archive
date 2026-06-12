---
title: "Anyone get splashy working with amd64 kernel?"
date: 2005-06-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by Major Nuggs on 2005-06-06
Greetings, first let me say howdy..  New Ubuntu user and new to the forums.  wooOOoo me.  :p

Anyways, I'm using the amd64-generic kernel because I heard the k8 freezes randomly..  :p

I can't compile splashy..  Well, i can probably compile that..  But directfb gives me crap and stuff that's already defined(all system headers, not from directfb).

I probably should post the compile errors but I just have this feeling that if I'm using a pretty stock system then other people experienced this also if trying to install it..

I'd really like to add some eyecandy to my boot..  Anyone got it running under the 64bit kernel?

Also, what about the random freezing problem with the K8 kernel?  I'd like to use it..  just don't want random crashes..  I don't like to reboot..  too much work.  hah.  then again, I'd like to get a bootsplash going..  make sense?  roffle.

If you absolutly need more information..  I can post it..  just working 10 hours a day six days a week makes me really lazy..  and I'd just like for it to _work_ just for once..  it's never that easy though..  Linux likes to make you _work_ for it's attention.

or the users do..  you decide.

Kind Regards,
Anthony

---

### Post by Major Nuggs on 2005-06-06
:(

*me cries

---

### Post by negatory on 2005-06-07
Random crashes?Where did you heard that?
I've got the 2.6.10-5-amd64-k8 kernel and have 15 days of uptime...
I find that kernel very stable.
As for splashy I don't know what it is....

Pedro Carrico

---

### Post by Major Nuggs on 2005-06-07
I got it from the forums..

---

### Post by duffman25 on 2005-06-10
Any progress with splashy in amd64? I have 2 pc's at home and I want to install splashy on my amd64 machine, but all I could find are debian packages... I could install them, but I would prefere if someone that has managed to get it to work under ubuntu said how to do it ;)

Thanxs

---

### Post by wiraone on 2005-06-12
[QUOTE=negatory]Random crashes?Where did you heard that?
I've got the 2.6.10-5-amd64-k8 kernel and have 15 days of uptime...
I find that kernel very stable.
As for splashy I don't know what it is....

Pedro Carrico[/QUOTE]
 I've just upgraded my system from Athlon 1700+ to Athlon64 2800+ .. and yes, I had lot of crashes the first time. My config has Asus K8N, ATI Radeon 9520, 1GB Kingston DDR400 .. It took me few days to get it stable .. and it hardly crash on me now. Most of the time, adding **noapic** to the kernel boot line will solve most of this kind of problem but in my case, RAM contributed to this problem .. did a memtest run during bootup and found that one of the two modules went bad .. reseated them properly and the problem gone.

---

### Post by Optimal Aurora on 2005-06-12
I have been using it myself and don't have alot of crashes, the only crash that I had was when I did a full dist-upgrade to breezy and that cause a crash but not when I am using hoary stuff and the amd64-K8 kernel my system is faster than the generic kernel was and less buggy (now if you are talking about the generic kernel I would have to agree with the crashes but not the optimized kernel...)

---

### Post by dickohead on 2005-06-28
[QUOTE=Major Nuggs]Greetings, first let me say howdy..  New Ubuntu user and new to the forums.  wooOOoo me.  :p

Anyways, I'm using the amd64-generic kernel because I heard the k8 freezes randomly..  :p

I can't compile splashy..  Well, i can probably compile that..  But directfb gives me crap and stuff that's already defined(all system headers, not from directfb).

I probably should post the compile errors but I just have this feeling that if I'm using a pretty stock system then other people experienced this also if trying to install it..

I'd really like to add some eyecandy to my boot..  Anyone got it running under the 64bit kernel?

Also, what about the random freezing problem with the K8 kernel?  I'd like to use it..  just don't want random crashes..  I don't like to reboot..  too much work.  hah.  then again, I'd like to get a bootsplash going..  make sense?  roffle.

If you absolutly need more information..  I can post it..  just working 10 hours a day six days a week makes me really lazy..  and I'd just like for it to _work_ just for once..  it's never that easy though..  Linux likes to make you _work_ for it's attention.

or the users do..  you decide.

Kind Regards,
Anthony[/QUOTE]
 Hey guys,

Would someone be able to point/link me to the 64bit packages for Splashy? I have as yet been unable to find them.

Dickohead.

---

### Post by billycub on 2005-06-28
Yep, I got splashy to work on my amd64-k8 kernel.  Seems to work fine so far.

I had to compile from the splashy source.tar.gz because the deb file complained about wrong architecture and wrong libc6 version.  Compiling from source was easy -- untarred, then did ./configure --prefix=/ && make && make install.

The configure script asked for some dev libraries which I installed from synaptic.

If anyone has created or can find a .deb file for splashy-amd64 I'd appreciate it!

-Billy

---

### Post by MiD-AwE on 2006-10-23
I've seen the "How To" but I'm not feeling confident about the accuracy.
[Splashy (replacement for usplash and bootsplash)]("http://www.ubuntuforums.org/showthread.php?t=216597&highlight=Splashy+%28replacement+for+usplash+bootsplash%29")
And, having visited [the wiki of the Splashy Project]("http://splashy.alioth.debian.org/wiki/doku.php") I still ask the question. Has anyone created a .deb file for splashy-amd64?

---

