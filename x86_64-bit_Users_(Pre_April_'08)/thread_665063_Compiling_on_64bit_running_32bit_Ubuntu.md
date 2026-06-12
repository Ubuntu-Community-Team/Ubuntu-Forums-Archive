---
title: "Compiling on 64bit running 32bit Ubuntu"
date: 2008-01-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by Dale Gerdemann on 2008-01-11
Sorry to ask a rather basic question, but I didn't see exactly this question in the stickies.

I have a 64bit machine and am running 32 bit Ubuntu. When I compile programs from source, is it at all important that the machine is 64bit? Should I use any special compiler options or libraries for 64 bit? Or do I simply use 32 bit versions to be consistent with the OS? For examplle, should I install the 64 bit version of libstdc++, or is this irrelevant for me?

Dale Gerdemann

---

### Post by Joeb454 on 2008-01-11
Compile them in 32 bit. I'm guessing you want them to run on your system? :p

Basic answer: No, you don't need to compile in 64 bit code

---

### Post by zipperback on 2008-01-11
if you are running the 32bit version of Ubuntu Linux on your system, then you will be compiling and running 32 bit versions of whatever applications it is that you are working with.

Be sure that you have installed the build-essential package.

```

sudo update
sudo apt-get install build-essential

```


- zipperback
:popcorn:

---

### Post by Kilz on 2008-01-11
> **Dale Gerdemann said:**
> Sorry to ask a rather basic question, but I didn't see exactly this question in the stickies.

I have a 64bit machine and am running 32 bit Ubuntu. When I compile programs from source, is it at all important that the machine is 64bit? Should I use any special compiler options or libraries for 64 bit? Or do I simply use 32 bit versions to be consistent with the OS? For examplle, should I install the 64 bit version of libstdc++, or is this irrelevant for me?

Dale Gerdemann

Since you are running 32bit there is no way you could compile 64bit applications. The 32bit verssion limits you to 32bit. 
Now, if you were running the 64bit version you could compile 32bit or 64bit versions. Just another instance where you limit yourself by installing an operating system not specifically created for your hardware.

---

### Post by Yellow Pasque on 2008-01-11
> Since you are running 32bit there is no way you could compile 64bit applications. The 32bit version limits you to 32bit.
I believe one CAN cross-compile 64-bit code if one needs to.

---

### Post by NullHead on 2008-01-12
NO .. you don't need 64 bit libs to compile you're software. You just need build-essential.

---

### Post by Kilz on 2008-01-12
> **Temüjin said:**
> I believe one CAN cross-compile 64-bit code if one needs to.

I have tried in the past and failed, I think it was because of lack of development files.

---

