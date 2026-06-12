---
title: "32-bit programs (and wine programs) can't lookup domain names"
date: 2008-04-27
forum: x86 64-bit Users
---

### Post by Agent ME on 2008-04-27
I've been having some trouble with some 32-bit programs (mostly wine-emulated programs, but even linux-32-bit programs) looking up domain names. I can run portable-firefox on my flashdrive, but it can't browse to domains (like "google.com") but it can work with IP addresses (if I enter google's IP, it works). Or if I use a socks or http proxy (with network.proxy.socks_remote_dns set to true for mozilla programs) it can do the lookups.

I'm currently using SSH to use my own computer as a socks proxy for these programs *(ssh -D 7070 localhost)*, but I want to know if there's a way to properly fix this and if others get this problem.

I'm running 8.04 64-bit version, upgraded from 7.10 64-bit via the autoupdater-program. This problem didn't happen with 7.10 for me.

---

### Post by Cappy on 2008-04-27
Here: [http://ubuntuforums.org/showthread.php?t=763576](http://ubuntuforums.org/showthread.php?t=763576)

---

