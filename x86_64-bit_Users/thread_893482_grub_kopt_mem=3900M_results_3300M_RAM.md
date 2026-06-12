---
title: "grub kopt mem=3900M results 3300M RAM ?"
date: 2008-08-18
forum: x86 64-bit Users
---

### Post by LinusLandar on 2008-08-18
hello forum,

i am using 8.04.1 amd64. If i set grub-kopt mem=3900M the result is the kernel is using 3300M memory (checked with free). shouldn't the amd64 kernel use 3900M instead?

best regards

frank

---

### Post by felker2 on 2008-08-18
First, post the output of "dmesg | head -20" (without the double quotes) here. It will show two things: Linux version and memory mapping.

Then, check BIOS version and BIOS memory mapping.

BTW: how old is the motherboard?

---

### Post by LinusLandar on 2008-08-19
hello,

motherboard is 1 year old. but no need to look further, i have solved my main issue with networking problems. seems to be ralated to an "old" driver for 3ware 8006 controller, having problems with systems having 4Gbyte RAM or more. i updated the driver, deleted the grub-mem-option, and everything seems to be fine.

i am going to upgrade to 8.04, because the error should not show up there. 

i hope ;-)

best regards

---

### Post by jespdj on 2008-08-19
Check if there is a "memory remapping" option in the BIOS settings and make sure it is enabled.

Seeing less than 4 GB (even with a 64-bit OS) is a common problem. Part of the address space is reserved for devices in your system.

---

### Post by felker2 on 2008-08-19
> **LinusLandar said:**
> 
i am going to upgrade to 8.04, because the error should not show up there. 


In your first post you said you were using 8.04.1, so how can you *upgrade* to 8.04? :confused:

---

