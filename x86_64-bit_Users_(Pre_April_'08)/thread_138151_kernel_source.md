---
title: "kernel source"
date: 2006-03-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by lokeey on 2006-03-01
i need to install kernel source, but i don't see kernel source i need on synaptic. or maybe it is the one, but how can i tell.

i'm running kernel 2.6.12-10-amd64-generic i only see kernel source 2.6.10-6 and 2.6.11-7. where can i get 2.6.12-10-amd64???

---

### Post by jeremiebergeron on 2006-03-01
There should be a wike page somewhere on installing manual kernels and it should tell you how to install the source you're looking for. I haven't done this recently so I can't remember how but I hope this helps.

---

### Post by lokeey on 2006-03-01
looked around and can't seem to find kernel source for amd64-generic anywhere. is anyone having the same problem locating this kernel source??? does it even exist?

i get the following error when i do....
'sudo apt-get install linux-source-2.6.12-10-amd64-generic'

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-source-2.6.12-10-amd64-generic

---

### Post by RAOF on 2006-03-01
The source package doesn't have an architecture (amd64) or subarchitecture (generic, k8, etc) associated with it.  This is because the same source builds **all** the kernels: -i386, -amd64, -powerpc, -arm, whatever.

Secondly, you probably don't **need** the kernel source.  What you probably need are the kernel headers.  You'll find **them** as the "linux-headers-amd64-generic" package.

If you just need to compile a driver, or something, the headers are what you need.

---

### Post by lokeey on 2006-03-01
w00t!
that did it!
had previously tried it and gave up, but i checked my history after seeing your post and saw a big fat TYPO!

thanks for the help!!!!

---

