---
title: "Does Hoary enable the NX bit?"
date: 2005-07-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by dustyculler on 2005-07-22
Does anyone know if the NX bit for an amd64 cpu is enabled by default in Hoary?
Is there anyway to test that it's enabled?

I was reading [Ingo Molnar's original post to lkml announcing the NX kernel patch](http://people.redhat.com/mingo/nx-patches/QuickStart-NX.txt)  and he stated that if you applied the patch, it should say that NX is enabled during bootup.  He also gave a way to know if the kernel supported NX, which I tried and it does. 

Using Hoary, I tried 
```
dmesg | grep NX 
```
which didn't return anything.

I'm setting up a server and trying to lock it down as much as possible and wanted to make sure that NX is working.

Any ideas?

---

### Post by FluffyElmo on 2005-07-22
Are you running 32bit or 64bit Hoary? My understanding is that the 32bit kernels have to have NX enabled explicitly since they don't assume a amd64 processor is present. The 64bit kernel should support it out of the box since ~2.6.8 or so.

But I may be very wrong on this, if anyone knows better please correct me :)

---

### Post by dustyculler on 2005-07-22
Thanks for the reply.
I'm running in 32-bit mode since hoary for the amd64 doesn't have a driver for my raid controller and the i386 port does.

Any idea how to enable the NX bit if it's not on by default?

---

### Post by FluffyElmo on 2005-07-22
Short of building your own kernel, I don't know. The Ubuntu Hardened wiki may be of interest though, they seem to have a kernel using PaX in the Breezy repositories. I don't know their current status but for a server it may be well worth looking at for NX support and more security related patches...

[https://wiki.ubuntu.com/UbuntuHardened](https://wiki.ubuntu.com/UbuntuHardened)
[http://lists.ubuntu.com/mailman/listinfo/ubuntu-hardened](http://lists.ubuntu.com/mailman/listinfo/ubuntu-hardened)

---

### Post by kestasjk on 2005-08-07
[QUOTE=FluffyElmo]Short of building your own kernel, I don't know. The Ubuntu Hardened wiki may be of interest though, they seem to have a kernel using PaX in the Breezy repositories. I don't know their current status but for a server it may be well worth looking at for NX support and more security related patches...

[https://wiki.ubuntu.com/UbuntuHardened](https://wiki.ubuntu.com/UbuntuHardened)
[http://lists.ubuntu.com/mailman/listinfo/ubuntu-hardened](http://lists.ubuntu.com/mailman/listinfo/ubuntu-hardened)[/QUOTE]
 What about 32-bit NX? My Centrino M processor has it, and XP SP2 is using it, but I'm not sure how to get Ubuntu Hoary to use it.

---

### Post by Tamir on 2005-08-07
Drain just made packages of nx, hosed in my repository, check it out in the post "amd64 packages" :).

---

### Post by kao on 2005-08-07
[QUOTE=dustyculler]Thanks for the reply.
I'm running in 32-bit mode since hoary for the amd64 doesn't have a driver for my raid controller and the i386 port does.

Any idea how to enable the NX bit if it's not on by default?[/QUOTE]

afaik, NX bit is available on amd64 only.
PS `dmesg |gre NX` on my 64-bit hoary is empty too

---

### Post by kestasjk on 2005-08-08
[QUOTE=kao]afaik, NX bit is available on amd64 only.
PS `dmesg |gre NX` on my 64-bit hoary is empty too[/QUOTE]
NX is available on my Centrino also, it says so in the BIOS, and XP SP2 is using it.

---

### Post by kestasjk on 2005-08-08
[QUOTE=Tamir]Drain just made packages of nx, hosed in my repository, check it out in the post "amd64 packages" :).[/QUOTE]
But this isn't for amd64 :(

---

### Post by DancingSun on 2005-08-08
[QUOTE=Tamir]Drain just made packages of nx, hosed in my repository, check it out in the post "amd64 packages" :).[/QUOTE]
I think Tamir's confusing the NX (no-execute) protection built on AMD chips with NX the remote display server.  [-X

---

### Post by kestasjk on 2005-08-09
[QUOTE=DancingSun]I think Tamir's confusing the NX (no-execute) protection built on AMD chips with NX the remote display server.  [-X[/QUOTE]
 It's not only for AMD chips, I think it's called XD (execute-disable) on Intel chips, but it's identical (Like Intel's SSE and AMD's 3Dnow.).

---

### Post by kestasjk on 2005-08-10
[QUOTE=kestasjk]It's not only for AMD chips, I think it's called XD (execute-disable) on Intel chips, but it's identical (Like Intel's SSE and AMD's 3Dnow.).[/QUOTE]
 So any word on how you get NX/XD enabled in Ubuntu?

---

### Post by DancingSun on 2005-08-10
Didn't the thread starter said you have to patch the kernel?  To me, that means no easy way to enable NX.  Better wait for the Ubuntu folks to do it.

---

### Post by voidlogic on 2005-08-18
I belive that we are all pacthed already :smile: , see this exerpt from wikipedia :

Linux

Linux itself supports standard hardware NX, now in 32 bit mode on 64-bit CPUs via Ingo Molnar's NX enabler patch as well as in 64 bit mode on CPUs that support it (these include current 64-bit CPUs of AMD and future CPUs announced by Intel, Transmeta and VIA). Linus Torvalds has taken an interest in the NX patch, and believes it may be wise to have NX enabled by default; thus, it has been **merged in 2.6.8**. This is significant on 32-bit x86 kernels, which may run on both 32-bit x86 CPUs and 64-bit x86 compatible CPUs. A 32-bit x86 kernel would not normally expect the NX bit that an AMD64 or IA-64 supplies; the NX enabler patch assures that these kernels will attempt to use the NX bit if present.
As of this patch, **Linux fully utilizes the hardware NX bit in supporting CPUs from Intel, AMD, Transmeta and VIA**. The NX patch was released to the Linux kernel mailing list in June, 2004.
Non-execute functionality has also been present for other non-x86 processors supporting this functionality for many releases.

---

### Post by DancingSun on 2005-08-18
Now that's sweet!

---

