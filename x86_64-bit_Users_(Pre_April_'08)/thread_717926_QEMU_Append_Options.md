---
title: "QEMU Append Options?"
date: 2008-03-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by electricchild on 2008-03-07
I am using QEMU to emulate a kernel with a file system image I have created, w/ Ubuntu Gutsy as my build OS. I was wondering, for people who have used QEMU, if there is a list of available options for the -append option when issuing the QEMU command in the build OS?

Basically my problem is the kernel isn't booting up correctly in the emulator, and I want to read the kernel boot-up log to see what the problem is with my kernel configuration. Is there any possible way to output that bootup log to a file in my Ubuntu OS so I can go through the problem? Please note that I cannot issue commands in the emulated environment because the kernel isn't booting up correctly, and thus I am not even getting to the CLI shell. (The append option might have something I can type in to let it output that information to a file in the Ubuntu OS, but I am not sure, so that's why I am asking you guys).

Thanks a lot!!!!

---

