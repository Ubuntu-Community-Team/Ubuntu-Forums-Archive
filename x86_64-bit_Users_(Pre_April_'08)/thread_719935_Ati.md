---
title: "Ati"
date: 2008-03-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by hvacr on 2008-03-09
I just installed the ATI driver using envy. I have a Radeon 1800, all seems to be ok, but I cannot run the ATI catalyst control center. I get the following error

 "There was a problem initializing Catalyst Control Center Linux edition. It could be caused by the following. No ATI graphic driver is installed, or the ATI driver is not functioning properly."

I cannot seem to find any cure for this. Has anyone ran into this, or has been able to fix it?

Thanks

---

### Post by soxs on 2008-03-10
Plx post the output of:
```
glxinfo | grep direct
```
&
```
fglrxinfo
```
This will check if the ati/amd driver is installed correctty.

Which way did you install the ati drivers? Did you uild packages or did you run the (graphical) installer?

---

### Post by Jouke74 on 2008-03-10
If Envy installed the drivers without any problems (which I sincerely wonder about given the problems I faced during install) then just open a command prompt and run: 

sudo apt-get install ia32-libs
sudo aticonfig --initial 

At least this is what worked for me after having this problem.

Indeed fglrxinfo should produce the latest ATI=AMD driver otherwise this also wont work.

---

### Post by soxs on 2008-03-10
lol.. ok if this is your problem, you should read [http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu) and you should understand what is required to make your driver run smooth

---

### Post by hvacr on 2008-03-11
> **soxs said:**
> lol.. ok if this is your problem, you should read [http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu) and you should understand what is required to make your driver run smooth

Been there and have done that, still did not work. I have gone back to the restricted drivers, as I realize now that extended desktop is not supported in ubuntu with ati.

---

### Post by soxs on 2008-03-11
what do you mean with *extended desktop*? Compiz? Multidisplay usage?

---

### Post by hvacr on 2008-03-11
> **soxs said:**
> what do you mean with *extended desktop*? Compiz? Multidisplay usage?


  I use 2 displays. With the windows drivers you can set up the second display as extended.

---

### Post by Jouke74 on 2008-03-11
And that can be done with aticonfig under linux as well :) 
Just type aticonfig --help in a terminal to get you started.

Also amdcccle could work here, have not tried that.

---

### Post by hvacr on 2008-03-11
> **Jouke74 said:**
> And that can be done withonfig under linux as well :) 
Just type aticonfig --help in a terminal to get you started.

Also amdcccle could work here, have not tried that.

I see nothing in the aticonfig that refers to extended desktop. Only single, clone, and the different horizontal.

---

