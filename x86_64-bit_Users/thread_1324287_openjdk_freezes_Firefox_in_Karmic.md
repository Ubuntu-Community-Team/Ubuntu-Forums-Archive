---
title: "openjdk freezes Firefox in Karmic"
date: 2009-11-12
forum: x86 64-bit Users
---

### Post by tlu on 2009-11-12
In Karmic openjdk freezes Firefox whenever I try to load a website requiring Java. In these cases I'm getting the following error message in .xsession-errors (or if I start FF in the console):

> /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/../../bin/java: error while loading shared libraries: libjli.so: cannot open shared object file: No such file or directory

I've filed a bug report on [https://bugs.launchpad.net/ubuntu/+source/openjdk-6/+bug/476550](https://bugs.launchpad.net/ubuntu/+source/openjdk-6/+bug/476550) some days ago but haven't got any response so far. 

Am I the only one affected by this problem? Are only 64bit systems affected?

Note that removing and reinstalling both openjdk and Firefox didn't help.

---

### Post by Bunnybugs on 2009-11-12
I recommend to install sun java untime from the repositories(Applications>Ubuntu Softwarcenter>Search for Sun Java Runtime)

Make sure that firefox isn't opened while installing!

---

### Post by tlu on 2009-11-12
> **Bunnybugs said:**
> I recommend to install sun java untime from the repositories(Applications>Ubuntu Softwarcenter>Search for Sun Java Runtime)


Thanks for your response. But I'm reluctant to follow this advice. Reasons:

1. openjdk is the standard java package in Jaunty/Karmic. It SHOULD work.
2. Sun Java is a universe package and, unfortunately, not always properly updated when a security update is available - see [https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/409559](https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/409559) . The available version in the Karmic repo right now is 6-15-1 although 6-17 with various security fixes is out from Sun.

The new version can be installed manually - see [http://ubuntuforums.org/showthread.php?t=1314202](http://ubuntuforums.org/showthread.php?t=1314202) . But that's a "solution" I want to avoid unless everything else fails.

---

### Post by Bunnybugs on 2009-11-12
> **tlu said:**
> Thanks for your response. But I'm reluctant to follow this advice. Reasons:

1. openjdk is the standard java package in Jaunty/Karmic. It SHOULD work.
2. Sun Java is a universe package and, unfortunately, not always properly updated when a security update is available - see [https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/409559](https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/409559) . The available version in the Karmic repo right now is 6-15-1 although 6-17 with various security fixes is out from Sun.

The new version can be installed manually - see [http://ubuntuforums.org/showthread.php?t=1314202](http://ubuntuforums.org/showthread.php?t=1314202) . But that's a "solution" I want to avoid unless everything else fails.


Well, I had the same trouble with OpenJDK... Tried IcedTea, but none of them worked... installed Sun, and it all works... can watch Youtube, can use chatboxes, etc, etc...

Guess it's a little bugged or some;)

---

### Post by Arup on 2009-11-13
Open JDK had a major version upgrade today, suggest you try it out after that. It works fine here with FF and Opera, Facebook photo upload works fine.

---

### Post by tlu on 2009-11-13
> **Arup said:**
> Open JDK had a major version upgrade today, suggest you try it out after that. It works fine here with FF and Opera, Facebook photo upload works fine.

Unfortunately it doesn't work for me :sad:

---

### Post by tlu on 2009-11-13
A new installation using the Alternate CD solved the problem - see [https://bugs.launchpad.net/ubuntu/+source/openjdk-6/+bug/476550](https://bugs.launchpad.net/ubuntu/+source/openjdk-6/+bug/476550)

---

### Post by Arup on 2009-11-13
tlu,

There was a txdata and a tztdata-java update yesterday, could be those two finally fixed your issue.

---

### Post by tlu on 2009-11-14
> **Arup said:**
> tlu,

There was a txdata and a tztdata-java update yesterday, could be those two finally fixed your issue.

Unfortunately today the problem is back. I'm getting sick of it ...:mad:


EDIT: I've replaced openjdk with Sun java, and all is well. But I'm not happy with this "solution".

---

### Post by Arup on 2009-11-14
> **tlu said:**
> Unfortunately today the problem is back. I'm getting sick of it ...:mad:


EDIT: I've replaced openjdk with Sun java, and all is well. But I'm not happy with this "solution".

tlu,

I am surprised as Open JDK works here on all the PCs I have installed it in. The reason I have turned away from Sun Java is because Ubuntu won't be upgrading it anymore. You have to do the upgrades yourself from the Java bin file. If Sun Java works for you, then I would stick with it.

btw are you the same tlu from Wilders, in that case greetings.

---

### Post by tlu on 2009-11-15
> **Arup said:**
> tlu,

I am surprised as Open JDK works here on all the PCs I have installed it in. The reason I have turned away from Sun Java is because Ubuntu won't be upgrading it anymore. You have to do the upgrades yourself from the Java bin file. If Sun Java works for you, then I would stick with it.

Arup,

I haven't installed Sun Java fron the repo but manually as explained on [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

I have no idea why openjdk doesn't work on my system. As mentioned it worked after the new installation. It stopped to work after I had changed the apparmor profile for firefox-3.5 to enforce mode. But the problem persisted when I changed it back to complain mode. Nevertheless, this might be an issue worth being investigated...

> btw are you the same tlu from Wilders, in that case greetings.

Yes, I am. Greetings also to you, Arup!

---

### Post by madhavsrao on 2009-11-15
yep tat worked for me toooo thanks

---

### Post by Arup on 2009-11-15
> **tlu said:**
> Arup,

I haven't installed Sun Java fron the repo but manually as explained on [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

I have no idea why openjdk doesn't work on my system. As mentioned it worked after the new installation. It stopped to work after I had changed the apparmor profile for firefox-3.5 to enforce mode. But the problem persisted when I changed it back to complain mode. Nevertheless, this might be an issue worth being investigated...



Yes, I am. Greetings also to you, Arup!


Nice to see you here tlu, the Java install works fine in most cases but when you install stuff like Open Office Base, the JDK version is drawn in.

---

### Post by tlu on 2009-11-15
> **Arup said:**
> Nice to see you here tlu, the Java install works fine in most cases but when you install stuff like Open Office Base, the JDK version is drawn in.
Good to see you here, too, Arup!

openoffice.org-base is not installed on my system. Besides, openjdk worked flawlessly under Jaunty. And it worked under Karmic after the new installation. Perhaps it was really the change in the apparmor profile that broke something ... oh, well, I think I have to try it out :roll:

---

### Post by Arup on 2009-11-15
If you don't need OO Base, stick with Sun Java which is more compatible than Open JDK. Even if there is Open JDK, you can always use update-alternatives to make Sun Java default.

---

### Post by tlu on 2009-11-16
> **Arup said:**
> If you don't need OO Base, stick with Sun Java which is more compatible than Open JDK. Even if there is Open JDK, you can always use update-alternatives to make Sun Java default.

Yes, I will stick with Sun Java and will pay attention to any security updates. BTW: in the meantime I had removed Sun Java and reinstalled openjdk with the apparmor profile set to complain mode - and the old problem was there again :sad: 

Back to Sun Java ;)

---

