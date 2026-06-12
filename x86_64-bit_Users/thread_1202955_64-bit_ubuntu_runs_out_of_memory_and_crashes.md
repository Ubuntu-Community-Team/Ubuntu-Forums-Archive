---
title: "64-bit ubuntu runs out of memory and crashes"
date: 2009-07-02
forum: x86 64-bit Users
---

### Post by Gatesgamer33 on 2009-07-02
On my laptop, when ever I load a 64 bit version of Ubuntu (any version) the memory usage will climb until it will run out and freeze. The strange thing is it only happens on 64-bit ubuntu. Does anyone know why?

---

### Post by 3Miro on 2009-07-03
How much memory do you have and how are you loading Ubuntu (i.e. CD flash drive or what).

What exactly is your CPU?

---

### Post by sanderj on 2009-07-03
How do you know your system is running out of memory? How have you discovered / analyzed that?

---

### Post by Gatesgamer33 on 2009-07-03
I have an Intel core 2 duo T5250 & 1Gb of Ram. I have loaded it from the Desktop and alternate install cds. I know that it runs out of memory, because I can watch the graph on the system monitor climb until it crashes. THANK YOU VERY MUCH FOR THE REPLY!

---

### Post by cariboo on 2009-07-04
Using the system monitor adds it's own overhead, that doesn't give a true reading of what is going on with the system. Two low overhead programs to check your ram usage and resource usage are free and top. To run either program open an Applications-->Accessories-->Termianl and for top type at the prompt:

```
top
```

and for free:

```
free -m
```

Could you run top and paste the output in your next post. Use the [noparse]```

```[/noparse] tags to make the out put easier to use.

As an aside, please don't yell in your posts.

---

### Post by mgranet on 2009-07-04
Also, using a 64 bit OS inherently uses more RAM. Because of the extra registers, the OS and all your programs will consume that much more RAM than a 32 bit setup. For example, my Kubuntu 9 x86 install is consuming about 375MB at idle. When I was running x64, I could expect it to idle at close to 650MB of RAM usage. Because of this, I personally would not recommend running x64 with less than 2GB RAM.

---

### Post by izizzle on 2009-07-04
You might want to try running memtest86 to see if there are any issues with your ram.

---

### Post by PmDematagoda on 2009-07-04
> **izizzle said:**
> You might want to try running memtest86 to see if there are any issues with your ram.

I don't think it's something wrong with the RAM since Ubuntu only crashes when it runs out of memory, the problem is most likely an application that is leaking memory.

---

### Post by Tanker Bob on 2009-07-05
You can use top to see which program is eating RAM. Execute top, then type 'F' to change the sort column, then 'N' to choose %MEM (your letter may vary, but I doubt it). Watch the display to see if any program's memory usage keeps increasing.

---

