---
title: "Can I try a 2.6.25.1 kernel?"
date: 2008-08-17
forum: x86 64-bit Users
---

### Post by resqguy on 2008-08-17
I have an issue with my soundcard that is reported to be fixed in 2.6.25.1.  Since this is a new motherboard and my only OS I would like to test this while I'm inside the 30 day RMA period.

I've upgraded kernels in the past but wasn't sure how these new distributions were integrated.  Can I try this - rename current kernel, build new one, test, revert back if things don't work?

---

### Post by Kilz on 2008-08-17
> **resqguy said:**
> I have an issue with my soundcard that is reported to be fixed in 2.6.25.1.  Since this is a new motherboard and my only OS I would like to test this while I'm inside the 30 day RMA period.

I've upgraded kernels in the past but wasn't sure how these new distributions were integrated.  Can I try this - rename current kernel, build new one, test, revert back if things don't work?

You should be able to install more than one kernel at once, and boot between them in grub.

---

### Post by cariboo on 2008-08-18
If you have linux drivers wouldn't it be easier just to use and install them. If not there is a newer kernel in the intrepid repositories, mind you Ubuntu and upstream kernel do not have the same numbers, kernel.org says the lates stable kernel is 2.6.26.2 where as my kernel say it is 2.6.26-5

The intrepid alpha 4 iso came out last thursday, If you want to download it and give it a try, be warned that this is alpha software and many things don't work the way you expect them to.

Jim

---

### Post by IntuitiveNipple on 2008-08-18
> **cariboo907 said:**
> ...mind you Ubuntu and upstream kernel do not have the same numbers, kernel.org says the lates stable kernel is 2.6.26.2 where as my kernel say it is 2.6.26-5

Just a note of explanation... we track the upstream kernel closely. An Ubuntu 2.6.26 kernel (during development) is re-based often to track upstream but doesn't show the .release.

The Ubuntu "-5" suffix is the ABI (Application Binary Interface) number. Each time the kernel's list of exported function signatures changes the ABI is incremented to indicate to external modules that the kernel interface has changed and they need to be rebuilt against the latest kernel headers.

As to the sound-card testing I agree with Jim, try the latest Intrepid LiveCD alpha - even if other things don't work at least you might get the chance to test the sound side of things before the RMA period expires.

---

### Post by Archmage on 2008-08-18
Did you consider testing the latest Alpha von Intrepid?

[http://ubuntuforums.org/showthread.php?t=889702](http://ubuntuforums.org/showthread.php?t=889702)

---

### Post by resqguy on 2008-08-18
> Did you consider testing the latest Alpha von Intrepid?


That's a great suggestion.  So I've burned a CD, do I boot from that CD or can I load it after Ubuntu is already up?

---

### Post by hardyn on 2008-08-18
you must boot it.

---

