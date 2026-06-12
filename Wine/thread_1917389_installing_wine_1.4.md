---
title: "installing wine 1.4"
date: 2012-01-30
forum: Wine
---

### Post by JeremySchubert on 2012-01-30
Hi All,

On 11.10, I'm trying to install wine 1.4 according to the instructions at 
[http://www.linuxnov.com/wine-1-4-release-candidate-1-released-whats-new-download/](http://www.linuxnov.com/wine-1-4-release-candidate-1-released-whats-new-download/)
When I try to follow the instructions
> 
sudo apt-add-repository ppa:ubuntu-wine/ppa
sudo apt-get update
sudo apt-get install wine 1.4

I receive the following output/error message via the console.
Any suggestions of how to resolve these conflicts?

Thanks, Jeremy

```
The following packages have unmet dependencies:
 libboost-date-time1.46-dev : Conflicts: libboost-date-time1.42-dev but 1.42.0-4ubuntu2 is to be installed
 libboost-filesystem1.46-dev : Conflicts: libboost-filesystem1.42-dev but 1.42.0-4ubuntu2 is to be installed
 libboost-graph1.46-dev : Conflicts: libboost-graph1.42-dev but 1.42.0-4ubuntu2 is to be installed
 libboost-iostreams1.46-dev : Conflicts: libboost-iostreams1.42-dev but 1.42.0-4ubuntu2 is to be installed
 libboost-math1.46-dev : Conflicts: libboost-math1.42-dev but 1.42.0-4ubuntu2 is to be installed
 libboost-program-options1.46-dev : Conflicts: libboost-program-options1.42-dev but 1.42.0-4ubuntu2 is to be installed
 libboost-python1.46-dev : Conflicts: libboost-python1.42-dev but 1.42.0-4ubuntu2 is to be installed
 libboost-regex1.46-dev : Conflicts: libboost-regex1.42-dev but 1.42.0-4ubuntu2 is to be installed
 libboost-serialization1.46-dev : Conflicts: libboost-serialization1.42-dev but 1.42.0-4ubuntu2 is to be installed
 libboost-signals1.46-dev : Conflicts: libboost-signals1.42-dev but 1.42.0-4ubuntu2 is to be installed
 libboost-system1.46-dev : Conflicts: libboost-system1.42-dev but 1.42.0-4ubuntu2 is to be installed
 libboost-test1.46-dev : Conflicts: libboost-test1.42-dev but 1.42.0-4ubuntu2 is to be installed
 libboost-thread1.46-dev : Conflicts: libboost-thread1.42-dev but 1.42.0-4ubuntu2 is to be installed
 libboost-wave1.46-dev : Conflicts: libboost-wave1.42-dev but 1.42.0-4ubuntu2 is to be installed
 libboost1.46-dbg : Conflicts: libboost1.42-dbg but 1.42.0-4ubuntu2 is to be installed
 libboost1.46-dev : Conflicts: libboost1.42-dev but 1.42.0-4ubuntu2 is to be installed
 libboost1.46-doc : Conflicts: libboost1.42-doc but 1.42.0-4ubuntu2 is to be installed
E: Unable to correct problems, you have held broken packages.
```

---

### Post by Perfect Storm on 2012-01-30
Try remove libboost -dev(s) version 1.42 first.

But I'm baffled that requires libboost devs packages. Couldn't it be from previously package installation?

---

### Post by JeremySchubert on 2012-01-30
> Try remove libboost -dev(s) version 1.42 first.
To do this, should I just go to the synaptic packet manager and just mark anything nameed libboost -dev version 1.42 first for removal?

> But I'm baffled that requires libboost devs packages. Couldn't it be from previously package installation? 	
You mean a previously installed wine package?

Thanks, 
Jeremy

---

### Post by BC59 on 2012-01-30
I have the same problem. Looks like they don't have all the necessary packages in the repository yet.

---

### Post by JeremySchubert on 2012-01-30
I tried [B]
apt-get --purge remove libboost*
[/B]Didn't help.  I'm just going to reinstall Ubuntu and start fresh with wine 1.4.

Jeremy


> **JeremySchubert said:**
> To do this, should I just go to the synaptic packet manager and just mark anything nameed libboost -dev version 1.42 first for removal?


You mean a previously installed wine package?

Thanks, 
Jeremy

---

### Post by Soulcage on 2012-01-30
I'm not seeing wine1.4 in the ppa [https://launchpad.net/~ubuntu-wine/+archive/ppa]("https://launchpad.net/~ubuntu-wine/+archive/ppa")
Or is this a different one? That looks like your problem trying to install something with a space or doesn't exsist.

---

### Post by cwwilson721 on 2012-01-30
Amazing...NOBODY READ THE LINK IN THE FIRST POST:
> The official repository not updated yet. Stay tuned.
All the files are NOT IN THE REPO!

So, it doesn't work.

Don't try until it's updated

---

### Post by BC59 on 2012-01-30
> **cwwilson721 said:**
> Amazing...NOBODY READ THE LINK IN THE FIRST POST:

All the files are NOT IN THE REPO!

So, it doesn't work.

Don't try until it's updated

You should read post #4 to don't waist your time.

---

### Post by JeremySchubert on 2012-01-30
Got it, Wine 1.4 is not ready yet for Ubuntu 11.10!  I was only trying to upgrade because on the Wine Forum I was asking for help with a windoze program install someone else chastized me for not being up to date with wine ver 1.4.  At the risk of being flamed, anyone know when wine 1.4 will be ready for 11.10?
 
Thanks,
Jeremy

---

### Post by BC59 on 2012-01-31
Wine 1.4 is not yet ready. The procedure you tried was for installing the release candidate 1 (RC1) of Wine 1.4
About dates of release of the final product, I'm not sure, but they will do it during next weeks. But Wine it's not a fixed-date release.

---

### Post by cwwilson721 on 2012-01-31
You can always compile it yourself if you wish.

But RC releases just aren't stable enough for me.

---

### Post by Christian W on 2012-02-01
In the meantime you can also run

```
sudo apt-add-repository ppa:ubuntu-wine/ppa
sudo apt-get install wine1.3
```This will install the latest wine 1.3-beta, which is already labeled as wine 1.4-rc1.

---

### Post by BC59 on 2012-02-02
> **Christian W said:**
> In the meantime you can also run

```
sudo apt-add-repository ppa:ubuntu-wine/ppa
sudo apt-get install wine1.3
```This will install the latest wine 1.3-beta, which is already labeled as wine 1.4-rc1.

Exactly, if you check the Wine installed is indicated as 1.4 RC1, even if you install it as 1.3

---

### Post by bladerunnerfast on 2012-02-10
> **JeremySchubert said:**
> Hi All,

On 11.10, I'm trying to install wine 1.4 according to the instructions at 
[http://www.linuxnov.com/wine-1-4-release-candidate-1-released-whats-new-download/](http://www.linuxnov.com/wine-1-4-release-candidate-1-released-whats-new-download/)
When I try to follow the instructions


I receive the following output/error message via the console.
Any suggestions of how to resolve these conflicts?

Thanks, Jeremy

```
The following packages have unmet dependencies:
 libboost-date-time1.46-dev : Conflicts: libboost-date-time1.42-dev but 1.42.0-4ubuntu2 is to be installed
 libboost-filesystem1.46-dev : Conflicts: libboost-filesystem1.42-dev but 1.42.0-4ubuntu2 is to be installed
 libboost-graph1.46-dev : Conflicts: libboost-graph1.42-dev but 1.42.0-4ubuntu2 is to be installed
 libboost-iostreams1.46-dev : Conflicts: libboost-iostreams1.42-dev but 1.42.0-4ubuntu2 is to be installed
 libboost-math1.46-dev : Conflicts: libboost-math1.42-dev but 1.42.0-4ubuntu2 is to be installed
 libboost-program-options1.46-dev : Conflicts: libboost-program-options1.42-dev but 1.42.0-4ubuntu2 is to be installed
 libboost-python1.46-dev : Conflicts: libboost-python1.42-dev but 1.42.0-4ubuntu2 is to be installed
 libboost-regex1.46-dev : Conflicts: libboost-regex1.42-dev but 1.42.0-4ubuntu2 is to be installed
 libboost-serialization1.46-dev : Conflicts: libboost-serialization1.42-dev but 1.42.0-4ubuntu2 is to be installed
 libboost-signals1.46-dev : Conflicts: libboost-signals1.42-dev but 1.42.0-4ubuntu2 is to be installed
 libboost-system1.46-dev : Conflicts: libboost-system1.42-dev but 1.42.0-4ubuntu2 is to be installed
 libboost-test1.46-dev : Conflicts: libboost-test1.42-dev but 1.42.0-4ubuntu2 is to be installed
 libboost-thread1.46-dev : Conflicts: libboost-thread1.42-dev but 1.42.0-4ubuntu2 is to be installed
 libboost-wave1.46-dev : Conflicts: libboost-wave1.42-dev but 1.42.0-4ubuntu2 is to be installed
 libboost1.46-dbg : Conflicts: libboost1.42-dbg but 1.42.0-4ubuntu2 is to be installed
 libboost1.46-dev : Conflicts: libboost1.42-dev but 1.42.0-4ubuntu2 is to be installed
 libboost1.46-doc : Conflicts: libboost1.42-doc but 1.42.0-4ubuntu2 is to be installed
E: Unable to correct problems, you have held broken packages.
```
When I add in terminal sudo apt-add-repository ppa:ubuntu-wine/ppa I get apt-add-repository command not found

---

### Post by BC59 on 2012-02-10
> **bladerunnerfast said:**
> When I add in terminal sudo apt-add-repository ppa:ubuntu-wine/ppa I get apt-add-repository command not found

As I explained above there is no Wine 1.4 for the moment. It's the 1.3 beta with a new name. So installing the wine 1.3, the installed Wine is the Wine 1.4rc2

---

### Post by YokoZar on 2012-02-14
> **BC59 said:**
> As I explained above there is no Wine 1.4 for the moment. It's the 1.3 beta with a new name. So installing the wine 1.3, the installed Wine is the Wine 1.4rc2
Right, I did it this way in the PPAs because renaming the package requires users to manually accept the removal and replacement on upgrade.  For Oneiric, Natty, Maverick, and Lucid I am delaying that problem till 1.4 releases in full.


Meanwhile, in Precise, there are actual wine1.4 packages in the archive.  They work fully, however they're not yet available with apt-get -- the reason is that I am waiting on the archive admins to manually remove the old wine1.2 and wine1.3 packages, which wine1.4 provides replacements for.  Until then, the only way to get the wine1.4 as I've packaged it in Precise involves manual compilation (on multiple architectures even!).

I will probably put the precise pacakges in the PPA to deal with this when I update them to rc3.

Thanks.

---

### Post by dino99 on 2012-02-14
> **YokoZar said:**
> 

I will probably put the precise pacakges in the PPA to deal with this when I update them to rc3.

Thanks.

Waiting for RC3 too, does not understand why it takes so much time to be compiled after each release is done (usually on Saturday) and winetricks needs to be updated too to replace the oldish one.

---

### Post by gabriel b on 2012-02-16
> **YokoZar said:**
> Right, I did it this way in the PPAs because renaming the package requires users to manually accept the removal and replacement on upgrade.  For Oneiric, Natty, Maverick, and Lucid I am delaying that problem till 1.4 releases in full.


The Lucid packade is still 1.3.37, did you miss that one or is it intentional?

---

### Post by johnaaronrose on 2012-03-01
Same as previous post re Lucid.

---

### Post by sportfreak2020 on 2012-05-03
its may3rd and wine1.4 is still not available in the repo .. is it just me acting like a noob !!??:lolflag:

---

### Post by Soulcage on 2012-05-03
Theres not going to be one for natty only oneiric and pangolin.
(I think so anyways. I might be thinking of 1.5.)

---

