---
title: "32 bit or 64 bit for 3 GB of RAM"
date: 2008-11-11
forum: x86 64-bit Users
---

### Post by CoreyB. on 2008-11-11
I know one of the advantages of 64 bit is that it can use more than 3.5 GB of RAM.  I recently installed Ubuntu 8.10 on my laptop (Linux n00b).  I installed the 32 bit version.  Would I get better or worse performance if I installed the 64 bit version?  I am already getting full use of my RAM.  From what I understand is it would be worse because it would use bigger files for almost everything right?  I have an Intel Core 2 Duo.  I don't have AMD 64, would the .iso that says 'amd64' work?  Is that just the way the 64 bit is designated?

---

### Post by waffen on 2008-11-11
Please you need read:

[http://ubuntuforums.org/showthread.php?t=765428]("http://ubuntuforums.org/showthread.php?t=765428")

I use 64 bits version (yes AMD packages is the good choice) and I see an increase of RAM use, is logic because the integer are more longer.

If you plan use more then 4GB use 64 bits version, if not check if all applications have a 64 bits version, if not you can compile forced to 32 bits... I only have problems with DBDesigner Fork, is too old for compile in 32bits, so I use it with Wine! and works again! :)

---

### Post by NullHead on 2008-11-11
I'd go for 64bit. It runs faster and you get to use all your ram :D

---

### Post by Yellow Pasque on 2008-11-11
You do have AMD64. The architecture is called 'amd64' because AMD invented it. Intel Core 2 processors (et al.) are compatible with the amd64 architecture, but of course, Intel calls it something different (EMT64) on their CPU's. Anyway, it's all x86_64 to us end users.

> From what I understand is it would be worse because it would use bigger files for almost everything right?
Not really. The differences between 32-bit and 64-bit in most apps are negligible. My personal opinion is not to mess with a working install unless you have a good reason to. So unless you routinely do applications that benefit from 64-bit (Photoshop, video encoding, virtualization, heavy math) or you plan to add more RAM in the future, I recommend staying with what you have.

Also, see the sticky in this forum.

---

### Post by Therion on 2008-11-11
I can't think of a single reason to use a 32-bit distro if your processor is 64-bit.  And yes, you will get better performance out of a 64-bit distro on a 64-bit processor based PC.  Better performance is why processors, and computing in general, are moving toward 64-bit.  I've used 64-bit distros of Ubuntu for last few years and have had nothing but success... Except for Intrepid.

---

### Post by waffen on 2008-11-11
> **Therion said:**
> I can't think of a single reason to use a 32-bit distro if your processor is 64-bit.  And yes, you will get better performance out of a 64-bit distro on a 64-bit processor based PC.  Better performance is why processors, and computing in general, are moving toward 64-bit.  I've used 64-bit distros of Ubuntu for last few years and have had nothing but success... Except for Intrepid.

Whats wrong in Intrepid?

---

### Post by Therion on 2008-11-11
> **waffen said:**
> Whats wrong in Intrepid?
I didn't mean to imply there is anything wrong with Intrepid in and of itself.  From what I can tell for many people it's a fine release.  It's just not panning out well for me, personally.  I gave it a couple go-arounds, but it's just not working out.  That's just my experience with it however and shouldn't be taken as condemnation of the distro itself.

---

### Post by waffen on 2008-11-11
> **Therion said:**
> I didn't mean to imply there is anything wrong with Intrepid in and of itself.  From what I can tell for many people it's a fine release.  It's just not panning out well for me, personally.  I gave it a couple go-arounds, but it's just not working out.  That's just my experience with it however and shouldn't be taken as condemnation of the distro itself.

Yes I understand you, my question point about thats go-arounds... for example I need to change the NetworkManager for Wicd, because NM never can store and manage my fixed IP address and other stuffs... is very interesting know about the others experience...

---

### Post by CoreyB. on 2008-11-11
> **Temüjin said:**
> You do have AMD64. The architecture is called 'amd64' because AMD invented it. Intel Core 2 processors (et al.) are compatible with the amd64 architecture, but of course, Intel calls it something different (EMT64) on their CPU's. Anyway, it's all x86_64 to us end users.


Not really. The differences between 32-bit and 64-bit in most apps are negligible. My personal opinion is not to mess with a working install unless you have a good reason to. So unless you routinely do applications that benefit from 64-bit (Photoshop, video encoding, virtualization, heavy math) or you plan to add more RAM in the future, I recommend staying with what you have.

Also, see the sticky in this forum.

Yeah, good point.  Maybe when 9.04 comes out, if I decide to do a fresh reinstall instead of upgrade, I might go with 64 bit.

---

