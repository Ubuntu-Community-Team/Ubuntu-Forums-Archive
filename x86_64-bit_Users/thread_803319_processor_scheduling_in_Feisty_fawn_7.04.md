---
title: "processor scheduling in Feisty fawn 7.04"
date: 2008-05-22
forum: x86 64-bit Users
---

### Post by Extr3me on 2008-05-22
Hello all,

I have been using ubuntu 7.04 with kernel version 2.6.20-16-generic for around a year now and I have been pretty impressed with it. Apart from a few bugs with LessTif it has been pretty good going, but I am starting to get a bit annoyed with the processor scheduling.

Every so often it seems to think that it is OK to run two heavy load jobs on the same CPU!!!  This often forces me to pause or cancel one job until the other completes and is a bit of a pain in the a**e.

I should say that I am running ubuntu on a dual-Opteron (thats two single-core chips!) workstationa and I regard a heavy-load job as one which will consume an entire CPU's usage.

Does anyone know how to find a solution to Ubuntu doing this?  Any help would be handy, as it is not always appropriate for me to be cancelling and suspending jobs willy-nilly.

Cheers.

---

### Post by prshah on 2008-05-22
> **Extr3me said:**
> Hello all,

I have been using ubuntu 7.04 with kernel version 2.6.20-16-generic for around a year now and I have been pretty impressed with it. Apart from a few bugs with LessTif it has been pretty good going, but I am starting to get a bit annoyed with the processor scheduling.


There you go, a good reason to upgrade to Hardy; it uses a new scheduler called CFS (Completely fair scheduler).

Maybe it will clear up your problems?

---

### Post by Jouke74 on 2008-05-22
You can use the "schedutils" package from Feisty I guess. In here  is a tool "taskset" which you can use to assign a specific task to a specific CPU. 

See also : [http://ubuntuforums.org/showthread.php?t=521150&page=2](http://ubuntuforums.org/showthread.php?t=521150&page=2) 
(post 7 and comments in other posts)

I used it back then to assign XGL to core 1 and Compiz to core 2.

After the update to Gutsy the shedutils package did not exist anymore in the repros :( But Compiz worked a lot better :)

Simply use taskset -c (0 or 1) and then the command of the program you want to use on the command line.

---

### Post by Extr3me on 2008-05-22
I wish I could upgrade to Hardy, but as this is an office workstation, the IT guy has to approve. He always comes across a little funny when you ask him: 'I need to upgrade to the latest OS because the current one sucks'.

Installing the schedutils package seems like the best solution that involved the least amount of installing. That will allow me to manually force the CPU I want to execute on.

Thanks for the help guys!!  :):):)

---

