---
title: "how the heck can I enable x2 dual core in hoary"
date: 2005-08-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by torin on 2005-08-26
well I searched the forum and about all I could scrape up is this [http://www.ubuntuforums.org/showthread.php?t=49368&highlight=amd+x2](http://www.ubuntuforums.org/showthread.php?t=49368&highlight=amd+x2) but aparently I ride the short bus because I have no cule how to begin and that thread dosent give a real "step by step" set of instructions so if one of you kind folk could give me the play by play on what I need to do in order to get my x2 4200+ running on both cores that would be great, btw MOBO sees the chip as what it is so it seems to be a software issue.

Rig Spec:

2 Serial ATA, Western Digital Caviar SE WD2500JD
1 Asus A8N-SLI Premium
1 AMD Athlon 64 X2 4200+ Manchester Core
2 OCZ 2GB Platinum Dual Channel
1 MSI NX6600GT-TD128E
1 ASUS DVD Burner DRW-1608P
1 CoolMax 600W ATX12V v2.0

nothing overclocked yet...

---

### Post by varunus on 2005-08-26
It looks like you need the 2.6.12 kernel to enable X2 dual core support.  (On top of that, it needs to be patched.)

In other words, you'll have to wait for breezy unless you want to try compiling your own kernel...sorry.  You could try downloading the 2.6.12 kernel source, patching it, and then compiling it yourself.  Its not that hard; I remember being afraid to the first time I used linux, but once I did it, it was easy.

I'll look into the X2 patch; maybe I can give you a step by step.  Its not that hard to compile a kernel, you just have to type commands in the right order into the console and wait for 30 min or so.

---

### Post by torin on 2005-08-26
[QUOTE=varunus]It looks like you need the 2.6.12 kernel to enable X2 dual core support.  (On top of that, it needs to be patched.)

In other words, you'll have to wait for breezy unless you want to try compiling your own kernel...sorry.  You could try downloading the 2.6.12 kernel source, patching it, and then compiling it yourself.  Its not that hard; I remember being afraid to the first time I used linux, but once I did it, it was easy.

I'll look into the X2 patch; maybe I can give you a step by step.  Its not that hard to compile a kernel, you just have to type commands in the right order into the console and wait for 30 min or so.[/QUOTE]

I have been reading [http://www.ubuntuforums.org/showthread.php?t=56835&highlight=install+SMP+kernel](http://www.ubuntuforums.org/showthread.php?t=56835&highlight=install+SMP+kernel) but im not sure if it all is in sync with the 2.6.12 kernel and there wasnt anything mentioned about a patch but hey its not like you get to be a noob just once, btw thnx for the quick reply  ](*,)

---

### Post by torin on 2005-08-31
I guess not alot of people have this issue...

---

### Post by DancingSun on 2005-08-31
[QUOTE=torin]I guess not alot of people have this issue...[/QUOTE]
Heheh, no kidding, you're talking about dual core here...not a lot of us can afford it. ](*,)

---

### Post by torin on 2005-08-31
[QUOTE=DancingSun]Heheh, no kidding, you're talking about dual core here...not a lot of us can afford it. ](*,)[/QUOTE]

trust me I would love to claim this as my home box, but im oh the hook to solve this for another  ](*,)

---

### Post by DancingSun on 2005-08-31
[QUOTE=torin]trust me I would love to claim this as my home box, but im oh the hook to solve this for another  ](*,)[/QUOTE]
Ah...ok, I was about to beat you up for bragging with the X2 in front of us!

Anyway, I found this post, not exactly a solution per se, but if you're desperate:
[http://ubuntuforums.org/showpost.php?p=319875&postcount=9](http://ubuntuforums.org/showpost.php?p=319875&postcount=9)

This one sounds better:
[http://ubuntuforums.org/showthread.php?t=57828&highlight=dual+core](http://ubuntuforums.org/showthread.php?t=57828&highlight=dual+core)

---

### Post by torin on 2005-08-31
ok here is how it goes and keep in mind this is a n00b in amd x2 speaking, if you follow this - [http://www.ubuntuforums.org/showthread.php?t=56835](http://www.ubuntuforums.org/showthread.php?t=56835) - with this kernel - [http://kernel.org/pub/linux/kernel/v2.6/linux-2.6.13.tar.bz2](http://kernel.org/pub/linux/kernel/v2.6/linux-2.6.13.tar.bz2) - it works

```
cloned@befaka:~$ sudo cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 43
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
stepping        : 1
cpu MHz         : 2211.379
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm cmp_legacy
bogomips        : 4427.27
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp

processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 43
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
stepping        : 1
cpu MHz         : 2211.379
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm cmp_legacy
bogomips        : 4422.97
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp
```

I hope that helps, but it worked for me  ](*,)  \:D/  :grin:

Rig Spec:

2 Serial ATA, Western Digital Caviar SE WD2500JD
1 Asus A8N-SLI Premium
1 AMD Athlon 64 X2 4200+ Manchester Core
2 OCZ 2GB Platinum Dual Channel
1 MSI NX6600GT-TD128E
1 ASUS DVD Burner DRW-1608P
1 CoolMax 600W ATX12V v2.0

nothing overclocked yet...

all comments welcome

thnx guys

 \:D/

---

### Post by DancingSun on 2005-09-01
Did you try this to verify?
```
cat /proc/cpuinfo | grep processor
processor       : 0
processor       : 1
```

According to [this thread](http://ubuntuforums.org/showthread.php?t=49368&highlight=dual+core), it's possible that you didn't enable dual core correctly.

---

### Post by torin on 2005-09-01
[QUOTE=DancingSun]Did you try this to verify?
```
cat /proc/cpuinfo | grep processor
processor       : 0
processor       : 1
```

According to [this thread](http://ubuntuforums.org/showthread.php?t=49368&highlight=dual+core), it's possible that you didn't enable dual core correctly.[/QUOTE]

cloned@befaka:~$ cat /proc/cpuinfo | grep processor
processor       : 0
processor       : 1
cloned@befaka:~$

---

### Post by DancingSun on 2005-09-01
[QUOTE=torin]cloned@befaka:~$ cat /proc/cpuinfo | grep processor
processor       : 0
processor       : 1
cloned@befaka:~$[/QUOTE]
SWEET! =P~

---

### Post by torin on 2005-09-03
a sceen shot before I change anything, saturday and all... peskey work  :-? 

[IMG]http://bewareofthis.info/this.png[/IMG]

---

### Post by DancingSun on 2005-09-03
=P~ 
You bastard!

BTW, what theme is that?

---

### Post by torin on 2005-09-04
[QUOTE=DancingSun]=P~ 
You bastard!

BTW, what theme is that?[/QUOTE]

the theme is gorilla

---

