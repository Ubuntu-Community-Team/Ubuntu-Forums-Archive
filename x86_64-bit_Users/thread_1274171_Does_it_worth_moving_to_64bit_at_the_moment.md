---
title: "Does it worth moving to 64bit at the moment?"
date: 2009-09-24
forum: x86 64-bit Users
---

### Post by Levo on 2009-09-24
This is the question: Does it worth moving to 64bit at the moment? What are the advantages and disadvantages? I found many about this, but all of them are pretty old. The new ubuntu is coming, so I want to know what to install!

---

### Post by HavocXphere on 2009-09-24
I'd say its 50/50. There aren't really any major problems with it, but the benefits are modest too. So I'd say go for it if you're interested.

The only area where I've run into issues is with Flash + browsers. Took a bit of time to sort out but nothing hectic. (The key insight there was that [64bit OS + 32bit Firefox] means you need 32bit Firefox plugins, not 64bit.

---

### Post by Levo on 2009-09-24
> **HavocXphere said:**
> I'd say its 50/50. There aren't really any major problems with it, but the benefits are modest too. So I'd say go for it if you're interested.

The only area where I've run into issues is with Flash + browsers. Took a bit of time to sort out but nothing hectic. (The key insight there was that [64bit OS + 32bit Firefox] means you need 32bit Firefox plugins, not 64bit.


I don't have any problems with Jaunty 32-bit, but I have an amd64 CPU. There aren't any speed or stability differences between these two?

---

### Post by Grenage on 2009-09-24
Personally I think so, little point dwelling in the past!

---

### Post by cybrsaylr on 2009-09-24
> **Levo said:**
> I don't have any problems with Jaunty 32-bit, but I have an amd64 CPU. There aren't any speed or stability differences between these two?

I'm running both.
32 bit on an old single core PC that can't run 64 bit and 64 bit is running on a newer dual core AMD laptop.

32 bit runs great on the old PC and 64 but runs great with no real problems on my laptop and appears a little more snappy.

Laptop boots up in less than a minute.

---

### Post by marshmallow1304 on 2009-09-24
If you have more than 3.5 GB of RAM, definitely 64-bit.  If not, it's a toss-up.

---

### Post by wrathican on 2009-09-24
I'm running 64bit as my main OS and it runs without any difficulties. I didn't even have any problems installing flash within Firefox (shock horror).

I currently run with 4GB of ram and wanted to take full advantage of that with the future in mind. I know you can use over 4GB of RAM in 32bit if you know what you're doing, but I thought 64bit would be less hassle when it comes to upgrading to more as and when I please.

In my opinion I would say yes, do it.

---

### Post by khelben1979 on 2009-09-24
> **Grenage said:**
> Personally I think so, little point dwelling in the past!

Agreed. 

If I had 64 bit hardware I would go for 64 bit software to fully take advantage of the hardware and get as much speed as possible.

---

### Post by Levo on 2009-09-24
If I need to run a 32bit application, will it work? Any issues?
And another question. I use wine to run uTorrent. Will it work too?
As far as I am concerned, the whole ubuntu repository is available for 64bit OS. If I'm wrong correct me.

---

### Post by khelben1979 on 2009-09-24
> **Levo said:**
> If I need to run a 32bit application, will it work? Any issues?

Since Ubuntu is based on Debian I believe you would find [this so called Unix tutorial]("http://www.unixtutorial.org/2008/03/install-32-bit-deb-packages-on-64-bit/") of interest.

---

### Post by Levo on 2009-09-24
> **khelben1979 said:**
> Since Ubuntu is based on Debian I believe you would find [this so called Unix tutorial]("http://www.unixtutorial.org/2008/03/install-32-bit-deb-packages-on-64-bit/") of interest.

What I ask is if the application itself will work, not how to install it.

---

### Post by khelben1979 on 2009-09-24
> **Levo said:**
> What I ask is if the application itself will work, not how to install it.

Yes, but the tutorial answers your question. It will work, but not without the necessary system libraries. I've worked on this myself last year.

---

### Post by QIII on 2009-09-24
Generally, 32 bit applications for Ubuntu from the repositories come with the 32 bit libraries required to run them.

If you have 64 bit architecture, I'd go that way.  64 bit architecture is the way the world is moving.

There are advantages to using 64 bit software in processing efficiencies.

There is also the memory issue.  You are generally limited to 4GB of memory (a little less actually, and less still if any of your hardware reserves memory) with a 32 bit system, although you can use PAE (Physical Address Extension) to address up to a theoretical limit of 64GB.  PAE has some drawbacks.  And I doubt you have a motherboard that will let you install that much.

If you are interested, a 64 bit system can address 16 exabytes of memory.  That's roughly 16 million 1TB drives...

---

### Post by Levo on 2009-09-24
OK, I will download the 64bit version of Karmic. But there are some "sticky" threads here, which say they are tutorials for 64-bit Java and Flash plugin. Doesn't they work out-of-the-box in 64bit?

PS: I have 2GB of memory. I think it is much more than enough for linux :D

---

### Post by QIII on 2009-09-24
Don't download Karmic yet.

