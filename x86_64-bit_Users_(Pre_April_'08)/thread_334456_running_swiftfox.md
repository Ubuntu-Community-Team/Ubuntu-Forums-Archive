---
title: "running swiftfox"
date: 2007-01-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by Brando569 on 2007-01-08
does anyone else have a problem running the new swiftfox? i found a post on their board about it and the guy didnt get an answer (it was from 12/26)  this seems to be the commom problem:

/opt/swiftfox/run-mozilla.sh: 424: /opt/swiftfox/swiftfox-bin: not found

anyone have a solution??

---

### Post by raul_ on 2007-01-08
could you explain a little better?

could you post the output of
```

ls /opt/swiftfox

```

please?

---

### Post by slicker on 2007-01-09
> **Brando569 said:**
> does anyone else have a problem running the new swiftfox? i found a post on their board about it and the guy didnt get an answer (it was from 12/26)  this seems to be the commom problem:

/opt/swiftfox/run-mozilla.sh: 424: /opt/swiftfox/swiftfox-bin: not found

anyone have a solution??

I have a soloution. Dont run it. Its non-free and proprietary. As such it has fewer people looking at the code and is a security risk. Use Firefox or Iceweasel.

---

### Post by raul_ on 2007-01-09
> **slicker said:**
> I have a soloution. Dont run it. Its non-free and proprietary. As such it has fewer people looking at the code and is a security risk. Use Firefox or Iceweasel.

That's not what this forum is for

---

### Post by ginsuedog on 2007-01-09
Which build of swiftfox are you using and how did you install it?  From what I understand there are two ways, one download the package and then run sudo dpkg --install swiftfox_2.0.0.1-1_*.deb or add the repository deb [http://getswiftfox.com/builds/debian](http://getswiftfox.com/builds/debian) unstable non-free.  Then type the following in the command line:  sudo apt-get update && apt-get install swiftfox-pentium4.

I've used 2.0, 2.0.0.1, and 2.0.0.2pre without issues, try reinstalling the package using the .deb file or via apt-get.

P.S.-What is the output from typing the following in the command line:
slocate swiftfox-bin

---

### Post by Unterseeboot_234 on 2007-01-09
I just checked my /opt folder. The firefox symlink directs to swiftfox-bin. The only way I've installed swiftfox is with Automatix2. IF and WHEN the ubuntu 32-bit firefox can connect to the 64-bit downloader, I will change, or IF and WHEN the ubuntu 64-bit firefox can run MPlayer, flash, I will change. swiftfox triples my download speed with DSL and that is important to me.

I have had problems in the past with Synaptic telling me there is an update. I let it update after making a note the updates were for firefox. That screwed it all up. I had to uninstall swiftfox and reinstall it. I have to keep my java development links separate from my swiftfox plug-in (I'm using the 64-bit java SDK anyway, and 64-bit java doesn't come with a plug-in). The swiftfox plug-ins all begin with ia32-plugin....

So, I guess I'm telling you that you have to re-install swift-. If you're still with problems, you might have to deinstall fire-. Use Synaptic, don't perform surgery on your File System by manually deleting firefox 32-bit. Good luck.

---

### Post by Brando569 on 2007-01-10
now it seems to work, i used synaptic to install it (there wasnt a p4 version of it in the repo only amd64 which is what i needed anyway) and it seems that the reason it wasnt working was because it needed about 6 or so (32bit) libraries, i guess automatix always installed them or something, idk.. btw does anyone have the repo address for it? i lost it and the site is down :?

---

### Post by slicker on 2007-01-10
> **raul_ said:**
> That's not what this forum is for

This forum is to give advice. That's what I did. Ubuntu is an Debian derivative, with a Foss philosophy. We should all do our part to promote free software over non-free. 

[QUOTE=Unterseeboot_234]   IF and WHEN the ubuntu 32-bit firefox can connect to the 64-bit downloader, I will change, or IF and WHEN the ubuntu 64-bit firefox can run MPlayer, flash, I will change. swiftfox triples my download speed with DSL and that is important to me.[/quote]

Swiftfox is 32bit, all versions, even the one for the 64bit processor. That is the reason all your 32bit plugins work. The download speed is all settings anyone can change, but the easy way to do it is just to install the fasterfox plugin.

---

### Post by raul_ on 2007-01-10
> **slicker said:**
> This forum is to give advice. That's what I did. Ubuntu is an Debian derivative, with a Foss philosophy. We should all do our part to promote free software over non-free. 

The forum is to give help. If he wanted advice he would've wrote something like "hey what do u think about...."

Anyway, the job here is not about promoting free software or not. People use what they want. If somebody asks for help on how to install the latest java, the latest ati drivers, i'm going to help them, i won't say "don't use it".

Glad we got that straight :cool:

---

### Post by slicker on 2007-01-11
> **raul_ said:**
> The forum is to give help. If he wanted advice he would've wrote something like "hey what do u think about...."

Anyway, the job here is not about promoting free software or not. People use what they want. If somebody asks for help on how to install the latest java, the latest ati drivers, i'm going to help them, i won't say "don't use it".

Glad we got that straight :cool:
That's your choice, to use proprietary software. But it is not a good idea, imho, and that of the majority of the Foss community. You have every right to do it, and suggest to others to do it. But I don't think you have a right to tell me or others what to do, or what to write when helping people. That is the job of moderators, a title I see you do not possess.
Glad we got that strait.

---

### Post by raul_ on 2007-01-11
[http://www.ubuntuforums.org/showthread.php?t=335094&highlight=richard+stallman]("http://www.ubuntuforums.org/showthread.php?t=335094&highlight=richard+stallman")

Humm. I guess i'm not the only using proprietary software then :mrgreen: I didn't tell you what to write man, i just said that the guy asked for help and you told him not to use the program. What kind of help is that? For the same reason i can't tell you what to write you can't tell the guy what to use. 

anyway, this thread should be locked

---

### Post by Brando569 on 2007-01-12
>  But I don't think you have a right to tell me or others what to do

do i detect some hypocrisy here? IIRC you were telling me what to use and what not to use. anyway this is over and done with, my problem is fixed. thanks to all that helped

/thread

---

### Post by Kilz on 2007-01-12
> **Brando569 said:**
> do i detect some hypocrisy here? IIRC you were telling me what to use and what not to use. anyway this is over and done with, my problem is fixed. thanks to all that helped

/thread

I disagree, not using an application is a solution. Especially if their are other versions or forks of that application. As users of free and open source software we should always look at the freedom the application offers. Applications that don't give you one of [the 4 freedoms]("http://www.fsf.org/licensing/essays/free-sw.html"), or take away a freedom should be avoided.

---

### Post by Brando569 on 2007-01-12
that doesnt really relate to what i was saying. slicker was first telling me what what to use and what not to use, then he turns around and is like dont tell me what to say and what not to say. i find that to be pretty hypocritical. anyway this isnt a thread about all this it was about me not being able to use swiftfox, which i now can. 

will a mod please lock this

---

### Post by Kilz on 2007-01-13
> **Brando569 said:**
> that doesnt really relate to what i was saying. slicker was first telling me what what to use and what not to use, then he turns around and is like dont tell me what to say and what not to say. i find that to be pretty hypocritical. anyway this isnt a thread about all this it was about me not being able to use swiftfox, which i now can. 

will a mod please lock this

I dont think so. You are paraphrasing what he said.

> **slicker said:**
> I have a soloution. Dont run it.

He in his own words gave you a solution, and what you asked for was a "solution"

> **Brando569 said:**
> anyone have a solution??

I do believe not running a proprietary application, but instead running a free one is a solution. The problem is someone told him thats not what this forum is for. But informing and helping is exactly what this forum is for.

---

