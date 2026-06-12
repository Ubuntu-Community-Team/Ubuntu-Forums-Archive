---
title: "[SOLVED] Firefox Java Plugin"
date: 2007-11-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by d1ss0nant on 2007-11-15
Hello - I can't seem to fix this problem...I am running Gutsy Gibbon 64 bit edition and the Java plugin for firefox just refuses to work.  I have tried to install the normal java plugin, the icedtea alternative, and yet another plugin i found on synaptic.  I have had no luck EVER - just grey boxes.  Does anyone have a proven method of getting this to work?  it's driving me nuts!  Thanks

---

### Post by Inxsible on 2007-11-15
Have you tried this?```
sudo aptitude install sun-java6-plugin
```

---

### Post by d1ss0nant on 2007-11-15
Yes, I installed this last night and it did not work (both from command line and synaptic).  I would be happy to give you more details (as far as what it said specifically), but I'm at work at the moment and I can't remote into my laptop.  I'll follow up tonight.  Thanks!

---

### Post by rsambuca on 2007-11-15
There is NO sun java plugin for 64 bit systems.  If you really need to have java in your browser, then you will have to use icedtea (which works with some sites), or install the 32bit browser, whch can then be used to run sun-java.

---

### Post by d1ss0nant on 2007-11-15
Ohhhh :(  I'm dissapointed to hear that...Well, there *is* a package on the java site ( [www.java.com](www.java.com) ) for a 64 bit plugin but it doesn't work...maybe this is just native to Ubuntu?  I really don't want to install 32 bit firefox, but maybe I will have to...is it possible to have 64 bit firefox and 32 bit firefox installed and running simultaneously?  Thanks for clearing it up

---

### Post by rsambuca on 2007-11-15
> **d1ss0nant said:**
> Ohhhh :(  I'm dissapointed to hear that...Well, there *is* a package on the java site ( [www.java.com](www.java.com) ) for a 64 bit plugin but it doesn't work...maybe this is just native to Ubuntu?  I really don't want to install 32 bit firefox, but maybe I will have to...is it possible to have 64 bit firefox and 32 bit firefox installed and running simultaneously?  Thanks for clearing it up

First, that is not a 64bit plugin for your web browser.  That is java to run on your system for programs written in java.  There is a big difference!

Second, yes, you can have a 32bit and 64bit version of Firefox living very happily together on one system.  I don't think you can have both open at the same time, though (although someone may have developed a workaround for this).  Kilz has written a script to automate the installation for you. 

The web browser is not an area where running 32 bit or 64 bit will affect performance, so don't worry about it.

You can follow the[ instructions on the first post of this thread]("http://www.ubuntuforums.org/showthread.php?t=202537&highlight=java") to set everything up.

---

### Post by davidstillson on 2007-11-15
I get the following error from sudo aptitude install sun-java6-plugin:

"The following packages have unmet dependencies:
  sun-java6-bin: Depends: unixodbc which is a virtual package.
                 Depends: libstdc++5 which is a virtual package.
  sun-java6-jre: Depends: java-common (>= 0.24) which is a virtual package.
Resolving dependencies...
Unable to resolve dependencies!  Giving up..."

any ideas?

---

### Post by rsambuca on 2007-11-15
> **davidstillson said:**
> I get the following error from sudo aptitude install sun-java6-plugin:

"The following packages have unmet dependencies:
  sun-java6-bin: Depends: unixodbc which is a virtual package.
                 Depends: libstdc++5 which is a virtual package.
  sun-java6-jre: Depends: java-common (>= 0.24) which is a virtual package.
Resolving dependencies...
Unable to resolve dependencies!  Giving up..."

any ideas?

Do you have all of your repositories enabled?  Go to System -> Administration -> Software Sources and make sure your Universe and Multiverse repos are checked.  Then try installing again.

---

### Post by davidstillson on 2007-11-15
they are both checked, and I also checked the other options there.

---

### Post by davidstillson on 2007-11-15
k, tried the command again, and now its downloading the software and the dependencies.

---

### Post by rsambuca on 2007-11-15
Have you tried installing from Synaptic?  Try installing the bin and jre files first.

---

### Post by davidstillson on 2007-11-15
Sweet, java is installed without a hitch, and I can access logmein machines via firefox now..  thanks a lot!!

---

### Post by rsambuca on 2007-11-15
> **davidstillson said:**
> Sweet, java is installed without a hitch, and I can access logmein machines via firefox now..  thanks a lot!!

Good stuff!

---

### Post by Inxsible on 2007-11-15
Mark your thread as solved. Thread Tools>>Mark thread as solved :D

---

### Post by rsambuca on 2007-11-15
> **Inxsible said:**
> Mark your thread as solved. Thread Tools>>Mark thread as solved :D

It isn't solved for the OP yet, since you gave incorrect advice earlier!

---

### Post by Inxsible on 2007-11-15
> **davidstillson said:**
> Sweet, java is installed without a hitch, and I can access logmein machines via firefox now..  thanks a lot!!

> **rsambuca said:**
> It isn't solved for the OP yet, since you gave incorrect advice earlier!
He did mention that java works  in firefox for him. 

As for the incorrect advice, I may have assumed that he was using a 32 bit firefox(which was presumptuous on my part)  but given that assumption, installing the sun java plugin works. correct?

---

### Post by rsambuca on 2007-11-15
> **Inxsible said:**
> He did mention that java works  in firefox for him. 

As for the incorrect advice, I may have assumed that he was using a 32 bit firefox(which was presumptuous on my part)  but given that assumption, installing the sun java plugin works. correct?

You should probably slow down a bit and read all of the information prior to dishing out hasty advice that doesn't work!  

1.  This is the 64bit forums.
2.  In the first post they say > I am running Gutsy Gibbon 64 bit edition....
3.  DavidStillson isn't the OP.

---

### Post by Inxsible on 2007-11-15
> **rsambuca said:**
> You should probably slow down a bit and read all of the information prior to dishing out hasty advice that doesn't work!  

1.  This is the 64bit forums.
2.  In the first post they say .
3.  DavidStillson isn't the OP.
1) I know
2) It still doesn't stop someone from using 32 bit firefox (and I already have agreed that I was presumptuous on that instance)
3) Clearly, my mistake 

:)

---

### Post by d1ss0nant on 2007-11-15
> **rsambuca said:**
> First, that is not a 64bit plugin for your web browser.  That is java to run on your system for programs written in java.  There is a big difference!

Second, yes, you can have a 32bit and 64bit version of Firefox living very happily together on one system.  I don't think you can have both open at the same time, though (although someone may have developed a workaround for this).  Kilz has written a script to automate the installation for you. 

The web browser is not an area where running 32 bit or 64 bit will affect performance, so don't worry about it.

You can follow the[ instructions on the first post of this thread]("http://www.ubuntuforums.org/showthread.php?t=202537&highlight=java") to set everything up.

Installing the 32 bit firefox with plugins (using that nifty script!) did the job for me - thank you to everyone who posted on this thread!  I really appreciate it.

---

### Post by rsambuca on 2007-11-15
Great stuff, but thank Kilz for the 'nifty script'!

---

