---
title: "cpu upgrading"
date: 2006-09-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by alijoe on 2006-09-14
I am going to upgrade my cpu. The new one will be amd64 x2. Will I have to do something with my system (I mean installing some extra packages like in case of Intel dual core cpu  - smp -when running 32 bits mode)?
Currently I am running 64 bits Dapper Drake on amd athlon64.

---

### Post by codejunkie on 2006-09-14
> **alijoe said:**
> I am going to upgrade my cpu. The new one will be amd64 x2. Will I have to do something with my system (I mean installing some extra packages like in case of Intel dual core cpu  - smp -when running 32 bits mode)?
Currently I am running 64 bits Dapper Drake on amd athlon64.

if you going to be using the same motherboard, the only thing you will have to do is install a kernel with smp support to make use of both cores, if your current kernel doesn't already have smp support built in but I'm thinking that the dapper 64bit kernel already has smp support built in, not sure though since it's been a while since I've used the 64bit version of dapper.

---

### Post by jespdj on 2006-09-14
Yes, the generic AMD64 kernel that comes with Dapper does have SMP support built-in. Try:
```
uname -a
```
to see if your kernel supports SMP.

SMP stands for Symmetric Multi Processing = support for more than one processor or core.

---

### Post by alijoe on 2006-09-14
Thank for your answers.
But it is my home computer and I write this question from work. I will try the command as soon as I come home.
I am a new one here in Ubuntu and I migrated from another distro afer being unable to install it on Asus F3F laptop. Ubuntu was the only one which recognized hardware perfectly except screen resolution which was easily solved by 915resolution package. The laptop has intel dual core cpu and by the  wiki I was recommended to install smp 686 kernel. As far as I remember only Intel cpus were mentioned in description of the package.
So I think you are right when you say that amd64 kernel supports multiprocessing and I will not have to install or do anything but changing cpu.

---

### Post by Kilz on 2006-09-14
> **alijoe said:**
> Thank for your answers.
But it is my home computer and I write this question from work. I will try the command as soon as I come home.
I am a new one here in Ubuntu and I migrated from another distro afer being unable to install it on Asus F3F laptop. Ubuntu was the only one which recognized hardware perfectly except screen resolution which was easily solved by 915resolution package. The laptop has intel dual core cpu and by the  wiki I was recommended to install smp 686 kernel. As far as I remember only Intel cpus were mentioned in description of the package.
So I think you are right when you say that amd64 kernel supports multiprocessing and I will not have to install or do anything but changing cpu.

686 isnt a 64bit kernel. You need a amd64bit kernal if you are running the amd64bit version. All amd64 kernels have smp so it doesnt matter what one you use.

---

### Post by alijoe on 2006-09-14
Yes, I know. It was installed on a laptop.
But there is 64 bits Dapper Drake on my desktop which contains Athlon 64.
And here is the answer to the question uname -a:
Linux xxxx-desktop 2.6.15-26-amd64-generic #1 SMP PREEMPT Thu Aug 3 02:52:35 UTC2006 x86_64 GNU/Linux
Everything is OK. Thank you for your help.

---

### Post by a-musing amazon on 2006-09-14
> **alijoe said:**
> I am going to upgrade my cpu. The new one will be amd64 x2. Will I have to do something with my system (I mean installing some extra packages like in case of Intel dual core cpu  - smp -when running 32 bits mode)?
Currently I am running 64 bits Dapper Drake on amd athlon64.

Check that your bios version can handle the relevant x2 processor - I know with mine (and its only about a year old) I would have to do a bios flash update for it to be recognised properly.

---

### Post by alijoe on 2006-09-15
Thanks for tip.
I have already checked it, my motherboard is MSI k8N Neo4 platinum, BIOS ver.1.90. I flashed it 6 months ago and it is still the latest BIOS.

---

