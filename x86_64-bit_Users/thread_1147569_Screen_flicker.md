---
title: "Screen flicker"
date: 2009-05-03
forum: x86 64-bit Users
---

### Post by Fir3chi3f on 2009-05-03
So far I'm loving 9.04 but every once in a while the screen will flicker a little usually when scrolling or opening another window. The graphics is ati x1200 which I'm guessing is the problem

I've tried installing the fglrx packages but that just broke X. Uninstalled packages with aptitude in recovery term.

Is there anything else I can try?

---

### Post by TheLastTimTam on 2009-05-04
I'm also having this problem - same card. Apparently this card isn't supported anymore or something?

---

### Post by jasonuscg on 2009-05-07
I'm also on 9.04 but I have an HD4850 and the screen flickers with any openGL program with compiz on. With metacity on instead of compiz it flickers with Wine.

Real fun, it make me want to smash fuzzy bunnies.

To turn off compiz easily I use 'Compiz Fusion Icon,' it is easily found in the package manager. But it is only a bandage on a wound and does not fix the problem.

---

### Post by Arup on 2009-05-07
I use the latest Catalyst from ATI site on my dual GPU 4850 and so far haven't noticed any flickering.

---

### Post by lightscribe on 2009-05-07
i have  same problem screen flickering alot and movie's just to slow to watch them so abit doggy i read somewhere that i need to try radeonHD drivers but i guess my ati radeon x 1200/1250 card not r600 gpu so didn't tried yet bcoz then i cant fix that black screen thingy x server terminal bcoz i dont have manuals for it:D/ 
i tried ati Catalyst drivers on my previuos version of 8.04 x64 ubuntu but it was rubbish too so didn't used ubuntu at all   and then it broke  again some how coudnt managed get rid of that black screan thingy so just want too ask you guys i know somebody knows how to get rid off that screencracking ui :confused:

---

### Post by clhsharky on 2009-05-07
I have SAPPHIRE X1650 card with Ubuntu open source ATI Radon driver in 9.04.and I don't have that problem.

---

### Post by Fir3chi3f on 2009-05-08
> **lightscribe said:**
> i have  same problem screen flickering alot and movie's just to slow to watch them so abit doggy i read somewhere that i need to try radeonHD drivers but i guess my ati radeon x 1200/1250 card not r600 gpu so didn't tried yet bcoz then i cant fix that black screen thingy x server terminal bcoz i dont have manuals for it:D/ 
i tried ati Catalyst drivers on my previuos version of 8.04 x64 ubuntu but it was rubbish too so didn't used ubuntu at all   and then it broke  again some how coudnt managed get rid of that black screan thingy so just want too ask you guys i know somebody knows how to get rid off that screencracking ui :confused:

If English is your native language please speak clearer

To fix the video this is what I did:

1) In the grub boot menu select the Recovery boot
2) Once it is finished booting first try the 'xfix' option and reboot to see if it worked.

If it did not (as in my case)
3) same as #1 except select 'root' and it will drop you to a root terminal
4) type in: ```
aptitude
```
5) under 'installed' ---> 'misc' you should see the restricted drivers that caused this problem (as in my case)
6) remove these packages*
7) reboot and if it still did not work- google other possibilities, try to keep up with this and other threads and last case- start your own thread to get help.
 
*I don't remember the exact keys that removes the packages I just know that once you select them to be removed you have to hit 'g' to tell it to do so.

---

