---
title: "Wine Installation"
date: 2012-07-26
forum: Wine
---

### Post by abomb07 on 2012-07-26
Ok so I am trying to install Wine on my computer running Ubuntu 12.04. I did this command: *sudo add-apt-repository ppa:ubuntu-wine/ppa*

That works. Then I do [I]sudo apt-get update
[/I]That works also. But, then I do *sudo apt-get install wine1.5*

This is the message I get:
[I]E: Unable to locate package wine1.5
E: Couldn't find any package by regex 'wine1.5'

[/I]Help is greatly appreciated. Thank you for your time.

---

### Post by Bufeu on 2012-07-26
Try to add the PPA first:```
sudo add-apt-repository ppa:ubuntu-wine/ppa
``` Then,```
sudo apt-get update
sudo apt-get install wine1.5
```

---

### Post by sorooshubu on 2012-07-26
> **abomb07 said:**
> Ok so I am trying to install Wine on my computer running Ubuntu 12.04. I did this command: *sudo add-apt-repository ppa:ubuntu-wine/ppa*

That works. Then I do [I]sudo apt-get update
[/I]That works also. But, then I do *sudo apt-get install wine1.5*

This is the message I get:
[I]E: Unable to locate package wine1.5
E: Couldn't find any package by regex 'wine1.5'

[/I]Help is greatly appreciated. Thank you for your time.

I tested these steps, it worked for me.
I entered following commands.
sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update 
sudo apt-get install wine1.5

---

### Post by abomb07 on 2012-07-26
> **Bufeu said:**
> Try to add the PPA first:```
sudo add-apt-repository ppa:ubuntu-wine/ppa
``` Then,```
sudo apt-get update
sudo apt-get install wine1.5
```
Thats what I did.

---

### Post by abomb07 on 2012-07-26
> **sorooshubu said:**
> I tested these steps, it worked for me.
I entered following commands.
sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update 
sudo apt-get install wine1.5
Doesn't work. Do you think it matters that I am running the PowerPC version of ubuntu?

---

### Post by Bufeu on 2012-07-26
> **abomb07 said:**
> Doesn't work. Do you think it matters that I am running the PowerPC version of ubuntu?What does *lsb_release -a* say?

---

### Post by Toz on 2012-07-26
Moved to the Wine sub-forum.

---

### Post by abomb07 on 2012-07-26
> **Bufeu said:**
> What does *lsb_release -a* say?
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04 LTS
Release:    12.04
Codename:    precise

---

### Post by Bufeu on 2012-07-26
> **abomb07 said:**
> No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04 LTS
Release:    12.04
Codename:    preciseHmm... Try installing Wine 1.4 instead.```
sudo apt-get install wine1.4 --install-suggests
```

---

### Post by abomb07 on 2012-07-26
```
Package wine1.4 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'wine1.4' has no installation candidate

```

That is what I got...

---

### Post by Bufeu on 2012-07-26
> **abomb07 said:**
> ```
Package wine1.4 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'wine1.4' has no installation candidate

```That is what I got...Hmm... What does *uname -m -p* says?

---

### Post by abomb07 on 2012-07-26
> **Bufeu said:**
> Hmm... What does *uname -m -p* says?
```
ppc ppc

```

No joke that is all it said when I entered *uname -m -p.*

---

### Post by Bufeu on 2012-07-26
> **abomb07 said:**
> ```
ppc ppc

```No joke that is all it said when I entered *uname -m -p.*Are you running the 32-bit or 64-bit version?

---

### Post by abomb07 on 2012-07-26
> **Bufeu said:**
> Are you running the 32-bit or 64-bit version?
32 bit

---

### Post by Bufeu on 2012-07-26
> **abomb07 said:**
> 32 bitTry [compiling Wine from source]("http://www.winehq.org/docs/wineusr-guide/installing-wine-source/").

---

### Post by abomb07 on 2012-07-26
> **Bufeu said:**
> Try [compiling Wine from source]("http://www.winehq.org/docs/wineusr-guide/installing-wine-source/").
**WAY** to complicated. I got stuck on the first step...

---

### Post by thatguruguy on 2012-07-26
> **abomb07 said:**
> Do you think it matters that I am running the PowerPC version of ubuntu?

Actually, that is the issue according to [WineHQ FAQ]("http://wiki.winehq.org/FAQ#head-5804ec2bb090feaf81f572993444efd8ec2a8569"):
> **2.7.2. Can I use Wine on an older Mac without an Intel chip?**

 No, not  even in Linux. Older Macs used PowerPC processors are incompatible with  code compiled for x86 (Intel and AMD) processors, unless the code is run  under CPU emulation. Wine Is Not a (CPU) Emulator, nor does it include  one. The Darwine project, however, was an effort to do just that. 

Wine won't work for you, irrespective of whether you try to compile it yourself or not.

---

### Post by abomb07 on 2012-07-26
:(
Do you know any alternatives to Wine that work on ppc?

---

### Post by thatguruguy on 2012-07-26
Unfortunately, no. You'd have to find a way to emulate the x86 hardware, first. By the time you've done that, I'd think that the overhead of running both a hardware emulator and an OS emulator (I know, I know, Wine is not an emulator) would constitute so much overhead that any Windows-based program would run poorly, at best.

---

