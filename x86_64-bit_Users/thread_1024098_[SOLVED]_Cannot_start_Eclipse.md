---
title: "[SOLVED] Cannot start Eclipse"
date: 2008-12-28
forum: x86 64-bit Users
---

### Post by portis on 2008-12-28
I've installed eclipse 3.4.1. But I cannot start it as a normal user. I got the error:

#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00007ff663acdcc7, pid=4851, tid=140696899955024
#
# Java VM: Java HotSpot(TM) 64-Bit Server VM (11.0-b16 mixed mode linux-amd64)
# Problematic frame:
# C  [libgobject-2.0.so.0+0x26cc7]  g_type_fundamental+0x17
#
# An error report file with more information is saved as:
# /home/ming/Software/eclipse/hs_err_pid4851.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)

I tried openjdk, java-6-sun, java-6-cacao, but got the same error.
But I can start Eclipse with a sudo prefix.
$sudo eclipse

Can anyone give me some idea? Thanks.

---

### Post by portis on 2008-12-28
I got it.

It's due to the input method. Found a workaround:

$GTK_IM_MODULE="" eclipse

---

### Post by uBeer on 2009-03-29
Can you tell a bit more about how you fixed it?
Because I have the same problem, and I don't know how to fix it.

Thanks!

---

### Post by uBeer on 2009-03-29
I put 
```
export GTK_IM_MODULE=""
```
in my ~/.bashrc and after a restart Eclipse started without much trouble.

---

### Post by uBeer on 2009-03-30
Hmm, only the first time I try to run it, it'll work, but when I've closed Eclipse and try to run it again I fails to start and get the same error message in my home directory.

Any other solution?

---

### Post by uBeer on 2009-03-31
Ah, found the problem: Eclipse 64 bit and Global Menu-bar applet don't work nice together :(

---

### Post by Adrian Challinor on 2009-04-24
So, pray tell, what did you do to solve it?

---

### Post by ttr on 2009-04-28
I had this issue, but it was resolved when I updated to the latest Java Jdk (1.6.0_13)

---

