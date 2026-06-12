---
title: "[SOLVED] Adobe Flash won't Install on Hardy"
date: 2008-06-28
forum: x86 64-bit Users
---

### Post by slayr007 on 2008-06-28
Hey I have done everything that The Adobe website has told me to do and flash still won't install.  If it helps I tried using the tar.gz file type

If anyone knows how to fix this, it'd be much appreciated

---

### Post by Pjotr123 on 2008-06-28
Do this for 100 % multimedia support, including Adobe Flash Player:

Step 1:
[http://ubuntutip.googlepages.com/multimediaubuntustep1](http://ubuntutip.googlepages.com/multimediaubuntustep1)

Step 2:
[http://ubuntutip.googlepages.com/multimediaubuntustep2](http://ubuntutip.googlepages.com/multimediaubuntustep2)

And you're done.  :-)

---

### Post by aysiu on 2008-06-28
If you just want to install Flash, follow this tutorial:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

If you want other multimedia codecs, follow this one:
[http://www.psychocats.net/ubuntu/nonfree](http://www.psychocats.net/ubuntu/nonfree)

These tutorials are screenshot-heavy and emphasize point-and-click solutions, but will resort to the .tar.gz if necessary.

---

### Post by slayr007 on 2008-06-28
only one problem I already have something, that completely doesn't work, running flash

---

### Post by slayr007 on 2008-06-28
I followed everything and it doesn't do anything

---

### Post by aysiu on 2008-06-28
What's "something"? Let's get rid of it and start afresh.

---

### Post by aysiu on 2008-06-28
> **slayr007 said:**
> I followed everything and it doesn't do anything
You'll have to be more specific. What is "everything"? Start with one set of instructions and we'll go from there. Did Flash at least appear to install correctly? What do you see when you visit a Flash site?

"It doesn't work" doesn't really help diagnose the problem.

Are you using 64-bit Ubuntu, by the way?

---

### Post by slayr007 on 2008-06-28
no it didn't do any thing that that guide said it would

---

### Post by slayr007 on 2008-06-28
u know, come to think of it, i believe I am

---

### Post by aysiu on 2008-06-28
> **slayr007 said:**
> u know, come to think of it, i believe I am
[This](http://ubuntuforums.org/showthread.php?t=202537&highlight=64-bit+flash) may help, then. Good luck (I don't know much about 64-bit).

---

### Post by slayr007 on 2008-06-28
Nothing works

---

### Post by aysiu on 2008-06-28
Well, I'm going to move your thread to the 64-bit forum, and hopefully you can get some help there, but you've got to start being a bit more descriptive of your problem. "Nothing works" doesn't really help the people trying to help you.

---

### Post by markbuntu on 2008-06-28
Ok then, if you are running amd64 hardy you really need to do this:

[http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

to get flash working properly in firefox if you have the 64 hardy.

If you already have unpacked the libflashplayer.so from your download, you can move it to /usr/lib/flashplugin-nonfree where it belongs. If you have flash 10b move it there after you follow the directions in the link above.

---

### Post by impel on 2008-06-28
> **markbuntu said:**
> Ok then, if you are running amd64 hardy you really need to do this:

[http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

to get flash working properly in firefox if you have the 64 hardy.

If you already have unpacked the libflashplayer.so from your download, you can move it to /usr/lib/flashplugin-nonfree where it belongs. If you have flash 10b move it there after you follow the directions in the link above.

Thanks. This works!! Ive been searching for forever and this is the only way it installs.

---

### Post by stchman on 2008-06-30
> **slayr007 said:**
> Hey I have done everything that The Adobe website has told me to do and flash still won't install.  If it helps I tried using the tar.gz file type

If anyone knows how to fix this, it'd be much appreciated

Are you trying to get Flash 9 working?  Are you running Hardy?  If yes then just do this:

```
sudo apt-get install flashplugin-nonfree
```

---

### Post by slayr007 on 2008-07-02
alright I figured it out!
First go to System>Administration>Synaptic Package Manager, then uninstall all Flash files, then install Flashplugin-nonfree and libflash0c2 and libflash-mozplugin, then it should play.  If you get a gray rectangle w/ a play symbol in the middle then you probably didn't do the right initial package.

---

