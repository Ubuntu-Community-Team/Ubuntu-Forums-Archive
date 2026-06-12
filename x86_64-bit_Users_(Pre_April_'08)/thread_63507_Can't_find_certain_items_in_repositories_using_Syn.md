---
title: "Can't find certain items in repositories using Synaptic"
date: 2005-09-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by puppy on 2005-09-08
Hi folks, running the 64-bit version of Hoary Hedgehog and, although I have had a few teething problems, I'm really getting into it now - my Battlestar Galactica Series 1 DVDs look great playing in Xine, and I've even got "autoplay" to work so that it starts up whenever I insert a DVD movie into the drive  \\:D/ 

Slight problem though - I have added all the repositories, including the back-ports, but I can't find certain apps, such as acroread, flashplayer, the java run-time and one or two others...

Is this because they are not available in 64-bit versions yet, or are there certain obscure repositories I should add so that I can get hold of them?

Any advice much appreciated

Pup

---

### Post by swamytk on 2005-09-08
[QUOTE=puppy] certain apps, such as acroread, flashplayer, the java run-time and one or two others...
[/QUOTE]

All these are having some commericial terms and licenses, so that they can't be available in official ubuntu repository. Check with backport repositories.

Try with this line in your /etc/apt/sources.list:

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

---

### Post by puppy on 2005-09-08
Actually, I have those repositories and these packages aren't there. 

I have however answered my own question - Tamir has an excellent thread open in this forum where he is making 64-bit versions of apps available and asking people to submit ideas for other ones that they want. I will link to his repository tonight and try some things out  :-) 

His thread is here:

[http://ubuntuforums.org/showthread.php?t=48905](http://ubuntuforums.org/showthread.php?t=48905)

There is also a petition for flash support in 64-bit linux here - let's all make sure we sign it! 

[http://ubuntuforums.org/showthread.php?t=51211](http://ubuntuforums.org/showthread.php?t=51211)

Aren't Ubuntu users wonderful  :grin:

---

