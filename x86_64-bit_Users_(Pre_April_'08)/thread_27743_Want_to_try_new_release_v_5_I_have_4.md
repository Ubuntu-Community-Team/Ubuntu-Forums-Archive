---
title: "Want to try new release v 5 I have 4"
date: 2005-04-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by rjz on 2005-04-17
I have sveral of version 4. I have downloaded the version 5 cd. Is there an upgrade path I can take or do I have to do a complete reinstall?

---

### Post by telmo on 2005-04-17
[QUOTE=rjz]I have sveral of version 4. I have downloaded the version 5 cd. Is there an upgrade path I can take or do I have to do a complete reinstall?[/QUOTE]

Your talking about Ubuntu distribution, right?
I would advise to backup everything you need and make a fresh install ;) It's the best way.

---

### Post by tonym on 2005-04-18
UBUNTU is based on Debian so you should never have to reinstall,  just upgrade from release to release.  See the Ubuntu 5.04 release page for instructions.

---

### Post by Psquared on 2005-04-18
Assuming someone wanted to do a fresh install of Hoary, what is the best way to backup data? For instance, I have information in Evolution like addresses, emails etc., plus all my documents. I didn't setup a separate partition for data - though in the future I will.

So how do I save all this stuff so I can use it in Hoary?

---

### Post by TravisNewman on 2005-04-18
nearly any application data will be saved in /home/yourusername/.programname

Evolution data will be in .evolution, etc etc. That's one of the great things about Linux in general-- backups are simple and effective. You could theoretically back up everyting in /home/yourusername and then restore it after reinstallation, and have everything the way it was before you formatted. I say theoretically, because occasionaly you'll have things that break due to missing applications.

---

### Post by FluffyElmo on 2005-04-18
I agree with tonym, I've upgraded 4 boxes now and it was quick, painless and successful each time. No need to reinstall and configure all my applications.

That said all the data you want should be in your home directory. Browse to your home folder and show hidden files (Ctrl-H) to see everything that is there. Evolution for instance stores its address and mail data in */home/username/.evolution/*. 

There will be exceptions though, so take your time and make sure you have everything you need.

---

### Post by syntax_error on 2005-04-18
> Originally Posted by **Psquared** 
Assuming someone wanted to do a fresh install of Hoary, what is the best way to backup data?  

If i was you, i would try partition image. It backups the whole partition in one click, and change it to image file, so if you got problem with hoary or you miss your old system you can change it back with one click too.  :smile:

---

