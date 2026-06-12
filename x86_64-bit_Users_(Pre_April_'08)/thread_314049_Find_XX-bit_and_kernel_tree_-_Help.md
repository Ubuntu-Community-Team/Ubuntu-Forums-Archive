---
title: "Find XX-bit and kernel tree - Help"
date: 2006-12-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by smith.norton on 2006-12-06
How can I find out whether 32-bit Ubuntu or 64-Ubuntu is running on my 64-bit laptop?

Also, I need the kernel tree to start kernel programming. I have absolutely no idea of kernel programming, I have got some documents like LKMPG, etc. Can anyone suggest how can I get started?

---

### Post by kuja on 2006-12-07
in a terminal: uname -m
If you're running 64-bit it will say x86_64.

As per getting the kernel. Unless you're working on something distribution related, you probably want a vanilla kernel from kernel.org. You can download the tree from there. If you ARE working on something distribution related, install the linux-source package.

Also, you may be able to find this book for free download if you look around: "Linux device drivers". I found it once ... it should give you a general idea of what's going on in the kernel.

---

### Post by bjd on 2006-12-07
The 'linux device drivers' book can be downloaded here: [http://lwn.net/Kernel/LDD3/](http://lwn.net/Kernel/LDD3/)
Though it may not be completely up-to-date regarding current kernels, it's a good starting point...

---

