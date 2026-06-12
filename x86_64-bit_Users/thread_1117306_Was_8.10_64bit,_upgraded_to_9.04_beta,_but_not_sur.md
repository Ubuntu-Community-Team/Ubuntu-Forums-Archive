---
title: "Was 8.10 64bit, upgraded to 9.04 beta, but not sure if IT'S 64bit"
date: 2009-04-05
forum: x86 64-bit Users
---

### Post by j0hnnya on 2009-04-05
Just trying to figure out exactly what version I am currently operating.  I was 8.10 64bit, upgraded to beta 9.04, but not sure if it's 64 bit as well.  If not, how would I go about up-ing it to 64 bit?

(I have looked at System>About Ubuntu, but it just says 9.04 everywhere I look)

Your help is appreciated.

---

### Post by vegetarianshrimp on 2009-04-05
[http://ubuntuforums.org/showthread.php?t=278606](http://ubuntuforums.org/showthread.php?t=278606)

**uname -a** in terminal

---

### Post by drs305 on 2009-04-05
If the following command returns "CONFIG_X86_64=y" it's 64-bit OS on a 64-bit system:
```
cat /boot/config-`uname -r` | grep CONFIG_X86_64= 
```

If it is a 32-bit install you cannot upgrade it to 64-bit without reinstalling from a CD/iso image.

---

### Post by Slim Odds on 2009-04-05
> **drs305 said:**
> If the following command returns "CONFIG_X86_64=y" it's 64-bit OS on a 64-bit system:
```
cat /boot/config-`uname -r` | grep CONFIG_X86_64= 
```If it is a 32-bit install you cannot upgrade it to 64-bit without reinstalling from a CD/iso image.

LOL. Talk about making it harder than it needs to be.

How about just:```
uname -m
```???

---

### Post by drs305 on 2009-04-05
> **Slim Odds said:**
> LOL. Talk about making it harder than it needs to be.
How about just:```
uname -m
```???

Believe me, I know; but it's a one-line copy paste either way. 

The reason I don't use the "uname" command any longer is I've read too many multi-page posts on whether the command returns the computer architecture or merely reports the *installed* system. I've even seen discussions go on almost without end as to the definition of "machine hardware"  although it seems pretty obvious to me (and to you).  ;-)

---

### Post by jespdj on 2009-04-06
There is no way to automatically upgrade from a 64-bit to a 32-bit installation or vice versa.

So, unless you did a fresh install, and if your 8.10 was 64-bit, your 9.04 is certainly also 64-bit.

---

### Post by Slim Odds on 2009-04-06
> **jespdj said:**
> There is no way to automatically upgrade from a 64-bit to a 32-bit installation or vice versa.

So, unless you did a fresh install, and if your 8.10 was 64-bit, your 9.04 is certainly also 64-bit.

That is correct. 32 bit systems upgrade to 32 bit and 64 to 64.

---

