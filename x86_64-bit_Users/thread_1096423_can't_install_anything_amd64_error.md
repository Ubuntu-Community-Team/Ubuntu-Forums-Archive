---
title: "can't install anything amd64 error"
date: 2009-03-14
forum: x86 64-bit Users
---

### Post by rosherau on 2009-03-14
I have 8.10 installed on a toshiba satellite notebook intell pentium dual core x2 1.8 gig cpu's.

Everytime I go to add/remove programs it comes up saying unable to install amd64. 
Even in Synaptic pkt manager things are greyed out.

However I do not have an amd64. 
When i go to system monitor it shows that I have intel pentium dual core i have 2 intel 1.86cpu. 
uname -a shows x86 64bit

Help!! how do I install anything, i have tryed to force
dkpg --force install with applicATIONS and even download fresh 64bit archetutre software and the same error occurrs.

Thankyou 4 your help
Roger

---

### Post by cariboo on 2009-03-14
You you don't have a 64-bit cpu, you wouldn't have been able to install a 64-bit version.

Have you tried updating the repositories? Just click the reload button, and see if that makes any difference.

Jim

---

### Post by rosherau on 2009-03-15
i dont have i386 archetecture.
Ive got intell x86 64.

But for some reason when ever i try to install anything in add/remove applications every single pice of software says.
Unable to install on (amd64).

Do i need to reinstall ubuntu under advanced settings and try to select which cpu i have ?
Or just install a i386 version and loose the peformance of my pc?

I have refreshed all reposorities 72 applications i believe were updated. still same problem.

I was reading somewhere that you could force install i386 archetecture into x86 but still it thinks i have an amd64 rather than an intell.

thx for the help, im realy keen ot get ubuntu to work.
Ive been trying to get into  linux for over 14 years with only minor success.

:)

---

### Post by lisati on 2009-03-15
This is just my opinion, but I think that part of the problem is not that the processor isn't 64-bit but that it's by Intel. I, too, have a Toshiba laptop (not the one I'm using right now) with an Intel dual-core processor, which is definitely 64-bit, but not by AMD.

---

### Post by rosherau on 2009-03-15
so do all x86 64bit processors come up as amd64 even if its an intell.

im going to load form the dvd and see which processor it believe i have.

also ill try to install again and see if there iss ana advanced ioption to install as a intell 64bit not amd64.
As all files believe i have an amd64 and can not install anything.

---

### Post by lisati on 2009-03-15
> **rosherau said:**
> so do all x86 64bit processors come up as amd64 even if its an intell.

im going to load form the dvd and see which processor it believe i have.

also ill try to install again and see if there iss ana advanced ioption to install as a intell 64bit not amd64.
As all files believe i have an amd64 and can not install anything.

[LIST=1]
[*]I highly doubt that Intel 64-bit proecessors show up as AMD64
[*]You would not be able to run 64-bit Ubuntu if you had a 32-bit machine
[/LIST]
A useful command for learning something about what's "under the hood" is ```
sudo dmidecode
```
Buried in the rather verbose output there will be a section on what kind of processor you have, which might help your research. On my Ubuntu machine it correctly identified it as a "Celeron" but said nothing about 32-bit or 64-bit. (My 64-bit laptop has only vista on it so I haven't had a chance to check what dmidecode has to say)

---

### Post by ameyer on 2009-03-15
> **lisati said:**
> [LIST=1]
[*]I highly doubt that Intel 64-bit proecessors show up as AMD64

As far as I can tell, that's not right.
[http://en.wikipedia.org/wiki/Amd64](http://en.wikipedia.org/wiki/Amd64)
> The x86-64 specification was designed by Advanced Micro Devices (AMD), who have since renamed it AMD64. The first family of processors to support this architecture, which AMD calls AMD64, was the AMD K8 family of processors. This was the first time any company other than Intel made significant additions to the IA-32 architecture. Intel was forced to follow suit, introducing modified NetBurst family processors, initially referred to as "IA-32e" or "EM64T" and now called Intel 64 and almost identical to AMD64

There's also Itanic... erm Itanium ( [http://en.wikipedia.org/wiki/IA64](http://en.wikipedia.org/wiki/IA64) ), but AFAIK there never was an Itanium laptop (or desktop).

---

### Post by lisati on 2009-03-15
Ah yes, I'd forgotten that the AMD folks had designed much of the spec.....

---

