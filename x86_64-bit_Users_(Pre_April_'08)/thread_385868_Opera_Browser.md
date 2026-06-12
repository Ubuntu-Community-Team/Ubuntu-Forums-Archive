---
title: "Opera Browser"
date: 2007-03-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by Graham1 on 2007-03-16
Is there a 64-bit version of Opera browser available? Add/Remove programs would not let me install the 32-bit version. Failing that, is it possible to allow Ubuntu to run 32-bit software?

:)

---

### Post by rajeev1204 on 2007-03-16
yes 

ubuntu is capable of running 32 bit software provided u have all the 32 bit libraries installed from the repos.

Iam running quake 4 which is 32 bit but it automatically links to the 32 bit libraries when running.

Also if u have a deb file , then using this command -sudo dpkg -i --force architecture filename  also installs the package but u may have to do a lot of work to link it to the proper libs .Also not all 32 bit debs have the necessary libs available in 64 bit

I couldnt get skype to run by force install cos it was missing a 32 bit library. So even though it installed , it wont run cos it missing a 32 bit library.Also linux32 should be installed before installing any 32 bit package . 

Typing 32 libs in search in synaptic lists the 32 bit libraries available for install.


regards

rajeev

---

### Post by Graham1 on 2007-03-16
Thanks rajeev :). I'll get those 32-bit libraries installed then. Will installing 32-bit software mess up the system or do they both run well together?

:)

---

### Post by rajeev1204 on 2007-03-16
Hi

the 32 bit software will not mess up ur system or the other way round . 

Yes , the force architecture method for installing debs could mess up a few things so avoid it ( Stay away from anything with force in it :)  ). As for other stuff , for example files with .tar and .sh extension they r safe .

The max damage they do is refuse to install LOL :) 


The recommended way to install anything is from the repos because it is tailor made for our versions. ( They r precompiled with certain libs or something like that )

regards

rajeev

---

### Post by Kilz on 2007-03-16
> **rajeev1204 said:**
> Hi

the 32 bit software will not mess up ur system or the other way round . 

Yes , the force architecture method for installing debs could mess up a few things so avoid it ( Stay away from anything with force in it :)  ). As for other stuff , for example files with .tar and .sh extension they r safe .



The only way that forcing something could mess up your system is if you are trying to install the 32bit and 64bit version of something. But say you are installing Wine, and dont have it already installed, you are not going to mess up anything. If anything it will messs up an application, not a system.
The reason is that when you force something it doesnt install libraries. You have to install them manualy. You would manualy install 32bit libraries to /lib32 or /usr/lib32 so tthat 32bit versions and 64bit versions (that are in /lib and /usr/lib) can reside on the same system.
I have been forcing 32bit aplications since I found out the Dapper beta could run 32bit applications (Breezy couldnt). I have yet to mess up a system doing it. If an application does mess up, itt is simple to reinstall it with apt/synaptic.

---

### Post by rajeev1204 on 2007-03-16
hmmm

---

