---
title: "Getting zoolz to work linux"
date: 2013-04-19
forum: Wine
---

### Post by cmcanulty on 2013-04-19
I took advantage of the 100GB free and am trying to get zoolz to work in ubuntu 12.04. I installed it with wine but can't get it to work. Part of the issue is there are numerous exe files and I don't know how to have wine run it. I am attaching a screenshot of its' folder.
[https://www.zoolz.com/Zoolz_Home]("https://www.zoolz.com/Zoolz_Home")

---

### Post by HermanAB on 2013-04-19
Hmm, all you need to do is install the utilities on a Windows machine, then sniff the proprietary protocol with Wireshark and reverse engineer it.  Nothing to it...

---

### Post by Mark Phelps on 2013-04-19
With Wine, it's not so much the exe files as it is the DLLs -- as every DLL that makes a Windows system call has to be replaced with a DLL that makes Linux system calls, instead.  There's a bunch of DLLs in there, too -- which really hurts your chances of getting this to work.

---

### Post by sandyd on 2013-04-19
Moved to wine

---

