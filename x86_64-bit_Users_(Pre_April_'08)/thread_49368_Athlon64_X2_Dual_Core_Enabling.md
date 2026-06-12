---
title: "Athlon64 X2 Dual Core Enabling"
date: 2005-07-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by jpoe on 2005-07-16
I was wondering if anything special needed to be done to setup the second core on an Athlon64 X2 system.

I installed the SMP kernels:

jpoe@samara:~$ uname -r
2.6.10-5-amd64-k8-smp

Originally I had problems with this (kernel panics) but this was solved by adding noapic to the boot command.   Everything seems to be working well, except that the System Monitor only shows one CPU, and top maxes at 100% CPU usage.

I haven't foud any other posts that suggest anything other than installing an SMP kernel needs to be done.  Am I forgetting anything?  Is my second core being used?

Thanks in advance for the help

---

### Post by joekr on 2005-07-16
Can you copy/paste the output you get from ```
sudo cat /proc/cpuinfo
```

My output shows (notice the bold)

> joe@amd64box ~ $ sudo cat /proc/cpuinfo
Password:
**processor       : 0**
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 7
model name      : AMD Athlon(tm) 64 Processor 4000+
stepping        : 10
cpu MHz         : 1085.017
cache size      : 1024 KB
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext lm 3dnowext 3dnow
bogomips        : 2150.40
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp


You should in fact see a second listing named ***processor       : 1*** (or similar) indicating a second physical core.  If you *do* see it, you can celebrate the fact that your X2 is installed properly, recognized by Ubuntu, and working it's dual core muscle for you :)

... if you *don't* see a second processor listing, report back (in any case I'd still like you to share the output of the command I first suggested) and we'll see if we can get your second core working.

As a follow-up question, have you updated your mobo's bios to the latest version?  Several manufacturers have had to dispatch bios upgrades in order to facilitate the X2's.

Good luck,

joe

---

### Post by jpoe on 2005-07-16
Hi Joe, Thanks for the quick reply!

I have an ASUS A8N-SLI Deluxe with revision 1011 which I believe is the most up-to-date non-beta bios, and I installed Windows XP 64bit long enough to run some benchmarks and everything seemed to show up perfectly there.  His is the output you requested:


processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 35
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 4400+
stepping        : 2
cpu MHz         : 2211.356
cache size      : 1024 KB
physical id     : 0
siblings        : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht pni syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm cmp_legacy
bogomips        : 4374.52
TLB size        : 1088 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp
cpu cores       : 2


I see that it only lists 1, but it does notice that 1 has dual cores.  Any thoughs?

Thanks again for the quick answer, I love this community... ;)

---

### Post by joekr on 2005-07-16
Looks like your all set  ;-)

---

### Post by jpoe on 2005-07-16
hmm, the only thing is that I was told the SMP kernel had to be installed to take advantage of the dual cores... but even with just the basic generic kernel the /proc/cpuinfo shows the same thing, 1 processor with dual cores...

---

### Post by jpoe on 2005-07-16
Also, if I run a CPU intensive single threaded program, ie:

int main(){
        long x,y;
        for(x = 0; x <  999; x++){
                for(y = 0; y < 9999999; y++);
        }
}

And I do top, I get that the program is running 100%.  And if I try a second, multithreaded version, like,

int main(){
        long x,y;
        fork();
        for(x = 0; x <  999; x++){
                for(y = 0; y < 9999999; y++);
        }
}

I get that each process is taking up 50% of the CPU cycles.

If this was using both processors, wouldn't the single thread only be able to consume 50% of the cpu cycles (assuming that Ubuntu is displaying the dual core as a single processor)...?

---

### Post by joekr on 2005-07-16
[QUOTE=jpoe]Also, if I run a CPU intensive single threaded program, ie:

int main(){
        long x,y;
        for(x = 0; x <  999; x++){
                for(y = 0; y < 9999999; y++);
        }
}

And I do top, I get that the program is running 100%.  And if I try a second, multithreaded version, like,

int main(){
        long x,y;
        fork();
        for(x = 0; x <  999; x++){
                for(y = 0; y < 9999999; y++);
        }
}

I get that each process is taking up 50% of the CPU cycles.

If this was using both processors, wouldn't the single thread only be able to consume 50% of the cpu cycles (assuming that Ubuntu is displaying the dual core as a single processor)...?[/QUOTE]

So long as you're running the smp kernel, you're doing fine ;)  Technically there are two cpus, so 100% usage refers to one core ;)

---

### Post by Flecko on 2005-08-05
Not to bring back up a dead topic, but I myself just built an Athlon x2 based system, and if your /cat/cpuinfo doesn't show 2 listings for cpus, you're not getting use of both cores.

The thing here is that support for the x2 was only added as of kernel 2.6.12 I believe...and even then, its a patch you have to apply. I'm just waiting until breezy I'd say, because my performance is fine, even if I'm only using half of my cpu.

I learned all this here: [http://forums.gentoo.org/viewtopic-t-360483.html](http://forums.gentoo.org/viewtopic-t-360483.html)

(even if gentoo is a ricer's distro)

But anyways, hope this helps,
-Flecko

---

### Post by jpoe on 2005-08-26
In case anyone is still having this problem, I did find a temporary solution until breezy that doesn't require recompiling a kernel.

About a week ago I was re-installing ubuntu and I accidentally chose the 686-smp kernel instead of the k7 kernel; and behold, both CPUs showed up and are fully functional!

I guess the tradeoff would be that you lose a few of the optimizations for the k7 architecture; but I would think doubling your CPUs would probably be more worthwhile.

Hope this helps...

James

---

### Post by qmerge on 2005-08-29
I have a dual core Athlon 64 x2 4200+ on a GA-K8NXP-SLI.
Ubuntu 386 boots, locks up on si sata
Ubuntu amd64 cannot boot.
Ubuntu 686 boots, locks up on si sata
Gentoo/amd64 kernel boots, was able to make raid 5 disk array.

I am booting from gentoo/amd64 kernel on ubuntu.
Only one cpu appears enabled.

---

### Post by torin on 2005-09-04
hope this can help you guys

[http://www.ubuntuforums.org/showthread.php?t=60099&page=1&pp=10&highlight=amd+x2](http://www.ubuntuforums.org/showthread.php?t=60099&page=1&pp=10&highlight=amd+x2)

[IMG]http://bewareofthis.info/this.png[/IMG]

---

