---
title: "smp kernel not working"
date: 2005-12-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by raheesom on 2005-12-07
My hardware is a dual Opteron.  The kernel I'm running is - (Breezy Badger) :-

raheesom@rahubuntu:~$ uname -a
Linux rahubuntu 2.6.12-9-amd64-generic #1 Mon Oct 10 13:27:39 BST 2005 x86_64 GNU/Linux

The generic kernel boots, the k8-smp kernel does not.   The console errors when booting the k8 kernel are too numerous for here and make very little sense to me!

vmlinuz-2.6.12-10-amd64-generic
vmlinuz-2.6.12-9-amd64-generic
vmlinuz-2.6.12-9-amd64-k8-smp

What are my options for trying to get smp to work?

Tnx
Rupert (rupert at heesom dot org dot uk).

---

### Post by pont on 2005-12-08
Im having the exact same problem, But the generic  kernel also kernel panics for me , Giving me something about sync.

This first occored when I upgraded my kernel in the i386 ubuntu pre-release.

It seems that no kernel, 64 or non 64 does not allow my computer to run currently.

Windows works ok :P~

---

### Post by ytene on 2005-12-18
Hi,

I can report exactly the same problem that you have seen. I can run a uni-processor kernel perfectly on a home-build machine based on a Tyan Thunder K8W with 2 x Opteron 250's, but the moment I download and try and boot from the SMP kernel I get errors everywhere.

I've been trawling around looking for fixes and actually found entries here that suggest possible solutions. This certainly seems to be a core ubuntu bug...

Here's what I found so far :-

[http://ubuntuforums.org/archive/index.php/t-76852.html](http://ubuntuforums.org/archive/index.php/t-76852.html)

I still consider myself to be a complete Newbie with Linux, even though I've used it as my OS of choice for about 3-4 years now [since Mandrake 7.1] Recent convert to ubuntu. I think I'm going to put a "sandbox" build down on my machine and try and compile my own kernel just to see if I can get it to work. 

Only thing is, I think I'll avoid bringing in the default source from kernel.org, since I don't know what patches get applied by the Debian or Ubuntu core maintainers. Instead I'm going to pull in the ubuntu AMD-64 uni-processor source and see if I can find how to tweak it for SMP operations, then compile that...

For fun, I might even try bringing in the 32-bit Intel image and see what happens if I try and run that as SMP. Should be possible for me to pull in the DVD iso quite quickly...

If I make any progress I'll report back.

---

### Post by ytene on 2005-12-20
Hi!

A further - and hopefully positive update for you. Last night I tried a fresh installation of 5.10 onto my "other" machine, and was able to get a stable SMP kernel up and working at the first attempt, with no tweaking required.

However, it is possible that this success came about as a result of being attempted on different hardware. The system that failed was :-

Tyan Thunder K8W
2 x Opteron 250s
4 x 1Gb Crucial PC 3200
XFX 6800 Ultra AGPx8 256Mb
2 x EIDE based DVD Drives [ROM & RW]
4 x SATA HDDs
1 x Adaptec PCI SCSI Adapter
1 x HP 36/72Gb DDS5 Tape

The system that worked was :-

Abit AV8
1 x Athlon64X2 4200
2 x 1Gb Crucial PC3200
XFX 6800 Ultra AGP 256Mb
2 x EIDE based DVD Drives [ROM & RW]
2 x SATA HDDs
1 x EIDE HDD

At this point in time I just don't have enough evidence to be able to state with clarity whether or not this new attempt will work if/when I try on the Opteron box. However, I'm pretty sure [90%+] that last night's successful attempt did pull in a different version of the SMP kernel than my first attempt - ie a different release.

Hopefully I will have some time this weekend to try the Opteron system and will post the results here as well.

---

### Post by ytene on 2005-12-20
Rupert,

Sorry for lack of clarity earlier. One possibly useful piece of information... The kernel image that I finally got working was

linux-2.6.12-10-amd64-k8-smp

I hope that proves to be more helpful for you. Still not had the time to try this on my Thunder K8W Opteron box, but as soon as I do I'll post the results.

Best Regards,

C

---

### Post by oceanstar on 2005-12-23
[QUOTE=raheesom]My hardware is a dual Opteron.  The kernel I'm running is - (Breezy Badger) :-

raheesom@rahubuntu:~$ uname -a
Linux rahubuntu 2.6.12-9-amd64-generic #1 Mon Oct 10 13:27:39 BST 2005 x86_64 GNU/Linux

The generic kernel boots, the k8-smp kernel does not.   The console errors when booting the k8 kernel are too numerous for here and make very little sense to me!

vmlinuz-2.6.12-10-amd64-generic
vmlinuz-2.6.12-9-amd64-generic
vmlinuz-2.6.12-9-amd64-k8-smp

What are my options for trying to get smp to work?

Tnx
Rupert (rupert at heesom dot org dot uk).[/QUOTE]
i also have the same problem.The generic kernel boots, the k8-smp kernel does not.
who can help me ?

---

### Post by rplantz on 2005-12-23
Don't know if this is the problem, but when I first installed the k8 kernel, I used synaptic to install linux-image-x.x.xx-xx-amd64-k8 (where x.x.xx-xx is the version number). Didn't work. Had to go back to my generic kernel.

Then I learned that I had to install linux-amd64-k8, which is a meta package that automatically installs the latest version, **plus some other required files**.

If you think this might be your problem, I would probably uninstall the k8 image first. I don't know if that makes any difference, but I tend to be compulsive.

---

### Post by oceanstar on 2005-12-24
i aslo have the same question.
The smp kernel doesnt work well .
I don;n know if this kernel can work statable?

---

