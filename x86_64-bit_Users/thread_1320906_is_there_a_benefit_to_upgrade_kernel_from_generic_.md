---
title: "is there a benefit to upgrade kernel from generic to server"
date: 2009-11-09
forum: x86 64-bit Users
---

### Post by ali_williams on 2009-11-09
I have 4gb of ram on my Ubuntu 9.10 64bit distro now back when i ran 9.04 i was on 32bit running the server kernel (that was because I had 4gb of ram) So now that I have moved on to the 64bit world is there a benefit to running the server kernel over what comes preinstalled? I only ask this because I run VMWare server on the pc and many other services like ftp, web, and samba.

---

### Post by TheHolm on 2009-11-09
> **ali_williams said:**
> I have 4gb of ram on my Ubuntu 9.10 64bit distro now back when i ran 9.04 i was on 32bit running the server kernel (that was because I had 4gb of ram) So now that I have moved on to the 64bit world is there a benefit to running the server kernel over what comes preinstalled? I only ask this because I run VMWare server on the pc and many other services like ftp, web, and samba.

Nobody tell you what kernel is better for you. Just install server kernel, boot from it and run couple of benchmark to compare performance.

---

### Post by ali_williams on 2009-11-10
> **TheHolm said:**
> Nobody tell you what kernel is better for you. Just install server kernel, boot from it and run couple of benchmark to compare performance.
cool thanks

---

### Post by Kilz on 2009-11-10
While not a answer to the specific version asked about. There is an advantage to using the server kernel on long term support versions. This is because the kernel is what is used to determine the amount of time support is available for the install. Generic kernel receives 3 years, server receives 5 years. Just something to keep in mind if you are setting up a server with the next version as lucid will be a lts.

---

### Post by ali_williams on 2009-11-10
> **Kilz said:**
> While not a answer to the specific version asked about. There is an advantage to using the server kernel on long term support versions. This is because the kernel is what is used to determine the amount of time support is available for the install. Generic kernel receives 3 years, server receives 5 years. Just something to keep in mind if you are setting up a server with the next version as lucid will be a lts.

I heard they have a virtual kernel for ubuntu for people that run vmware server i think i might give that a Go seeing as that i use my box for mostly vmware stuff ;)

---

