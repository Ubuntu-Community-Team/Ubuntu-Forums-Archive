---
title: "Shutdown saves session???"
date: 2005-09-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by nwillis on 2005-09-02
OK, this is just nuts.  Wednesday I compiled a new kernel (2.6.10; nothing special), and since then every time I try to shut down the system via GNOME's System > Log Out > Shut down menu, two things go wrong, and one just happens inexplicably:
[list=1]
[*]The system does *not* shut down
[*]It returns a message box reading "Your session has been saved"
[*]esd starts up and is eating cpu
[/list]

I don't have to tell you that none of this is welcome news.  For starters, what's hanging the shutdown sequence?  After I click the OK button on the message box, I'm returned to the system, running normally as if nothing were wrong.

Second, before anyone asks, *no* the "Save current setup" box is not checked.  !??!?!?  Finally, I don't use esd.

I don't have any proof that the new kernel is connected to this screwball behavior, it could just be coincidence.  But the only other things that have changed are normal, synaptic-primed updates.

Where do I look?  

Nate

---

### Post by mlomker on 2005-09-02
That's odd, but I assume you've verified that it isn't desktop related by booting into the olde kernel?

In some ways you're doing better than I am--I've tried six times to recompile the 2.6.10 kernel and it never boots...even using the exact config that came with the kernel.  I don't get it.  I'm running 2.6.13-ck1 right now, instead.  VMware won't work on it, but otherwise it's peachy.

---