It is an Alpha, which means it is in testing, is unstable and is not recommended for production or general use systems.

You will likely have a myriad of problems with it.

---

### Post by Levo on 2009-09-24
> **QIII said:**
> Don't download Karmic yet.

It is an Alpha, which means it is in testing, is unstable and is not recommended for production or general use systems.

You will likely have a myriad of problems with it.

Yes I know. I already test the 32bit version. I don't really care about the problems! I mainly use my Jaunty installation. What about flash and java?

---

### Post by khelben1979 on 2009-09-24
> **Levo said:**
> PS: I have 2GB of memory. I think it is much more than enough for linux :D

It generally depends on what you want to do. I'm on 1GB over here and my harddrive is constantly swapping. But sure, I've run Linux in graphical mode with 64 MB of RAM and it actually worked quite well, at the time..

---

### Post by QIII on 2009-09-24
> **Levo said:**
> What about flash and java?

Java (64 bit) is in the Karmic repositories (although I can't remember if it is Update 15 or 16.  I'm not at my Ubuntu machine.)

You can get 32 bit flash from the repositories, or you can get the 64 bit version from Adobe and CAREFULLY follow the instructions to install it

---

### Post by Levo on 2009-09-24
> **QIII said:**
> Java is in the Karmic repositories (although I can't remember if it is Update 15 or 16.  I'm not at my Ubuntu machine.)

You can get 32 bit flash from the repositories, or you can get the 64 bit version from Adobe and CAREFULLY follow the instructions to install it

Do you know why flash has problems with 64bit? Does this affect other programs? In 32bit jaunty the whole system hangs when a flash video is played!

---

### Post by NoaHall on 2009-09-24
If you follow the advice in my sig to install 64 bit flash, it will run much better than the 32 bit version.

---

### Post by Levo on 2009-09-25
Does anybody know anything about virtual machines? Will they work faster? (install 32bit guest in 64bit ubuntu)

---

### Post by wrathican on 2009-09-25
> **QIII said:**
> There is also the memory issue.  You are generally limited to 4GB of memory (a little less actually, and less still if any of your hardware reserves memory) with a 32 bit system, although you can use PAE (Physical Address Extension) to address up to a theoretical limit of 64GB.  PAE has some drawbacks.  And I doubt you have a motherboard that will let you install that much.

Ahh, that was the way of getting 4GB of RAM to work on 32bit. I couldn't for the life in me remember what it was..

And Levo:
Im running a few virtual machines in virtualbox on my x64 platform. I run: Vista (x86), Win7 (x86), Ubuntu Server 8.04 x86, Ubuntu 9.04 x64 without any problems in the slightest. All Withh Guest Additions and USB/Networking working

if you run 32bit host and want to test a 64bit guest, you wont be able to. so to run 64bit guest you need to have 64bit host. 32bit guests work fine on 64bit host. at least in my experience.

---

### Post by Levo on 2009-09-25
I'll give 64bit a try. I hope it will be better (faster, stable,...)

---

### Post by linuxape on 2009-09-29
I will be buying a new laptop soon, possibly a Lenovo T400 or Dell E6400 w/ 8GB RAM.  

Currently I am forced to keep WinXP on Virtualbox to run some legacy molecular-biology programs that act unstable on WINE.  My current IBM-T43p has 2GB RAM and after allocating 1GB to WinXP while running multiple apps (like Thunderbird, Skype, Firefox, OpenOffice etc) in Ubuntu8.10-32bit host things do tend to slow down.  So I was thinking more RAM should solve the problem...... only to find out 32bit can only handle upto 3.5GB (w/o PAE).  I don't want to mess with PAE and stuff.  

So my question is w/ 8GB RAM in 64bit environment has anyone noticed any perceivable improvement while running multiple apps and virtualbox with some version of windows?  Will it worth paying for the extra 4GB or so of RAM and installing 64bit Ubuntu (be it 8.10 or 9.10 due soon)?  Comments or ideas are welcome.

---

### Post by wrathican on 2009-09-30
i think 8GB might be a bit overkill! but possibly something nice to have!

I currently run a Windows Vista VM (with virtualbox) on 1.5GB of RAM (i have 4) without any problems. I only use it for Photoshop, which can be quite memory intensive at times. Vista has a minimum spec of 1GB to run. XP only need 512mb AFAIK.

the main resource problems are from the CPU, it can be quite CPU intensive as some points. Although I don't really have a good processor.

8GB would only really be beneficial in a server environment, if you planned on running multiple VM's all the time.

if i could afford it and my mobo supported it i would definitely have 8GB RAM. the more RAM the merrier.

---

### Post by Slim Odds on 2009-09-30
I'm not sure why everyone freaks out about 8G of RAM (if you look around you can get 8G for about $100US, which is on about $50US more than 4G).

In other words, if you're buying a new system, it's only an additional $50US to go with 8G. I don't think that's much when you factor in the cost of the motherboard, hard drives, etc.

I'm currently running a low end quad core CPU with 8G RAM and Ubuntu 8.10. It's fantastic. I'm also using RAID 0 to pep up the disk I/O.

---

