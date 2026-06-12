---
title: "lib32 installed by default on 8.10?"
date: 2009-02-26
forum: x86 64-bit Users
---

### Post by crowel57 on 2009-02-26
I recently installed Ubuntu 8.10 x64 on my new laptop. I've used linux a lot before, but this was my first time with Ubuntu, and I love it. However, when I installed on my laptop, by default, it also installed all the 32 bit libraries, and my Ubuntu x64 fully supports all 32-bit programs (at least every one I've tried so far).
However, I then gave my CD to my friend who has a Gateway desktop. When he installed, it did not install any 32 bit libraries, and will not execute any 32 bit programs.
We're both developers, so we need the 32-bit Java Development Kit, so, just using 64 bit version is not an option.

Does anyone have any idea why it would install by default on my machine, and it doesn't on his? And maybe how we can get it to install on his? We manually added lib32 libraries, but that didn't help. He still gets complaints about the architecture. Any help would be greatly appreciated!

---

### Post by wfp on 2009-02-26
Have you read through this > [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

---

### Post by Yellow Pasque on 2009-02-27
Has your friend done this:
```
sudo apt-get install ia32-sun-java6-bin
```

---

