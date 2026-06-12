---
title: "CS:S+Steam+Wine=Broked."
date: 2007-08-11
forum: Wine
---

### Post by nickajeglin on 2007-08-11
Well... Now I have everything up and running. Including CS:S. the problem is that it loads for a while, then the background screen turns sideways, then is cut in half by a diagonal stripe of agony, then the menu appears, but all of the characters are terribly corrupted, bearing no resemblance to the words that they're supposed to.
I'm using a rather crappy graphics card (nvidia gforce4 MX I believe) so maybe that's the problem?

oh, yeah, and when I quit, it puts me back onto the desktop at 800x600 res, and the buttons of steam (minimize, close, launch, etc.) no longer work.

---

### Post by dinux on 2007-08-11
do you have a kernel newer than 2.6.14? i'm asking this because there some known issues with that kernel or older

---

### Post by nickajeglin on 2007-08-11
What's the code to find that out?:redface:

---

### Post by Alex&amp;Linux on 2007-08-11
```
echo `uname -r`
```

Should display that info

```
ajn@ajn-desktop:~$ echo `uname -r`
2.6.20-16-generic

```

---

### Post by nickajeglin on 2007-08-11
That's the exaxt same numbers that I get.

---

### Post by Alex&amp;Linux on 2007-08-11
Not too much of a suprise there.
Regarding the issue at hand, I havent tried HL via wine, actually, I havent used wine at all but I  believe that the answers you seek may be found at  [www.winehq.org](www.winehq.org).

If you find out anything useful, try and conclude this thread with it, as others may have a similar problem!

---

### Post by nickajeglin on 2007-08-11
Actually [http://appdb.winehq.org/](http://appdb.winehq.org/) has been far more helpful to me than just winehq. They go through and test a bunch of apps and post the results. I've used it  a bunch since I switched over from windows. Unfortunately I haven't been able to find anyone else with this problem there or anywhere so far, so I posted here in hopes that someone would have the skills that I lack to fix it.

---

