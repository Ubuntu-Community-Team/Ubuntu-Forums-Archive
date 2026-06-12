---
title: "RealPlayer Binary won't execute"
date: 2007-11-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by cosmofed on 2007-11-10
I'm trying to install RealPlayer. I have downloaded the program from [www.real.com/linux](www.real.com/linux).
Saved it to my desktop and changed permission to execute:

cos@cos-laptop:~$ cd /home/cos/Desktop
cos@cos-laptop:~/Desktop$ ls -l
total 5672
drwxrwxrwx 2 cos cos    4096 2007-11-07 14:26 BCM4311(rev01)
-rwxrwxrwx 1 cos cos 5790356 2007-11-08 20:11 RealPlayer10GOLD.bin
cos@cos-laptop:~/Desktop$ sudo ./RealPlayer10GOLD.bin
[sudo] password for cos:
sudo: unable to execute ./RealPlayer10GOLD.bin: No such file or directory
cos@cos-laptop:~/Desktop$ 

What am I missing here?
Thank you,

---

### Post by cjazz on 2007-11-11
I was going to ask if you'd made the file executable, but I just reread your post and saw that it was. Giving myself one self-administered slap upside the head.

Not that it's necessarily your problem, but I had to install ia32-libs to allow the 32-bit Real Player to install on my 64-bit system. Still don't know why it would report "no such file or directory."

---

### Post by Kilz on 2007-11-11
Perhaps you have a corrupted file.

---

### Post by mexaly on 2008-07-04
> **cjazz said:**
> I was going to ask if you'd made the file executable, but I just reread your post and saw that it was. Giving myself one self-administered slap upside the head.

Not that it's necessarily your problem, but I had to install ia32-libs to allow the 32-bit Real Player to install on my 64-bit system. Still don't know why it would report "no such file or directory."
Thanks, Cjazz, ia32-libs was the answer for me.

It took a long time to find your tip, and golly, I was getting frustrated with everybody else's 'chmod' tips, when I already knew that.

Thanks again, and happy Independence Day!

mexaly

---

