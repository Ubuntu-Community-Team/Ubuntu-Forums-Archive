---
title: "configure errors"
date: 2005-09-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by indym79 on 2005-09-09
when ever I attempt to run ./configure with anything I always get this error message.

"configure: error: no acceptable C compiler found in $PATH"

I just installed 5.04 for AMD64 about 2 days ago.

I have used Linux in the past from time to time but would still call my self new to Linux.

I don't know how to make sure things like a compiler are even installed or installed correctly.  I would have thought that they would be upon installing the system.

---

### Post by DJ_Max on 2005-09-09
```
sudo apt-get install build-essential
```

---

### Post by mlomker on 2005-09-09
apt-get install build-essential

You'll probably want to download the linux-headers for your running kernel as well (do a search in synaptic).  **uname -r** from a prompt will tell you what version your running kernel is.

---

