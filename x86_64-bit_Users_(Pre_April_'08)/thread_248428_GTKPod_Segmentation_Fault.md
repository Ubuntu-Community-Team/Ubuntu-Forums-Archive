---
title: "GTKPod Segmentation Fault"
date: 2006-09-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by thoffland on 2006-09-01
Does anyone know what this means or how I can fix it? 

I can launch GTKPod if the iPod is not connected, but then it doesn't do anything. If I try to launch it from a terminal with the iPod connected, I get "Segmentation Fault" error and it doesn't open. 

I cant even get it to work with Amarok, so I'm thinking I'm missing something. I did check all the dependancies of GTKPod and installed the libgpod... anything else I need to do?

I should add that I had it working on a previous install, but I had to re-install ubuntu due to some other problems I'd created. I've kept my sources.list at the default.

---

### Post by iamthemike on 2006-09-03
Hey, you're not alone. Is this a new ipod? I just bought a new ipod nano 1gb. My brother's ipod nano 2gb has the same firmware, buts its a little older. My dad's ipod video works fine with gtkpod, as does my brother's ipod nano 2gb. All ipods work fine with windows itunes, but mine alone will gets this segmentation fault when I try to use it (mounted) with gtkpod. I assume this is actually a libgpod problem. I've tried on two different linux pcs, and get the same results. the older ipods work just fine, and my new ipod gets a segmentation fault. Its driving me nuts, and NO ONE out there seems to have a fix that works. Searching forum after forum I can't find a solution. If you find one, please let me know.

---

### Post by iamthemike on 2006-09-03
Hey, if you are using version 0.99.x of gtkpod, trying reverting back to 0.88.x and see if it works for you. It worked for me.

---

### Post by thoffland on 2006-09-04
> **iamthemike said:**
> Hey, if you are using version 0.99.x of gtkpod, trying reverting back to 0.88.x and see if it works for you. It worked for me.

Thanks!! I'm out of town now but I'll try it when I get home. 

My iPod is a newer one I guess, it's a 2gig nano that I got for Christmas last year. The weird thing is that GTKPod worked on my last Ubuntu install... then I tinkered too much and had to re-install, now it doesn't work. I've tried re-installing libgpod from a terminal and it gives me the error that I need another lib of some kind, then that one has some other dependancy too but I cant seem to locate that one. 

My workaround was to share my music folder, map it to a Win2K machine and run Itunes that way. It took about 6 hours to sync 400 songs!!! I cant wait to try your idea... I hope it works!!

---

### Post by iamthemike on 2006-09-04
keep me posted.

---

### Post by jasnix on 2006-09-09
Awesome!  Thanks so much, downgrading to gtkpod-0.88.x worked perfectly!

---

### Post by thoffland on 2006-09-30
> **iamthemike said:**
> keep me posted.

Your the man! I just installed .88x and conected my Ipod and it connected but I cant get it to work, I even "restored" my ipod. Just cant seem to get music onto it this way. I'll keep trying. 

Edit: I'm running 64bit Ubuntu but if anyone else is looking for it, you can find it here: [http://tinyurl.com/nv94c](http://tinyurl.com/nv94c)

---

### Post by dbw on 2006-12-29
It seems this is a 64 bit problem?  It was also fixed for me by reverting to the .88 version - thanks for posting that link, thoffland.  Does anyone know how we tell the dists about this?

---

