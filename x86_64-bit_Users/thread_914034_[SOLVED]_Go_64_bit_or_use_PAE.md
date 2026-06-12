---
title: "[SOLVED] Go 64 bit or use PAE?"
date: 2008-09-08
forum: x86 64-bit Users
---

### Post by omegga on 2008-09-08
I have a HP 8510p with 4 GB ram. And if I use a normal 32 bit OS it can only access 3 GB ram. I've searched about it and it seems I can do two things:
1) Enable PAE.
2) Install 64 bit version.

The main reason I would use 64 bit is to access all the ram properly. But on 64 bit all the programs use more memory.. so I wonder if this really would be an advantage. If 64bit programs would use 33% more memory it's basically useless to use the 64 bit OS (at least if you only look at the memory usage). So **question 1: how much more memory to 64bit programs use?** Would it be worth it to use 64 bit (if you ONLY look at memory usage).

I tested the live CD of the 64 bit version. Graphics card seem to work correctly, sound works, network card detected. So that seems to be good! **Question 2: What is the status of the drivers?** Is it good at detecting usb devices like camera's?

Or use PAE. I've read that there's a small performance hit because there's an added layer to calculate the physical address. And 32 bit programs won't "see" all the 4 GB right? **Question 3: With PAE only the kernel uses all the RAM, reducing the need to use the harddisk swap. Is this correct?** Is it hard to enable PAE? I read that you need to recompile the kernel? **Question 4: So you have to recompile it with PAE on everytime there's an update to the kernel?**

---

### Post by tuxxy on 2008-09-08
The main reason I would use 64 bit is to access all the ram properly. But on 64 bit all the programs use more memory.. so I wonder if this really would be an advantage. If 64bit programs would use 33% more memory it's basically useless to use the 64 bit OS (at least if you only look at the memory usage). So question 1: how much more memory to 64bit programs use? Would it be worth it to use 64 bit (if you ONLY look at memory usage).

**64-Bit will run fine on 4GB RAM and yes its worth it imo **


I tested the live CD of the 64 bit version. Graphics card seem to work correctly, sound works, network card detected. So that seems to be good! Question 2: What is the status of the drivers? Is it good at detecting usb devices like camera's?

**Yes, and its good that you got all them detected fine already **

Heres a link to the [64-Bit User-Group]("http://ubuntuforums.org/group.php?groupid=258") when you decide to take the plunge! :)

---

### Post by Kilz on 2008-09-08
> **omegga said:**
> But on 64 bit all the programs use more memory.. so I wonder if this really would be an advantage. If 64bit programs would use 33% more memory it's basically useless to use the 64 bit OS (at least if you only look at the memory usage).

Unused Ram is wasted ram. If its being used, its not being wasted. The 64bit processor does use more ram, so that the chip can use it.
On the other hand, if you install a 32bit operating system, the chip runs in 32bit mode, runs at half performance and wastes ram because it doesn't make good use of it. If you do find a way to make the 32bit mode use more ram, you imho will create a bottleneck because the 32bit chip can only process so much.

---

### Post by Jouke74 on 2008-09-09
With a Hardy install and normal use I am filling about 485 mb of RAM. 4 GB will be fine to run 64 bit. I really don't understand why you are complaining about programs using a bit more RAM while you have 4 GB to use :confused:

Anyway, you'll be fine as of course is mentioned earlier already.

---

### Post by insane_alien on 2008-09-09
64-bit has more advantages than being able to use your full 4GB efficiently.

it also allows apps to run faster due to access to the full 64-bit registers.

---

### Post by philinux on 2008-09-09
I dont get this memory stuff for 64 bit.

I fire up Hardy and open firefox and thunderbird. System monitor shows 384meg used out of 2gig. This sounds like normal to me.
I fire up google earth and it goes up to 500meg.

---

### Post by insane_alien on 2008-09-09
well, with 64-bit apps, the pointers are 64 bits long as opposed to 32 bits long in 32-bit apps. worst case scenario is that it doubles the memory taken up by the program. although in reality it only tends to be  less than 10% increase

---

