---
title: "MATLAB in wine"
date: 2008-10-29
forum: Wine
---

### Post by thatcrazylankyguy on 2008-10-29
For a engineering class at a community college i have to run MATLAB. I installed it on my laptop w/ ubuntu and wine (i installed wine from the add/remove programs in ubuntu, i'm not sure what version it is). It hasn't really been running very well. Whenever i open an m-file i can't see part of the txt in it and the progam exits randomly. I'm not sure what the problem is but if you have any advice it will help.

---

### Post by eldragon on 2008-10-29
there exists a native matlab version for linux, so no need of wine for it.

if you already got a license, just find how to get the same copy but built for linux, and apply your license. about how to do that. i wouldnt know :D
call matlab for support on the issue..

in the meantime, you could try octave, which is matlab's FOSS counterpart

---

### Post by cyfur01 on 2008-10-29
If you bought the Student Edition (2007a), the disk comes with PC, Mac and *nix editions on it, so you should be able to natively install it on Ubuntu (that's what I did).

Also, if you run Compiz Fusion, then you'll also need to [make a fix]("http://linuxinside.blogspot.com/2008/01/solution-for-compiz-matlab.html") for the *nix version.

---

### Post by ad_267 on 2008-10-29
Depending on what you're doing, Octave is mostly compatible with Matlab. And yes the Linux version of Matlab will work a lot better if you can get hold of it.

If this wasn't for a course I'd say just use Python with Scipy.

---

### Post by thatcrazylankyguy on 2008-11-04
Unfortunately i can't use Octave or anything besides MATLAB for the class i'm taking. Everything i turn in has to be done on MATLAB. I will look for a linux version of it, but i don't have alot of money to spend. The version i have now is an old version that the school gave me to use for this course.
I can get Crossover, they had a deal a little bit ago and i can get it for free. do you know if matlab will run well on that?

---

### Post by eldragon on 2008-11-04
> **thatcrazylankyguy said:**
> Unfortunately i can't use Octave or anything besides MATLAB for the class i'm taking. Everything i turn in has to be done on MATLAB. I will look for a linux version of it, but i don't have alot of money to spend. The version i have now is an old version that the school gave me to use for this course.
I can get Crossover, they had a deal a little bit ago and i can get it for free. do you know if matlab will run well on that?

if it runs on octave, matlab will read it. octave even reads .m files, so there you go. anyway, the best chance you got is to get a linux native version *ehem* somewhere.

---

### Post by Trap3d on 2008-11-04
the problem with getting a linux version is that it might not be read on windows linux has that thing with linux-ized progs sometimes ive had it with oppen office not shure why tough as i guess the windows version is the same for linux

---

### Post by ad_267 on 2008-11-04
> **Trap3d said:**
> the problem with getting a linux version is that it might not be read on windows linux has that thing with linux-ized progs sometimes ive had it with oppen office not shure why tough as i guess the windows version is the same for linux

There shouldn't be any problem with files made on linux being read in windows. The only thing I can think of is that text files in linux use \n for a newline, whereas notepad expects \r\n, but I think Matlab is a bit smarter. Honestly you shouldn't have any problems. I've done heaps of stuff in octave that needs to run in Matlab.

---

