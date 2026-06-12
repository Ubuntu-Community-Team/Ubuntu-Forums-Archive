---
title: "[ uname ] reports wrong system"
date: 2008-08-13
forum: x86 64-bit Users
---

### Post by Nolan Cooper on 2008-08-13
Hi--
I have searched the forums and used google for this problem.
When trying to compile or install a program I receive a failure because it identifies the system as x86_64. This is wrong, it is x86_32.

Can someone help or point me in the right direction?
I have no clue as how to fix this.

thanks 
nolan

---

### Post by cubeist on 2008-08-13
> **Nolan Cooper said:**
> Hi--
I have searched the forums and used google for this problem.
When trying to compile or install a program I receive a failure because it identifies the system as x86_64. This is wrong, it is x86_32.

Can someone help or point me in the right direction?
I have no clue as how to fix this.

thanks 
nolan

what is the output of uname -a  in a terminal?

---

### Post by Nolan Cooper on 2008-08-14
output below.

[uname-a]--->
Linux RETIRED 2.6.24-19-generic #1 SMP Fri Jul 11 21:01:46 UTC 2008 x86_64 GNU/Linux

[uname-m]--->x86_64

nolan

---

### Post by Kilz on 2008-08-14
You have the 64bit or AMD64 version installed.

---

### Post by Nolan Cooper on 2008-08-18
Kilz, thanks for the reply.

This must mean that I have the 64 bit hardy installed. Is that correct?

The system is an Intel 32 bit CPU.

I do not know how the 64 bit was installed, as I made sure the 32 bit DVD was facing down in the reader. How would it read from the top?

thanks
nolan

p.s. To solve, need I just to uninstall Ubuntu and reinstall?

---

### Post by Jouke74 on 2008-08-18
Hmmm very interesting because I don't think a 64 Bit OS will work on a pure 32 bit Intel processor. With other words, your processor is probably capable of running 64 bit as well.

If you really want a 32bit OS then a reinstall with the 32 bit i386 version will be fine. 

Of course, since this is the 64 bit forum, I suggest to keep this version instead :lolflag:

---

### Post by ibuclaw on 2008-08-18
```
sudo lshw -C processor
```
Will tell you what your CPU is capable of.

```
dpkg --print-architecture
```
Will tell you which architecture your repository is tied to.

If all the output says that it is 64bit, then it is what it is, I'm afraid, whether you like it or not.

Also, note that recent PC's with Intel Chips are mostly 64bit enabled, even if you don't realise this in the first place.

If the above two app commands produce an output that does not seem to suggest that your PC is 64bit, then I'll look deeper into helping you fix it.

Regards
Iain

---

### Post by Sef on 2008-08-22
> Hmmm very interesting because I don't think a 64 Bit OS will work on a pure 32 bit Intel processor. With other words, your processor is probably capable of running 64 bit as well.

That is correct.  An AMD64 can run either 32 or 64-bit oses; however, an x86 (32-bit) can only run 32-bit oses.

---

