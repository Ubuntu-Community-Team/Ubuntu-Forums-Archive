---
title: "Kernel patches and 2.6.13+"
date: 2005-10-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by jimbolaya on 2005-10-11
I need to use 2.6.12 or above and would ideally like to use 2.6.13 or above.  However, there doesn't seem to be a package for this kernel for Hoary.  

Alternatively, I would love to be able to pick up a kernel from kernel.org and patch it so that it resembles the packaged Ubuntu kernels.  None of this seems to be discussed anywhere.  Mostly I've seen things like "you can find the latest kernel source at . . ." as a response to "what patches are used" when I really just want a list of patches that are used.

Can anyone help me with this question?

James

---

### Post by 23meg on 2005-10-11
you can find the Ubuntu patches to the vanilla kernel in the package linux-patch-ubuntu-2.6.12 .

i'd like to do something similar: i need to patch a 2.6.12 or higher kernel with the task preemtion patch (which AFAIK didn't make it into .13) in order to enable realtime operation with the JACK audio server. but if i do this with a vanilla kernel i'll lose the benefits of Ubuntu patches to it, so what i'd like is 2.6.12 plus task preemption patch plus Ubuntu patches to 2.6.12 . i'd appreciate some pointers. 

question: will .13 be available in Breezy in a while just like .11 was available in Hoary? if it is, will it include Ubuntu patches to .12?

---

