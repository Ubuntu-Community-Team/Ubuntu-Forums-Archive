---
title: "AMD K6 Processor"
date: 2009-06-10
forum: x86 64-bit Users
---

### Post by Yogesh Iyer on 2009-06-10
Can I run Ubuntu 8.01 LTS in my AMD - K6 processor? How much RAM do I require?

---

### Post by Cheesemill on 2009-06-10
There is no such thing as Ubuntu 8.01 LTS

Do you mean 8.04 LTS or 8.10 (Non LTS)?

---

### Post by sanderj on 2009-06-10
> **Yogesh Iyer said:**
> Can I run Ubuntu 8.01 LTS in my AMD - K6 processor? How much RAM do I require?

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

### Post by Yogesh Iyer on 2009-06-15
> **sanderj said:**
> [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)
There is nothing mentioned about an AMD K6 processor in the system requirements. And say, can Ubuntu 9.04 run in that processor?

---

### Post by Yogesh Iyer on 2009-06-15
> **Cheesemill said:**
> There is no such thing as Ubuntu 8.01 LTS

Do you mean 8.04 LTS or 8.10 (Non LTS)?
ok then say ubuntu 9.04? can it run in an amd k6 processor?

---

### Post by zgornel on 2009-06-16
Theoretically yes. You need at least 256mb of ram. The problem is that the cpu is extremely old and weak for ubuntu.

---

### Post by sanderj on 2009-06-16
> **Yogesh Iyer said:**
> There is nothing mentioned about an AMD K6 processor in the system requirements.

... and nothting about a Core, a Core Duo, an i7, a Pentium, an Athlon, an Sempron, an Opteron, etc, etc, etc. Nevertheless, people are able to determine whether their CPU is OK:

The information on the mentioned URL says "700 MHz x86 processor" as "Recommended minimum requirements", so ask yourself two things
1) Is your AMD K6 at least 700 Mhz?
AND
2) Is your AMD K6 a x86 processor? See [http://en.wikipedia.org/wiki/AMD_K6](http://en.wikipedia.org/wiki/AMD_K6) and [http://en.wikipedia.org/wiki/K6-2](http://en.wikipedia.org/wiki/K6-2) , and search for "x86".

However, instead of asking question, you could just let your K6-system boot a Ubuntu-CD and see for yourself.

---

### Post by markharding557 on 2009-06-17
if i remember correctly the k6 series maxed at 550mhz so it probably will struggle with ubuntu but something like dam small linux could be a better option for such an old machine.
why is this in the 64bit forum?

---

### Post by jocko on 2009-06-18
> **markharding557 said:**
> if i remember correctly the k6 series maxed at 550mhz so it probably will struggle with ubuntu but something like dam small linux could be a better option for such an old machine.
why is this in the 64bit forum?

K6 maxed out at 300 MHz, K6-2 and K6-3 at 550 MHz, but of course none of them were 64 bit cpu's, so this thread definitely does not belong here...
The [bare minimum requirements]("https://help.ubuntu.com/community/Installation/SystemRequirements") for installing ubuntu (using an alternate cd) are:
> **Bare Minimum requirements**

 It should be possible to get Ubuntu running on a system with the following minimum hardware specification, although it is unlikely that the system would run well. You should use the *Alternate install CD* to attempt such an installation. 

[LIST]
[*]300 MHz x86 processor
[*]64 MB of system memory (RAM)
[*]At least 4 GB of disk space (for full installation and swap space)
[*]VGA graphics card capable of 640x480 resolution
[*]CD-ROM drive or network card
[/LIST]
So, it it is possible to install and run ubuntu with one of the better K6 processors as long as the rest of the requirements are met. But it will run very slowly, so I would suggest xfce (xubuntu) or something even lighter instead of gnome (ubuntu), and it's probably a good idea to start with a minimal install and just install absolutely essential packages instead of the entire xubuntu-desktop to save both disk space and memory usage.

---

### Post by zgornel on 2009-06-18
> **jocko said:**
> K6 maxed out at 300 MHz, K6-2 and K6-3 at 550 MHz, but of course none of them were 64 bit cpu's, so this thread definitely does not belong here...
The [bare minimum requirements]("https://help.ubuntu.com/community/Installation/SystemRequirements") for installing ubuntu (using an alternate cd) are:
So, it it is possible to install and run ubuntu with one of the better K6 processors as long as the rest of the requirements are met. But it will run very slowly, so I would suggest xfce (xubuntu) or something even lighter instead of gnome (ubuntu), and it's probably a good idea to start with a minimal install and just install absolutely essential packages instead of the entire xubuntu-desktop to save both disk space and memory usage.
I saw quit recently a Kubuntu 7.10 running on a Sun Dual UltraSparc II ~ 300Mhz and the speed and responsiveness were terrible. In this case, even xfce is too much for the K6. The best thing is to use fluxbox or some other minimalistic window manager or install some distro designed for old pc's ;) .

---

### Post by MonsterTrimble on 2009-07-13
Bigtime no. The K6 is the last of the non-686 based systems. You need an older kernel to run it properly. I would suggest Puppy or maybe something E17 based.

---

### Post by Slim Odds on 2009-07-13
> **zgornel said:**
> The problem is that the cpu is extremely old and weak for ubuntu.

Maybe, if it works out a little........ maybe then it'll be ok. ;)

---

