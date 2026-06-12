---
title: "No &quot;ttf-mscorefonts-installer&quot; package"
date: 2014-11-14
forum: Wine
---

### Post by Alex Eagle on 2014-11-14
I installed Wine because I wanted to run Duck Builder, an old game I used to play on at school (it's dead cool! check it out someday).
Anyway, I got this warning:
```
Data files for some packages could not be downloaded

The following packages requested additional data downloads after package installation, but the data could not be downloaded or could not be processed.

ttf-mscorefonts-installer

This is a permanent failure that leaves these packages unusable on your system.  You may need to fix your Internet connection, then remove and reinstall the packages to fix this problem.
```

What to do? In what circumstances would it affect me, and how would I fix it, if it were a problem? Just a simple reisntall of Wine?

Thanks guys. :-)

---

### Post by slickymaster on 2014-11-14
Run the command below, to fix the error
```
sudo apt-get install --reinstall ttf-mscorefonts-installer
```

---

### Post by ajgreeny on 2014-11-14
You may need to accept the license for the core-fonts which is not a intuitive as it might be; when you see the window appear for the acceptance of license you must use tab to highlight the **OK** (or is it **YES**, I can't remember) then hit enter and the configuration will continue.

---

### Post by slickymaster on 2014-11-14
ajgreeny is right.

Sorry about forgetting to mention that. If you don't accept its license agreement you end up where you started, thus still getting the same error.

---

### Post by Alex Eagle on 2014-11-14
All set up. Don't know what effect it will have. I've worked out that they'd be useful if I was running MSWord, but I'm not so don't know if it'll be of any use anyway.

And it was OK, then YES, BTW. :-P

Thanks.

---

### Post by slickymaster on 2014-11-14
> **Alex_Eagle said:**
> All set up. Don't know what effect it will have. I've worked out that they'd be useful if I was running MSWord, but I'm not so don't know if it'll be of any use anyway.

And it was OK, then YES, BTW. :-P

Thanks.

Alex_Eagle, please [mark your thread as SOLVED]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads"), so other people searching the forums know that it provides a working solution for this type of problem.

---

### Post by Alex Eagle on 2014-11-15
Sorry, thought I'd done that! :-)

---

