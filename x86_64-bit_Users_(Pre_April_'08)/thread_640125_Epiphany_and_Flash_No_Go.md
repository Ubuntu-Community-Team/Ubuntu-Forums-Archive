---
title: "Epiphany and Flash No Go"
date: 2007-12-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by NickArgyle on 2007-12-13
I have flash working in both Galeon and FF, but I want to use Epiphany as my main browser. All I get is a blank white spot where flash should be. Any ideas?
Earlier I force installed 32bit epiphany, but I got a missing dependency error and the file it needed wasn't in the repos. Then my apt and dpkg system got messed up so I force removed it and reinstalled 64bit version. How can I get flash working in 64bit Epiphany? Gnash doesnt play youtube or google video so it is out of the question.

---

### Post by utUtu on 2007-12-13
> **NickArgyle said:**
> I have flash working in both Galeon and FF, but I want to use Epiphany as my main browser. All I get is a blank white spot where flash should be. Any ideas?
Earlier I force installed 32bit epiphany, but I got a missing dependency error and the file it needed wasn't in the repos. Then my apt and dpkg system got messed up so I force removed it and reinstalled 64bit version. How can I get flash working in 64bit Epiphany? Gnash doesnt play youtube or google video so it is out of the question.

Sorry I'm not familiar with Epiphany, but I'm guessing there must be some place where it looks for plugins.  Once you know where it is, go to that directory, and then just create links to all the files in /usr/lib/firefox/plugins.  Good luck.

---

### Post by fjgaude on 2007-12-14
Funny, I use both FF and Epiphany and have no trouble with Flash. It works in both browsers. I installed Flash when asked by Ubuntu if I wanted it. I did a clean install and simply went to sites that needed multimedia codecs and the like.

---

### Post by NickArgyle on 2007-12-14
> **utUtu said:**
> Sorry I'm not familiar with Epiphany, but I'm guessing there must be some place where it looks for plugins.  Once you know where it is, go to that directory, and then just create links to all the files in /usr/lib/firefox/plugins.  Good luck.
Well, I copied the flash so file to the Epiphany plugin directory, however it doesn't work because of the 64bit thing I think. The version of flash that I have is obviously 32bit and I am running 32bit firefox. However, I am confused as to why 64bit Galeon works with flash...

---

### Post by david_2001 on 2007-12-16
> **NickArgyle said:**
> Well, I copied the flash so file to the Epiphany plugin directory, however it doesn't work because of the 64bit thing I think. The version of flash that I have is obviously 32bit and I am running 32bit firefox. However, I am confused as to why 64bit Galeon works with flash...
I don't use Ubuntu at the moment but am running a 64-bit distribution with 64-bit Firefox and Epiphany, and 32-bit flash works just fine in both with nspluginwrapper.  As you seem to have a mixture of 32-bit and 64-bit browsers installed (why so many?) your best bet is probably going to be to rip everything out, clean up and start again, sticking to either all 32-bit or all 64-bit with nspluginwrapper next time around!!!  Personally, I would take the 64-bit route.

---

### Post by Kilz on 2007-12-16
> **david_2001 said:**
> I don't use Ubuntu at the moment but am running a 64-bit distribution with 64-bit Firefox and Epiphany, and 32-bit flash works just fine in both with nspluginwrapper.  As you seem to have a mixture of 32-bit and 64-bit browsers installed (why so many?) your best bet is probably going to be to rip everything out, clean up and start again, sticking to either all 32-bit or all 64-bit with nspluginwrapper next time around!!!  Personally, I would take the 64-bit route.

This is not so good advice from someone who may not understand what is going on. I would not recommend anyone following it. Removing everything to get one plugin working is a lot of extra needless work.
There are reasons to have both installed. One is that java isnt perfect in 64bit browsers.
If the orignal poster used [my howto or script ]("http://www.ubuntuforums.org/showthread.php?p=1174435")to install the 32bit browser , the 32bit and 64bit share no files or folders.
The 32bit and 64bit cant use the same files, but will not conflict. So even if they used another method it cant possibly be why 1 browser of 3 dose not have flash. If it were the reason 64bit Galeon would not work.

---

### Post by david_2001 on 2007-12-16
> **Kilz said:**
> This is not so good advice from someone who may not understand what is going on. I would not recommend anyone following it. Removing everything to get one plugin working is a lot of extra needless work.
I don't know but I expect that you meant "for someone" rather than "from someone".  Anyway, the stated problem was related to flash.  If you install ia32 firefox, i.e. not in a chroot, then it and its 32-bit plugins will be somewhere that 64-bit epiphany won't be looking and, in any event, won't work.  Hence the recommendation to start again and settle on just the one architecture.  This is keeping it simple and may even be a useful learning experience.

---

### Post by Kilz on 2007-12-16
> **david_2001 said:**
> I don't know but I expect that you meant "for someone" rather than "from someone".  Anyway, the stated problem was related to flash.  If you install ia32 firefox, i.e. not in a chroot, then it and its 32-bit plugins will be somewhere that 64-bit epiphany won't be looking and, in any event, won't work.  Hence the recommendation to start again and settle on just the one architecture.  This is keeping it simple and may even be a useful learning experience.

This is wrong thinking. Picking apart grammar will not help prove that your suggestion isnt a good one. I have been dealing with the this problem since Dapper Drake. I wrote the 32bit firefox howto and install script used since Dapper Drake.
The reasons your idea is not a good one.
1. 64bit Epiphany cant use 32bit plugins. 
2. Chroots are a huge waste of time when dealing with only a 32bit browser. They simply are not needed after Breezy.
3. Since the 32bit browser shares no files or directories (not even plugins) with 64bit Epiphany. It cant possibly effect the 64bit Epiphany using a 64bit plugin.
4. 64bit Galeon works.
5. There is no 64bit java plugin that works for everyone.

It would be better to simply symlink the working plugin that 64bit Galeon uses to the 64bit Epiphany plugin folder. Less work, no deleting.

---

### Post by schmolch on 2007-12-16
I have trouble with flash in epiphany as well.
It works when i reinstall flash but after every restart of epiphany its broken again.
So if i want to use flash i have to reinstall it, restart epiphany, and then it works.
This is with Gutsy64.

---

### Post by fjgaude on 2007-12-16
As best as I can tell things have been done that is not what Ubuntu 64-bit designers planned for. If we install the OS clean, then go to access sites that have multimedia we are asked if we wish to have the various items installed; if yes, then they are installed.

But if we go ahead and install using other means we are screwed.

---

### Post by Kilz on 2007-12-17
> **fjgaude said:**
> As best as I can tell things have been done that is not what Ubuntu 64-bit designers planned for. If we install the OS clean, then go to access sites that have multimedia we are asked if we wish to have the various items installed; if yes, then they are installed.

But if we go ahead and install using other means we are screwed.

IMHO is incorrect. One of Linux's great strengths is that it is customizable. You are not stuck in any situation with what developers say is the only way. Granted this requires knowledge. But there are install scripts created by knowledgeable people that can let even those that cant do it themselves get customize. Wiping out an install (or part of it)  to start over is a last resort commonly used in desperation by people who cant figure out what is wrong. Doing so may wipe out countless hours of customizing and may create a lot of work that could be avoided.

---

### Post by Kilz on 2007-12-17
> **schmolch said:**
> I have trouble with flash in epiphany as well.
It works when i reinstall flash but after every restart of epiphany its broken again.
So if i want to use flash i have to reinstall it, restart epiphany, and then it works.
This is with Gutsy64.

Please provide the results of 
```
ls -al /usr/lib/epiphany/2.20/plugins
```

---

### Post by fjgaude on 2007-12-17
> **Kilz said:**
> IMHO is incorrect. One of Linux's great strengths is that it is customizable. You are not stuck in any situation with what developers say is the only way. Granted this requires knowledge. But there are install scripts created by knowledgeable people that can let even those that cant do it themselves get customize. Wiping out an install (or part of it)  to start over is a last resort commonly used in desperation by people who cant figure out what is wrong. Doing so may wipe out countless hours of customizing and may create a lot of work that could be avoided.

Yes, all we have to do and know is where to get the scripts to do what has to be done. Thank God for knowledgeable people. <sigh>

---

### Post by Kilz on 2007-12-18
> **fjgaude said:**
> Yes, all we have to do and know is where to get the scripts to do what has to be done. Thank God for knowledgeable people. <sigh>

You can also try google and reading.

---

### Post by fjgaude on 2007-12-18
Okay, I gain knowledge by reading and Googling. Thanks, man, for the useful advise. <smile>

---

### Post by Kilz on 2007-12-18
> **fjgaude said:**
> Okay, I gain knowledge by reading and Googling. Thanks, man, for the useful advise. <smile>

No problem, always glad to point people to the place I myself got the information over the last year and a half.

---