### Post by omegga on 2008-10-06
Update: I'm now running the 64 bit version of Ubuntu for around 3 weeks and it's running fine. The programs I use most of the time work perfectly. Sometimes an "exotic" program is difficult to set up though, because there isn't a package for the 64 bit version. But I'm happy with it overall.

---

### Post by mihai.ile on 2008-10-07
You can always use a 32bit Ubuntu without the 1GB of SWAP.
Ubuntu 32bit can address 4GB, not 3GB.
The reason you see 3GB of ram is because Linux 32bit uses 3GB RAM + 1GB swap.
By not using swap you can't hibernate but youll have almost 4GB of ram available.
Almost because linux also uses some mb for other things like addressing various pci devices, etc...

---

### Post by Sef on 2008-10-07
> You can always use a 32bit Ubuntu without the 1GB of SWAP.
Ubuntu 32bit can address 4GB, not 3GB.
The reason you see 3GB of ram is because Linux 32bit uses 3GB RAM + 1GB swap.
By not using swap you can't hibernate but youll have almost 4GB of ram available.
Almost because linux also uses some mb for other things like addressing various pci devices, etc...

The op has 4 GB ram and 32-bit cannot see more than 3.2 gb ram.  As Kilz said, unused ram is wasted ram.

---

### Post by Yellow Pasque on 2008-10-07
> the chip runs in 32bit mode, runs at half performance
You should really read about 64-bit computer architecture and learn why this isn't true. We wouldn't want to spread misinformation now, would we? :P

---

### Post by jroper on 2008-11-05
In my particular use case, I was doing Java development, and the application I was developing ran in 4 concurrent JVMs, plus I had another JVM for my IDE.  Under 32 bit, it required just over 2GB of memory to run comfortably.  At 64 bit, it needed well over 3GB of memory, combine that with other applications like web browser, database, and the OS itself, and I found my machine was swapping constantly.  So I run 32 bit Linux with PAE on 4GB of RAM and have no problems, it's very performant.

---

### Post by jollo on 2008-11-14
> **jroper said:**
> ...  So I run 32 bit Linux with PAE on 4GB of RAM and have no problems, it's very performant.

Jroper, since I have a very similar use case (and have had problems with 64bit Ubuntu since my application uses Java3D for visualization and try getting Sun to support amd64 architectures!! :( ) I would be grateful if you could point me to a comprehensive how-to to get PAE working on my Ubuntu 8.10 32-bit.
 
Thanks in advance!

---

### Post by HipShot on 2008-11-15
> **mihai007 said:**
> You can always use a 32bit Ubuntu without the 1GB of SWAP.
Ubuntu 32bit can address 4GB, not 3GB.
The reason you see 3GB of ram is because Linux 32bit uses 3GB RAM + 1GB swap.
By not using swap you can't hibernate but youll have almost 4GB of ram available.
Almost because linux also uses some mb for other things like addressing various pci devices, etc...

Virtual memory is a function of the OS not the architecture.

32 bit recognizes 4gb of addressable namespace, not just ram. That includes all cache from all devices in your system. The back end of the address range is reserved for system devices, (video ram, cpu cache, drives, etc.).

That is where the limit is imposed. Whatever range is not reserved for the system devices is made available for addressing ram.

---

### Post by schettj on 2008-11-15
> **HipShot said:**
> Virtual memory is a function of the OS not the architecture.

32 bit recognizes 4gb of addressable namespace, not just ram. That includes all cache from all devices in your system. The back end of the address range is reserved for system devices, (video ram, cpu cache, drives, etc.).

That is where the limit is imposed. Whatever range is not reserved for the system devices is made available for addressing ram.

Man, this is silly.

If you run the SERVER kernel, you get PAE and full access to 4gb (less some trivial amount) ram in 32 bit mode. 
```

$ uname -a
Linux schettino.us 2.6.24-21-server #1 SMP Wed Oct 22 00:18:13 UTC 2008 i686 GNU/Linux
$ free -m
             total       used       free     shared    buffers     cached
Mem:          4054       3909        145          0        181       2099
-/+ buffers/cache:       1628       2426
Swap:         9656        295       9360

```

Just install the server kernel.

While there is some slight to significant (depending on the job mix) performance boost from going to 64bit, you need not do it just to gain access to the full 4gb ram. I'm sure someday we'll all be running 64bit and this will all seem quaint.

---

### Post by jollo on 2008-11-15
Ok, Skettj, this makes a whole lot of sense: install the server kernel, where PAE seems to be enabled by default, is an easy way to get PAE working. Just out of curiosity: is there any way of just enabling it without changing my kernel under the hood?

Thanks!

John

---

### Post by bodhi.zazen on 2008-11-15
> **jollo said:**
> Ok, Skettj, this makes a whole lot of sense: install the server kernel, where PAE seems to be enabled by default, is an easy way to get PAE working. Just out of curiosity: is there any way of just enabling it without changing my kernel under the hood?

Thanks!

John

You have basically 3 options :

1. Use a 64 bit kernel.

2. Use the 32 bit server kernel.

3. Compile your own 32 bit kernel.

I am sorry I do not have a link off the top of my head, but it is not difficult to compile your own kernel (and activate PAE support). There is information on how to do this on the Ubuntu forums, ubuntu wiki, and various blog sites (google will hit any number of them).

---

### Post by jollo on 2008-11-17
> **bodhi.zazen said:**
> You have basically 3 options :

1. Use a 64 bit kernel.

2. Use the 32 bit server kernel.

3. Compile your own 32 bit kernel.



Thanks a lot, very clear. Just a misgiving about running a 32bit server kernel on a machine intended to be a desktop: restricted modules (such as proprietary accelerated video drivers) will only be available for generic kernel versions (reasonable: servers do not need fancy 3D graphics). 

I totally agree with the "in a few years we will all be running 64 bit" argument: I just wish it was now.

One small step forward towards this end: Sun finally made Java3D 1.5.1 available for 64 bit Linux! :)

