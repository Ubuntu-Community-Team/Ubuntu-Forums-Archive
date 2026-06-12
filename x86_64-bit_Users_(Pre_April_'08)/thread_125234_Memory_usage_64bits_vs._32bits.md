---
title: "Memory usage: 64bits vs. 32bits"
date: 2006-02-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by awi on 2006-02-03
I'm using Ubuntu on a AMD64, and most of the programs are available.
What I am very disappointed, is the memory usage of every graphic semi-heavy or heavy program I use, is bigger than it is on i386. I have not tested yet on this very mahcine, a i386 installation, (but I am just about to do it), but my former Desktop was an AMD Athlon 1800+, now I have a 2500+ (64bits), and everything runs slower, mainly because all the swapping that is made.
I found this interesting thread: 

[http://ubuntuforums.org/showthread.php?t=88717](http://ubuntuforums.org/showthread.php?t=88717)

and I can confirm that Azureus and Eclipse uses more memory on the same machine, with different implementation of Java (32 and 64 bits).
I also made this test between firefox and thunderbird (32 ann 64 bits), and I`ve got this results, opening and performing the same actions on both versions:

I use xosview as one of my obligated desktop monitor application, and from there, and to the top command, I can tell you that, suddenly, x86 is better supported or better ported (?), developed (?), I really don't know what is the real reason, but I'm really sad with the performance I'm getting.

Firefox and Thunderbird running with linux32 takes less memory.

```
Firefox32
Tasks:   1 total,   0 running,   1 sleeping,   0 stopped,   0 zombie
Cpu(s): 23.7% us,  2.4% sy, 63.4% ni,  8.7% id,  1.5% wa,  0.0% hi,  0.2% si
Mem:    425376k total,   419404k used,     5972k free,     1200k buffers
Swap:   987956k total,   117776k used,   870180k free,    72244k cached

  PID USER      PR  NI CODE DATA  RES SWAP  SHR  VIRT %CPU    TIME+  COMMAND
24853 afeltes   15   0   72 103m  79m 212m  22m  291m  0.0   1:09.52 firefox-bin


Firefox64
top - 13:26:55 up  2:49,  4 users,  load average: 1.81, 1.85, 1.74
Tasks:   1 total,   0 running,   1 sleeping,   0 stopped,   0 zombie
Cpu(s): 23.9% us,  2.4% sy, 63.5% ni,  8.5% id,  1.5% wa,  0.0% hi,  0.2% si
Mem:    425376k total,   419144k used,     6232k free,     1032k buffers
Swap:   987956k total,   121164k used,   866792k free,    76728k cached

  PID USER      PR  NI CODE DATA  RES SWAP  SHR  VIRT %CPU    TIME+  COMMAND
25625 afeltes   15   0   72 128m  78m 214m  20m  292m  0.0   0:30.04 firefox-bin

thunderbird32
Tasks:   1 total,   0 running,   1 sleeping,   0 stopped,   0 zombie
Cpu(s): 23.8% us,  2.4% sy, 63.7% ni,  8.4% id,  1.5% wa,  0.0% hi,  0.2% si
Mem:    425376k total,   359840k used,    65536k free,     1460k buffers
Swap:   987956k total,   121164k used,   866792k free,    76296k cached

  PID USER      PR  NI CODE DATA  RES SWAP  SHR  VIRT %CPU    TIME+  COMMAND
 8604 afeltes   15   0  11m 127m  41m 115m  16m  156m  0.0   0:35.11 thunderbird

thunderbird64
top - 13:30:07 up  2:52,  4 users,  load average: 1.37, 1.60, 1.66
Tasks:   1 total,   0 running,   1 sleeping,   0 stopped,   0 zombie
Cpu(s): 23.8% us,  2.4% sy, 63.7% ni,  8.3% id,  1.5% wa,  0.0% hi,  0.2% si
Mem:    425376k total,   405792k used,    19584k free,     3380k buffers
Swap:   987956k total,   105512k used,   882444k free,   114036k cached

  PID USER      PR  NI CODE DATA  RES SWAP  SHR  VIRT %CPU    TIME+  COMMAND
26301 afeltes   16   0   72 129m  48m 231m  21m  280m  0.0   0:04.89 mozilla-thunder

```

Anyone else have notice this? Any developer who can give some answers? Should not suppose to be 64bits applications faster than 32bits? Where is the bottle neck?
Thanks in advance for any information.

---

### Post by FluffyElmo on 2006-02-03
I remeber a discussion about this a while ago here, [http://ubuntuforums.org/showthread.php?t=43403]("http://ubuntuforums.org/showthread.php?t=43403")

In short, memory usage will go up with 64bits but performance should be faster. The relevant comment from roboguy is:

> The reason you are seeing a larger memory requirement for you 64 bit apps vs the 32 bit version of the same size will be largely because of pointer size. One of the most fundamental differences between 64 and 32 bit systems is their ability to address memory. 32 bit systems can address 2^32 locations in memory where as 64 bit systems can address 2^64 memory locations ( a much larger number ).

However, with this benifit also comes a cost. In order to be able to address that large a space, on a 64 bit system all pointers are 64 bits long, twice the size of their 32 cousins. Similarly on a 64 bit linux system a "long" in C is 64 bits compared to only 32 bits on a 32 bit system. The net effect of this is as you have seen, programs using more space in memory while running.

Another benefit of 64 bit systems is their ability to perform mathematical operations on floating point numbers in fewer cpu cycles than a 32 bit system. This is because the 64 bit system can load each of the 64 bit operands in one clock cycle due to it's 64 bit data bus and perform the operation in one additional cycle. A 32 bit system takes 2 cycles to load each operand, then 2 cycles to perform the operation. This makes a huge performance difference if you have an application that is very floating point intensive.

So in your case I'd guess that the amount of RAM is a bottleneck and adding more would show a nice performance boost, though something else may be going on. 

I have 1gb and notice no real problems running Azureus/Eclipse/Evolution/etc at the same time. I'll take a quick look at my memory usage when I get home to see if it matches what you're seeing.

---

### Post by rmjokers on 2006-02-03
The primary reason for upgrading from 32 to 64 bits is to get access to 64 bit registers and a larger memory address space.  In order to take advantage of this, things like memory pointers have to be 64 bits rather than 32 bits, meaning that a 64 bit program will ALWAYS be as large or larger than its 32 bit couterpart.  In other words, what you are seeing is expected.  As for whether or not one is faster than the other, that depends on optimizations in the hardware and the compiler.  However, your tests measured memory footprint, not speed.  Some speed measurements given the two setups above might be interesting to see though.

---

### Post by awi on 2006-02-03
Thank you both for the replies, yes that's true, the test was for the memory part, but when a lot of swapping is going on, it is not hard to tell which one runs faster, so far. :( 
I'll try to get more memory and see how things works out.

---

### Post by awi on 2006-02-27
I've finally got 1GB. 
Amazing difference, at normal usage, there is almost no swapping, and I finally can use my IDE (Eclipse) in a decent way \\:D/ 
Thank you all for the help.
Best Regards

---

