---
title: "How do i set linux-amd64-xeon as my default kernal"
date: 2007-11-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by robinlennox on 2007-11-07
I've install it... using sudo apt-get install linux-amd64-xeon.... reboot the server.... and it's still show the default kernal amd64-server if i run uname -r

Any Ideas, How I can set the default kernal to be amd64-xeon?

---

### Post by John.Michael.Kane on 2007-11-07
> **robinlennox said:**
> I've install it... using sudo apt-get install linux-amd64-xeon.... reboot the server.... and it's still show the default kernal amd64-server if i run uname -r

Any Ideas, How I can set the default kernal to be amd64-xeon?

Those kernels are obsoleted ,and are no longer used. Ubuntu uses a standard generic kernel which includes smp support built in.

---

### Post by robinlennox on 2007-11-08
I am running Ubuntu 6.06: Is it still the case that I should leave the default kernal on?

---

### Post by John.Michael.Kane on 2007-11-08
> **robinlennox said:**
> I am running Ubuntu 6.06: Is it still the case that I should leave the default kernal on?

You should be able to move over to the xeon kernel, As those kernels where not obsoleted until edgy was released.

IMHO unless the server is acting up or seems not to be function at it's peak level I would leave it be.  

That said. You can check under the grub menu to see if the new kernel is listed by pressing the Esc key during reboot. you may also want to try reinstalling the kernel in question using sudo aptitude install linux-amd64-xeon.

---

