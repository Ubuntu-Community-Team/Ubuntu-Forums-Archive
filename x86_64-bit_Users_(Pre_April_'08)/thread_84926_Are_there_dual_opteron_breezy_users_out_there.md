---
title: "Are there dual opteron breezy users out there?"
date: 2005-11-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by BIGtrouble77 on 2005-11-01
...Because I highly doubt it as none of the kernels that comes with breezy64 work.  I get kernel panics with every one.  To be fair I get the same issue with Fedora Core 4 and SuSe 10- and they both install the faulty kernel by default so I can't even boot into the system.  The standard ubuntu kernel does work fine, but it's not optimized and limited to one processor.

Anyway, there are a bunch of posts here with people in the same boat i'm in. No one can get dual opterons with the smp amd kernel working.  I wanna know if anyone has gotten it to work, and if so how?  

I may try and compile my own kernel as a last resort.  I was going to download Debian, but the AMD64 version is not official.  Is it stable and are the repositories decent? Should I just try hoary?  I'd like to stick to a debian based distro if possible.

---

### Post by horus on 2005-11-01
Working fine here thus far at least - the base breezy install went on without a glitch; I'm just layering other stuff on now.

Our hardware is a Celestica a2210 with two Opteron 244s, 4GB and two mirrored 160GB PATA drives FWIW.

root@tzut:~# uname -a
Linux tzut 2.6.12-9-amd64-generic #1 Mon Oct 10 13:27:39 BST 2005 x86_64 GNU/Linux

---

### Post by BIGtrouble77 on 2005-11-01
[QUOTE=horus]Working fine here thus far at least - the base breezy install went on without a glitch; I'm just layering other stuff on now.

Our hardware is a Celestica a2210 with two Opteron 244s, 4GB and two mirrored 160GB PATA drives FWIW.

root@tzut:~# uname -a
Linux tzut 2.6.12-9-amd64-generic #1 Mon Oct 10 13:27:39 BST 2005 x86_64 GNU/Linux[/QUOTE]
Interesting, so you're not using one of the 'SMP' labeled kernels?  Are you sure the system is running in smp?

---

### Post by horus on 2005-11-01
*Are you sure the system is running in smp?*

Good point, well made :)

Damn: I should have spotted that, as I had exactly the same problem with this (twin PIII) box when I first put Warty on it.

More later...

---

### Post by horus on 2005-11-01
Well, there's a thing...

Booting the SMP kernel locks the box up here too. Safe mode fine though. However, turning off idiot-luser-boot-mode seems to result in a working box:

root@tzut:~# uname -a
Linux tzut 2.6.12-9-amd64-k8-smp #1 SMP Mon Oct 10 13:18:18 BST 2005 x86_64 GNU/Linux

So, tentatively at least, I suggest taking "splash" out of your kernel boot options is worth a try. I took "quiet" out too, but that may not be necessary. I've no problem with this - boot-time eyecandy that hides infornation that I might want to see is a waste of time and programmer braincells anyhow - but it looks like a bug that wants fixing regardless.

---

### Post by BIGtrouble77 on 2005-11-01
[QUOTE=horus]Well, there's a thing...

Booting the SMP kernel locks the box up here too. Safe mode fine though. However, turning off idiot-luser-boot-mode seems to result in a working box:

root@tzut:~# uname -a
Linux tzut 2.6.12-9-amd64-k8-smp #1 SMP Mon Oct 10 13:18:18 BST 2005 x86_64 GNU/Linux

So, tentatively at least, I suggest taking "splash" out of your kernel boot options is worth a try. I took "quiet" out too, but that may not be necessary. I've no problem with this - boot-time eyecandy that hides infornation that I might want to see is a waste of time and programmer braincells anyhow - but it looks like a bug that wants fixing regardless.[/QUOTE]
cool, i'll have to give that a shot later today.  thanks.

---

### Post by BIGtrouble77 on 2005-11-01
Sadly, that didn't help.

I still get:
PANIC: early exception rip ffffffff8044341d error cr2 0
PANIC: early exception rip ffffffff8011812c error cr2 ffffffffff5fd023

