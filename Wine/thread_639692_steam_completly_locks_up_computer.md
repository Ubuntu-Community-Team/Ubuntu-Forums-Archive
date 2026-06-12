---
title: "steam completly locks up computer"
date: 2007-12-13
forum: Wine
---

### Post by Ffuzzdaddy on 2007-12-13
I recently installed wine on my computer and steam. steam loads up fine but about 2-3 mins in to a game my computer completely locks up. i thought it was my video card driver so i used envy to update my video card driver. but it still happens.
graphics card is ati mobility radeon x1600

---

### Post by Hooloovooloo on 2007-12-13
Yeea, i think it's because of a memory leak in the ATI driver. I have the same problem. Wait and see if they fix it soon. :)

---

### Post by Technophobia on 2007-12-13
Does the 5 second rule apply to computers? So if memory leaks and you computer licks it up in under 5 seconds is the memory still good?

---

### Post by drummingpariah on 2007-12-13
> **Technophobia said:**
> Does the 5 second rule apply to computers? So if memory leaks and you computer licks it up in under 5 seconds is the memory still good?

As opposed to bad?  Unless you're very familiar with TOP and possibly have some debugging/tracking clients, there isn't much you can do for a leak.

As far as your memory leak, it's not going to cause the ram to go bad.  Do you just mean that restarting is not necessary?  In that case, you should still have all the same modules and libraries loaded up, and your operating system is still running, so you should be good to go.  Unlike most other operating systems (no names), *nix is in layers of importance that make sense.  It's good at finding problems when it can, and fixing them.  Unfortunately, there's nothing it can do about bad code and infinite loops.  Steam could have been made better.  It's hacked in to work on Windows, and the Valve crew isn't giving the same attention to Wine; also, ATI has proven their lack of support for the open source community time and time again.  Perhaps AMD will help?  Time will tell.

---