---

### Post by schettj on 2008-11-17
> **jollo said:**
> Thanks a lot, very clear. Just a misgiving about running a 32bit server kernel on a machine intended to be a desktop: restricted modules (such as proprietary accelerated video drivers) will only be available for generic kernel versions (reasonable: servers do not need fancy 3D graphics). 


I'm using EnvyNG for Nvidia graphics, works fine. Would also work for ATI.

If you're using one of those two, don't let that stop you. I prefer the server kernel, go figure ;) Running it on a desktop and a laptop machine with no issues. There really is no "desktop" or "server" kernel, it's just build options that are tweaked to favor one or the other's typical load. Machines are so fast these days there really is little you'd need to do to favor interactiveness, so on fast hardware (say, for example, 64bit dual core CPUs with lots of ram) you'll be hard pressed to notice the difference, let alone measure it ;)

---

### Post by Ingenium on 2008-11-26
I'm having an issue that's bizarre. I just upgraded from 2GB of RAM to 4GB on my Core Duo system and installed the server kernel. It boots fine, but the system still only sees 3.2GB of RAM. 

uname -a: 
```
Linux josh-laptop 2.6.24-21-server #1 SMP Wed Oct 22 00:18:13 UTC 2008 i686 GNU/Linux
```

free -m:
```
             total       used       free     shared    buffers     cached
Mem:          3288       1221       2067          0         49        563
-/+ buffers/cache:        608       2680
Swap:         2863          0       2863
```

The BIOS correctly reports 4048MB of RAM. 

dmesg output shows:
```
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 00000000000eee00 (reserved)
[    0.000000]  BIOS-e820: 00000000000eee00 - 00000000000ef000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000000ef000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cf790000 (usable)
[    0.000000]  BIOS-e820: 00000000cf790000 - 00000000d0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec20000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000feda0000 - 00000000fedc0000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000] 2423MB HIGHMEM available
[    0.000000] 896MB LOWMEM available.
```

There isn't anything in dmesg about issues with PAE, as it would give if the kernel doesn't support PAE.

Any ideas?

---

### Post by punkybouy on 2008-12-03
Some system boards will start reserving memory when enough has been installed.  Check your system board manual.

---

