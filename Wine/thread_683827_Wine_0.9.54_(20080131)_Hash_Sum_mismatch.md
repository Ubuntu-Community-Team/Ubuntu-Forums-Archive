---
title: "Wine 0.9.54 (20080131) Hash Sum mismatch"
date: 2008-01-31
forum: Wine
---

### Post by Resonance378 on 2008-01-31
SOLVED:   /var/lib/apt/lists/  and doing rm *wine* took care of the issue

Hi folks. I am attempting to update Wine to 0.9.54 from 0.9.53 and am getting the message:
```

Failed to fetch http://wine.budgetdedicated.com/apt/dists/gutsy/main/source/Sources.bz2  Hash Sum mismatch
Failed to fetch http://wine.budgetdedicated.com/apt/dists/gutsy/main/binary-i386/Packages.gz  Hash Sum mismatch
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

My S.W.A.G. is that something is wrong with the MD5 hash and the index.  Could someone explain to me what is going on and how to fix it?

---

### Post by Resonance378 on 2008-01-31
Perhaps my answer is here:  [https://blueprints.launchpad.net/ubuntu/+spec/apt-authentication-reliability](https://blueprints.launchpad.net/ubuntu/+spec/apt-authentication-reliability)

I'm not sure... any answers would be great.

---

### Post by Vadi on 2008-01-31
Slightly out of sync = I'd wait a bit then.

Or if I were you, just download the .deb from this page: [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

---

### Post by Resonance378 on 2008-02-01
Yeah it worked just fine on my home machine.  I'll have to try again tomorrow at work.  Learned a lot just trying to resolve the issue though.

---

### Post by Resonance378 on 2008-02-01
I am still getting the hash sum mismatch issues on my 2nd  machine.

---

### Post by Resonance378 on 2008-02-08
Can anyone help me resolve the Hash Sum Mismatch issues from the very 1st post of this thread?  I've tried and failed miserably so far.

---

### Post by Vadi on 2008-02-10
Try removing/adding the repositories back in?

Or you could just download the .debs.

---

### Post by Resonance378 on 2008-02-11
Downloading the .debs isn't exactly any sort of solution to an on going problem.

It's a work around or a cover-up at best, but thank you for the information.  

Working through this on my own I discovered this is not a Wine error so I'll rename the thread here and mark it SOLVED.

Even after doing all of the commands that apt recommends to resolve the issue the error listed in the 1st post still persisted.

APT has a nice list of repositories it stores @ /var/lib/apt/lists/

Going to the directory I listed: /var/lib/apt/lists/  and doing rm *wine* took care of the issue.

---

### Post by atryus28 on 2008-03-01
Thanks Resonance378, I seemed to have a different mismatch but removing it resolved the issue.  Thanks

---

### Post by Jasethemuss on 2008-04-19
Hi there, 

I'm pretty new to this game, but I managed to remove the wine docs by following the steps you suggested above i.e /var/lib/apt/lists/ and doing rm *wine*. Unfortunately that didn't fix the below problem in my case. 

Failed to fetch [http://wine.budgetdedicated.com/apt/dists/gutsy/main/source/Sources.bz2](http://wine.budgetdedicated.com/apt/dists/gutsy/main/source/Sources.bz2)  Hash Sum mismatch
Failed to fetch [http://wine.budgetdedicated.com/apt/dists/gutsy/main/binary-i386/Packages.gz](http://wine.budgetdedicated.com/apt/dists/gutsy/main/binary-i386/Packages.gz)  Hash Sum mismatch

Is there any more information that'd be helpful to list here to possibly illuminate what the issue might be? Until then it looks like I'm stuck with a very old version of wine. 

Thanks,

---

### Post by Jasethemuss on 2008-04-27
Problem solved, for me anyway. Just persevered and a couple of days later it seemed to work. Repository site must've been down or something.

---

