---
title: "Memory leak in 8.10?"
date: 2008-12-02
forum: x86 64-bit Users
---

### Post by Ilya Skorik on 2008-12-02
I use 8.10 with standart repos. Nvidia driver from ubuntu repos.

And now, after 12 hours of work there is used memory 2.5 of 2.9 Gb, and 300 mb of swap.

Five minutes ago pidgin was crashed. I have started firefox, openoffice, terminals, pidgin, banshee, eclipse.

```

nassaja@nassaja-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2764       2730         33          0          8        232
-/+ buffers/cache:       2489        274
Swap:         8142        211       7930
nassaja@nassaja-desktop:~$ 

```

Then I close ALL programs. Only one terminal was started:

```
nassaja@nassaja-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2764       1630       1133          0         12        **241**
-/+ buffers/cache:       1376       1387
Swap:         8142        143       7998
nassaja@nassaja-desktop:~$ 

```


What happens there? Where is memory? How I can check who eat it?

Please help me.

---

### Post by philinux on 2008-12-02
use the 

top

command

---

### Post by OrangeCrate on 2008-12-02
Linux manages memory differently. Here's a good read on what there's no free RAM...

> Traditional Unix tools like 'top' often report a surprisingly small amount of free memory after a system has been running for a while. For instance, after about 3 hours of uptime, the machine I'm writing this on reports under 60 MB of free memory, even though I have 512 MB of RAM on the system. Where does it all go?

[http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?sid=619cda6e4dae2a0651c474f9f5e4dfcf](http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?sid=619cda6e4dae2a0651c474f9f5e4dfcf)

---

### Post by Ilya Skorik on 2008-12-02
> **OrangeCrate said:**
> Linux manages memory differently. Here's a good read on what there's no free RAM...


I heard and read about this excuse. But after all here it is eaten **3**! Gigabytes. And in a swap around 300 MB!

And after that some programs, like pidgin start to take off! 

You think, that this is normal behaviour for the memory manager?

---

### Post by OrangeCrate on 2008-12-02
It doesn't matter whether you have 256 MB, or 4 GB of RAM, that's just how Linux works.

Here's mine, so you can compare to your "free -m" in your first post. Except that I have only 512 MB of RAM on this machine, do you see the similarity?

```
$ free -m
             total       used       free     shared    buffers     cached
Mem:           500        453         47          0         16        254
-/+ buffers/cache:        182        318
Swap:         1466          4       1462
```

---

### Post by Ilya Skorik on 2008-12-02
I understand all of this. But I can't understand only one thing, why such effect was not stay on 32 bits? 

From me, 32bits Ubuntu stably has been occupied approximately half of memory (1.5 Gb), with all buffers, cache, etc. And without swap.

Now my 64 bit ubuntu linux eat all memory, and in a swap hangs 300 mbytes. And after that, some applications like pidgin, firegox begin crashing.

I can't understand this.

---

### Post by OrangeCrate on 2008-12-02
Have you use the

```
top
```

command in a terminal to see what's using your resources?

Philinux suggested that earlier.

---

### Post by Ilya Skorik on 2008-12-08
I found, who eat my memory. This is Eclipse for x86_64. Next question - why.

---

### Post by lavinog on 2008-12-08
> **Ilya Skorik said:**
> I found, who eat my memory. This is Eclipse for x86_64. Next question - why.

If you start it and don't do anything, does it eat your memory?

I read another post recently about Eclipse using up all of their memory...maybe there is an issue.
[http://ubuntuforums.org/showpost.php?p=6314091&postcount=5](http://ubuntuforums.org/showpost.php?p=6314091&postcount=5)

---

### Post by Ilya Skorik on 2008-12-08
No, Eclise don't eat memory when I not use it. But when I use Eclipse my memory can go away in a 3-4 hours. May be this is java issue? I'm use sun-java-jre6.

---

### Post by lavinog on 2008-12-08
> **Ilya Skorik said:**
> No, Eclise don't eat memory when I not use it. But when I use Eclipse my memory can go away in a 3-4 hours. May be this is java issue? I'm use sun-java-jre6.

Maybe there is a setting. I don't use Eclipse, but many programs have settings like maximum undo steps. If so, try lowering the maximum # of undo steps.

A quick google search for eclipse memory hog seems to show that it is pretty common for eclipse to use alot of memory depending on how it is configured.

---

### Post by edm1 on 2008-12-08
> **OrangeCrate said:**
> It doesn't matter whether you have 256 MB, or 4 GB of RAM, that's just how Linux works.

I have 3 gigs of memory and have never seen it go above 800mb.

---

### Post by cacycleworks on 2008-12-09
2 G here...

```
$ free -m
             total       used       free     shared    buffers     cached
Mem:          2005       1989         16          0         62        196
-/+ buffers/cache:       1729        275
Swap:         5553        623       4929

$ top
top - 21:36:48 up 3 days, 22:37,  1 user,  load average: 0.08, 0.13, 0.10
Tasks: 135 total,   2 running, 133 sleeping,   0 stopped,   0 zombie
Cpu(s):  2.0%us,  0.0%sy,  0.0%ni, 98.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2053736k total,  2037644k used,    16092k free,    64372k buffers
Swap:  5686968k total,   638812k used,  5048156k free,   201216k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 5452 root      20   0  466m  65m 3232 S    2  3.3  51:15.81 Xorg
14683 chris     20   0  757m 291m  33m S    2 14.6   3:45.62 firefox
14720 chris     20   0  773m 264m  32m S    2 13.2   2:17.96 firefox
 9362 chris     20   0  170m  17m  11m S    1  0.9   0:18.32 konsole
 6155 haldaemo  20   0 41232 5024 3116 S    0  0.2   7:20.66 hald
 6835 chris     20   0  182m  19m  12m S    0  1.0  12:25.65 kicker
13840 chris     20   0  795m  37m  25m S    0  1.9  21:03.70 soffice.bin
    1 root      20   0  4020  616  536 S    0  0.0   0:01.64 init

```

:) Chris

---

### Post by tuvw610 on 2008-12-09
There are more info at the site twentyfifthnovember too, if you wanna have a look, visit it and learn from that [http://www.inwowgold.com](http://www.inwowgold.com). We are a world class [wow gold](http://www.inwowgold.com) store online. We supply [cheap wow gold](http://www.inwowgold.com), the cheapest wow gold to our loyal and reliable customers. You may **buy cheap wow gold** here. There is wow gold for sale; you can [buy wow gold](http://www.inwowgold.com) here. We have mass available stock of [world of warcraft gold](http://www.inwowgold.com) on most of the servers, so that we can do a really instant way of wow gold delivery. We know what our buyers need so we offer an instant way of cheap [wow power leveling](http://www.inwowgold.com/power-leveling/), the cheapest wow gold delivery.

---

