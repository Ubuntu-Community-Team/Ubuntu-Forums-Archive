---
title: "Running Kqemu on Vista x64"
date: 2008-04-30
forum: x86 64-bit Users
---

### Post by timryan on 2008-04-30
I recently installed Ubuntu 7.10 on my portable hard drive and have been using Qemu to run Ubuntu while in Windows. However, I've found that running Ubuntu is extremely slow. I have 4gb of RAM, Vista x64, a q6600 proc, and I've allocated 1gb of RAM to Ubuntu whenever its started up, but it still runs fairly slow. I've been trying to get Kqemu to work, but it hasn't cooperated. Whenever i type "net start kqemu" in the cmd prompt, it returns the following message: "System error 1275 has occurred. The driver has been blocked from loading." Kqemu never starts up :/
Is there any way I can get it to work? I hate that fact that Ubuntu is so slow while being emulated. I've read a few posts on some random forums that Kqemu isn't compatible with x64 architecture... I really hope that isn't the case.

Furthermore, is there any alternative I could possibly take when it comes to emulating? Maybe using another emulator? I really enjoy being able to use both Windows and Ubuntu at the same time, and I already have Ubuntu 7.04 installed on a laptop of mine, so I dont want to take that route when it comes to my desktop.
Thanks in advance.

-Tim

---

### Post by M0J0Nixon on 2008-08-15
Hey Tim,

I have the exact same problem.  Kqemu just doesn't like running on my Vista x64.  Any chance that you figured out a way around this?

Or anyone else out there?  I would love to get this working, but as it is it just doesn't run fast enough to enjoy.

Thanks for any help!

---

### Post by worldgnat on 2008-12-05
The problem is that Kqemu is a 32-bit driver running on a 64 bit operating system. From what I've found, if you have 64-bit windows or more than 3 gigs of RAM, there is no way to run Kqemu.

Cheers,
-Peter

---

