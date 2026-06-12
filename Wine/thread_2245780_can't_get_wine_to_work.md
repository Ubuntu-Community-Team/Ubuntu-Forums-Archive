---
title: "can't get wine to work"
date: 2014-09-26
forum: Wine
---

### Post by jcrdlasesssb on 2014-09-26
I can't seem to get wine to work the way it should.  I have Xubunutu 14.04.1.  I have two programs that require windows to run.  On Xubuntu 12.04 these two programs both run perfectly, without a glitch under wine.  But under wine on Xubuntu 14.04.1, they will run but with such bad problems that they are unusable.  What is the problem?  How do I fix it? Or will I have to stay with xubuntu 12.04 until I am done using these programs?  They are essential for my daughter and her speech therapy.

Bess

---

### Post by QIII on 2014-09-26
Moved to ***Wine***

---

### Post by kc1di on 2014-09-26
Hi jcrdlasesssb  and welcome to the Forums. 

Sorry your having problems with wine.  Most likely it's the version of wine that is causing the problems.  the version of wine in 12.04 was 1.4 and in 14.04 it's 1.6 
some programs don't run well in the newer wine version.  you can try install 1.4 and see if that fixes your problems.
in a terminal run the following commands, one at a time,  to replace 1.6 with 1.4  you may also wish to install playonlinux which is a front end for wine and lets you choose which version of wine to use with each program. 

```
sudo apt-get purge wine
sudo apt-get install wine1.4
```

good luck.

---

### Post by jcrdlasesssb on 2014-09-26
Dave, I tried what you suggested--it didn't work :(  I guess I will just have to stay with Xubuntu 12.04.  When I tried to install just 1.4, it wanted to reinstall 1.6 along with it.  And Play On Linux didn't give me a choice--it just gave me the choice of the system default, and I think the system is defaulting to 1.6.

---

### Post by kc1di on 2014-09-27
> **jcrdlasesssb said:**
> Dave, I tried what you suggested--it didn't work :(  I guess I will just have to stay with Xubuntu 12.04.  When I tried to install just 1.4, it wanted to reinstall 1.6 along with it.  And Play On Linux didn't give me a choice--it just gave me the choice of the system default, and I think the system is defaulting to 1.6.

That's strange because PlayonLinux on my machine allows me to change which version of wine I want it to use with each program I want to install. 
you select the version of wine to use from the tools tab, Mangage Wine version.  On mine it gives the choice of wine 1.7 all the way back to .9 or something like that.
1.4 is included.

---

### Post by Bhaskara_Rao on 2015-01-26
Hi,

Please let me know the names(if possible with links) of the Speech Therapy Applications you are using. I need it for my daughter too.

Thanks,
Bhaskar

> **jcrdlasesssb said:**
> I can't seem to get wine to work the way it should.  I have Xubunutu 14.04.1.  I have two programs that require windows to run.  On Xubuntu 12.04 these two programs both run perfectly, without a glitch under wine.  But under wine on Xubuntu 14.04.1, they will run but with such bad problems that they are unusable.  What is the problem?  How do I fix it? Or will I have to stay with xubuntu 12.04 until I am done using these programs?  They are essential for my daughter and her speech therapy.

Bess

---

### Post by joelfrese on 2015-02-12
I'm just confirming that WINE does not install on my Xubuntu 14.04.1. It complains that the package is broken but I didn't find a way to resolve it. I heard some complaints about this version (the 14 series altogether) and I think I'm going to have to make a distro switch or something until this all gets fixed. Skype, WINE (1.6 and 1.7 along with the version that comes from the basic repository) and Steam have some file conflicts. Unfortunately, that's not going to work for me. If there is a fix, let us know!

---

