---
title: "Is this a bad joke or something???(Usplash related)"
date: 2006-12-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by Jimmy_r on 2006-12-30
I have been using the 64 bit version of Ubuntu since Breezy(when I began using Linux).
When some things did not work (Flash, Java plug-in, etc), I was comforted by the fact that they were "closed source".
When I began using Edgy, the last straw was Usplash. Since the alpha-releases, usplash would not work. Later in the cycle, they got usplash running, but with black/white artwork.
Not only was Usplash "open source", but also developed by Ubuntu devs. So that was the last straw and I began using the 32-bit version.
Some time ago I tried Feisty to see if the problem was resolved there, but no.
I figured it must had been a really severe bug...
Reading bugreports on Launchpad this does not seem to be prioritized at all.

Today I found some threads about it in this sub-forum, and a "fix" also.
I begun investigations and found that it really was not so severe a bug.

In fact, I took a theme I had been modifying earlier on 32-bit and "adapted" it for 64-bit.
By adapting, I mean that I opened the themes c file and deleted a few blocks of code(making it a 1280x1024 only theme).
I did not have to write a single line of code.
I compiled and installed it, and it worked. Usplash in full color at 1280x1024. (.so file attached)

So, does anybody know what is the deal with this?
Why does Ubuntu devs cripple the 64-bit version??

---

### Post by ciscosurfer on 2006-12-30
I'm not sure I follow your concern.  Can you rephrase your question, please?  What exactly are you trying to say?

---

### Post by Dun on 2006-12-31
> **ciscosurfer said:**
> I'm not sure I follow your concern.  Can you rephrase your question, please?  What exactly are you trying to say?

I agree with OP, this issue has been severely neglected by the Ubuntu 64-bit developers. A bugraport has been filed Nov 22, and still no progress has been made. The usplash is after all the first thing a new user sees. This whole issue has made me look Ubuntu in a very different light. Perhaps the six months release cycle is too much?

---

### Post by Jimmy_r on 2006-12-31
> **ciscosurfer said:**
> I'm not sure I follow your concern.  Can you rephrase your question, please?  What exactly are you trying to say?

I mean that I was turned off from the 64 bit version because of the usplash black/white bug(not only that, but it was the last straw).

Now I realized that I, as a hobby programmer, could fix that "bug" in a few minutes.
So has someone before me, a few weeks ago: [http://www.ubuntuforums.org/showthread.php?t=304673&page=3]("http://www.ubuntuforums.org/showthread.php?t=304673&page=3")
The fix was also posted directly to the bug report:
[https://bugs.launchpad.net/distros/ubuntu/+source/usplash-theme-ubuntu/+bug/67545]("https://bugs.launchpad.net/distros/ubuntu/+source/usplash-theme-ubuntu/+bug/67545")
A bugreport that has got the priority "low" and does not appear to have any developer activity.

So the question is: **If it is so easy to fix, why has it not even been fixed in Feisty?**
I thought that perhaps someone on these forums had heard something, so that I would not have to bother the developers with my questions directly.

I just got the impression(after this, and reading the conversation between kilz and the ubuntu devs) that 64-bit on ubuntu is underprioritized.

> **Dun said:**
> This whole issue has made me look Ubuntu in a very different light. Perhaps the six months release cycle is too much?

I can only agree...

It is their distribution, they do with it as they please and I really have no right to complain(it is free after all), but if they do not want to support 64-bit can they please state that clearly instead of delivering a crippled Ubuntu that will only turn potential users off?
If a new linux user decides to try this new thing called Ubuntu and installs a version suitable for his new 64-bit processor only to be greeted by this black/white splash, missing flash/Java plugins will only make him run faster towards his Windows CD...

---

