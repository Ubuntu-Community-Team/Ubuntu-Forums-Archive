---
title: "Memory Management options?"
date: 2007-05-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by BC Boy on 2007-05-27
Hullo, and welcome to my first post :popcorn:

I've always given serious thought to MS alternatives, ever since Win95 came out. At the time, being a poor high-school kid, getting my hands on a shiny new OS CD was rather out of the question. But somebody dropped a copy of OS/2 in my lap...And so started my calamitous adventure ;) Okay, OS/2 at that time wasn't that great, but when I came across a copy of OpenLinux with KDE, I was entranced. It ran on even my 386 (pentiums were out by then, and 16-bit was on its way to the golden circuit board in the sky) Best of all, I didn't pay for it, never had to register it, and every program I used was the same. After that computer died, I returned to the Windows world, until about a month ago.  I'm tired of buying programs, of filling out endless registrations, of companies asking for my personal information; I'm tired of supporting all those fat CEO's on my working-class salary. Enter: Ubuntu...

Ubuntu kicks @$$ compared to OpenLinux! Of course we are talking about the difference between a 16-bit OS and a 64-bit OS, but mostly the ease-of-use is what I like (but the rotating cube is sweet too :D ) No more make madness (almost), no more booting to text because you toasted the OS (well, mostly, stupid nvidia driver :p), just click a checkmark, hit 'apply' and your stuff is installed, no fuss. Now that's what I call an OS!

Anyway, before all the preamble, I wanted to know if there was some way I could manage the memory that Ubuntu uses, like MemTurbo for WinXP? I noticed that I'm using about double the RAM with Ubuntu at idle as I would in the same state in XP. Not that it matters that much, since I bought an extra GB before installing Ubuntu, but RAM is finite, and I'm kinda stingy there :p

Sorry for the big post...

---

### Post by BC Boy on 2007-05-27
shameless bump :)

---

### Post by david_2001 on 2007-05-27
I'm sure that a techie will be along shortly.  In the meantime, take a look at [http://cbbrowne.com/info/ramcompress.html](http://cbbrowne.com/info/ramcompress.html).

---

### Post by hardyn on 2007-05-27
This is a pretty common question... Linux handles ram differently...

linux will attempt to use all the ram, all the time to reduce disk paging.  ram is not freed unless another process will consume it, i believe this is thought to be more efficient.

---

### Post by jamesford on 2007-05-27
the way i think it works lets say u have 1 gig of ram and start firefox. firefox may only use lets say 60 mb, but is allocated 300 mb for example. firefox can then take ram from this allocated pool without disturbing any other process. all other apps do the same until all ram is used, then it will start taking allocated ram from other apps that isnt in use. i think

what u may be interested in is how often it will use swap instaed of ram. this is stolen from a website somewhere, dont remember which, ive got it in a text file
```

Swappiness
The default value for vm.swappiness is 60 in Ubuntu Feisty whic is a good default value but if you want to tweak the performance a little bit more you can change this value to a lower value to reduce the load of the swap. If you run the follwing command:
sysctl -q vm.swappiness
You will se that the value is set to 60. And by running:
sudo sysctl vm.swappiness=10
You will change the value from 60 to 10 which will make your system write to swap a lot less and I would recommend this to everyone that has 512 MB of memory or more. If you find that you have very little use of swap set the value to 0. This will not disable the swap but it will make your system write to the swap as little as possible and keep as much as possible in memory. This makes a huge improvement when switching between applications since they are now likely to be in physical ram instead of on the swap partition.

To set your value permanent you need to change the sysctl.conf file:
sudo gedit /etc/sysctl.conf
Add the line
vm.swappiness=10
To the end of the file. This way it will be set upon boot.

I've found that the value of 5 works very good for my use and I have 1 GB of memory.
```

---

### Post by ENN0 on 2007-05-27
I need help!

---

### Post by hardyn on 2007-05-27
care to elaborate?

---