---

### Post by BIGtrouble77 on 2005-11-03
Well, I tried debian and the smp kernel works fine.  I think I might reinstall breezy, then add the debian repository to get that kernel, then return to the breezy repository immediately afterwards.  Would that be a really bad thing to do?  

Only dowside I can think of is that I won't get updates for that kernel, but don't think we even get kernel updates anyway.

-BT

---

### Post by switi on 2005-11-04
Hi,

what about if you take the working kernel configuration of the Debian package and use it to compile your ubuntu kernel on your own? (I always do this)

Bye Switi

---

### Post by horus on 2005-11-04
Looks like I spoke too soon; the SMP kernel wouldn't boot this morning... I'm going to try a Debian kernel here too, until a new Ubuntu release emerges.

Sadly, my skills don't extend to kernel hacking even had I any spare tuits, which I don't...

---

### Post by Teroedni on 2005-11-04
Hmm wont it work with K7 smp kernel then?
I just love opteron i wish i had some to play with:)

---

### Post by BIGtrouble77 on 2005-11-04
[QUOTE=switi]Hi,

what about if you take the working kernel configuration of the Debian package and use it to compile your ubuntu kernel on your own? (I always do this)

Bye Switi[/QUOTE]
Can you elaborate a bit more on how to do this?  I have instructions for compling my own kernel, I just haven't tackled it yet.
EDIT: NM, I figured it out.  I may have to resort to this if the 2.6.14 kernel doesn't work

Another quick question hopefully someone can answer.  Even though I'm successfully using the smp kernel in Debian, how can I tell that both processors are actually being used in smp?  The system monitor in Gnome is only reporting one cpu.  So i'm not sure if it's a limitation of the monitor (possibly a misconfiguration?) or that it's simply not working in smp.
EDIT: I figured this one out too, ran mpstat

---

### Post by Kango_V on 2005-11-09
Using Breezy on Dual Opteron machine 248s.

Hardware:

IBM Intellistation A-Pro 6224-38G.
Dual Opteron 248s
2GB Ram
3x36GB Atlas 10K 4 drives
Linux 2.6.12-9-amd64-k8-smp (from normal breezy repo)
Nvidia driver works ok.
Dual 20" TFT screens (using Nvidia Twinview).

This setup works a treat.  Using Sun and IBM Java 5 AMD64 sdks with no problems.  Using the Blackdown 1.4.2 VM to get the plugin for firefox.  My maps now work on map24.co.uk -- sweet :).

Only thing that doesn't work is flash (no 64 bit).  oh well.

Everything else is peachy.

Daz

---

### Post by C_nemo on 2005-11-14
Im also using breezy on a dual Opteron setup, no problems here, but I have experienced bootup problems on other peoples dual Opteron machines YMMV. 

I have disabeled the boot splash (in fact it never came on), probably since I upgraded from Warty.

---

### Post by tobuntu on 2005-11-29
Linux ubuntu 2.6.12-10-amd64-k8-smp #1 SMP Fri Nov 18 12:20:27 UTC 2005 x86_64 GNU/Linux

I am using this kernel on a Dual Opteron box, only thing you may want to try it adding acpi=off to your /kernel string in grub, see if that helps

---

### Post by mikebern on 2005-11-29
Things work fine here. You must be running at least 2.12 kernel. I did have problem with hoary smp kernel until I upgraded to 2.12 kernel mysself

I am running Dual core Daul processor setup with 8gb of ram.


processor       : 3
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 33
model name      : Dual Core AMD Opteron(tm) Processor 270
stepping        : 2
cpu MHz         : 2009.263
cache size      : 1024 KB
physical id     : 1
siblings        : 2
core id         : 1
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov
pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm cmp_legacy
bogomips        : 4014.08
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp

I also have Dual processor setup with 4gb of ram.

processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 5
model name      : AMD Opteron(tm) Processor 248
stepping        : 10
cpu MHz         : 2191.989
cache size      : 1024 KB
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov
pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext lm 3dnowext 3dnow
bogomips        : 4374.52
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp

---

