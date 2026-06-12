---
title: "which download ?"
date: 2009-04-15
forum: x86 64-bit Users
---

### Post by stans on 2009-04-15
I'd like to install a 64 bit version - how do I know which one is correct ?

I have a Pentium 4 -

---

### Post by Yashiro on 2009-04-15
You want the iso tagged with AMD64.
[http://cdimage.ubuntu.com/releases/8.04.2/release/ubuntu-8.04.1-dvd-amd64.iso](http://cdimage.ubuntu.com/releases/8.04.2/release/ubuntu-8.04.1-dvd-amd64.iso)
for example.

---

### Post by 3Miro on 2009-04-15
The one that might work is the amd64 (don't get taken by the amd, it is just the name for the standard, Intel Core 2 Duo uses the same standard).

I don't know if P4 supports 64 bit (some do some don't). The best way to check is to download the LiveCD and try it, but that might waste a CD. Another way is to check if the CPU supports EMT64.

---

### Post by stans on 2009-04-15
Thanks for the replies. The AMD did indeed throw me, that's why I asked.

Is there a command that will tell me what the cpu is capable of ?

Cancel the question; found the answer (lshw.txt).

---

### Post by FredB on 2009-04-16
if you have a P4 CPU, you will have to use a 32 bits version.

Only Core2Duo / AMD X2 and younger CPU are 64bits enabled.

---

### Post by jespdj on 2009-04-16
> **FredB said:**
> if you have a P4 CPU, you will have to use a 32 bits version.

Only Core2Duo / AMD X2 and younger CPU are 64bits enabled.
No, that is not accurate. Note that there are a lot of Pentium 4 models. Some do support 64-bit and some do not. All Core 2 Duo processors support 64-bit, but the older Core Duo processors do not.

You can use [Intel's processor finder](http://processorfinder.intel.com/) to find the specifications for your processor, if you know which model it is exactly.

---

### Post by stans on 2009-04-17
LSHW showed me '64 wide' so I downloaded the 64 bit .iso image, burned it to a cd then booted it as a test. 

One of the utilities on it did indeed recognize the 8gb I had just added.

Thanks again for all the responses.

---

