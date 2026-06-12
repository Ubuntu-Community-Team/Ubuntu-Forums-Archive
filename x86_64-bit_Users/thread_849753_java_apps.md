---
title: "java apps"
date: 2008-07-04
forum: x86 64-bit Users
---

### Post by Richard-g8jvm on 2008-07-04
Yes I've read the sticky bit.

I'm using a AMD dual core Athlon , I'm begining to wish I'd bought a intel dual core thing.
I need to install netbeans, the package off the sun site wont load as it needs jdk.
all the package bundles from Sun will not install, they just hang during install.
Following the info on the stick bit I get

NetBeans cannot be installed on your computer type (amd64)

Either the application requires special hardware features or the vendor decided to not support your computer type.

I moved from Mandriva due to a bug effecting FFT, I'm now wondering if I've jumped from the frying into the fire ?

Is unbutu using 32bit libs for everything ?

theres only a few libs in /lib64 and a lot of lib32 


Is tghis resolvable ??#

TIA
Richard

---

### Post by stchman on 2008-07-05
> **Richard-g8jvm said:**
> Yes I've read the sticky bit.

I'm using a AMD dual core Athlon , I'm begining to wish I'd bought a intel dual core thing.
I need to install netbeans, the package off the sun site wont load as it needs jdk.
all the package bundles from Sun will not install, they just hang during install.
Following the info on the stick bit I get

NetBeans cannot be installed on your computer type (amd64)

Either the application requires special hardware features or the vendor decided to not support your computer type.

I moved from Mandriva due to a bug effecting FFT, I'm now wondering if I've jumped from the frying into the fire ?

Is unbutu using 32bit libs for everything ?

theres only a few libs in /lib64 and a lot of lib32 


Is tghis resolvable ??#

TIA
Richard

If you want Netbeans then use the one in the repos.  The version in the repos is 6.

```
sudo apt-get install netbeans
```

---

### Post by Kilz on 2008-07-05
> **Richard-g8jvm said:**
> Yes I've read the sticky bit.

I'm using a AMD dual core Athlon , I'm begining to wish I'd bought a intel dual core thing.


The intel chip and the AMD one use the exact same Ubuntu. There is no difference.

---

### Post by jespdj on 2008-07-06
I'm running NetBeans 6.1 (downloaded from the NetBeans website) on 64-bit Ubuntu 8.04 without any problems.

First, you ofcourse need to have Java installed. Install, for example, Sun JDK 6. You don't need to download Java from Sun's website and try to install it manually. Just get it from the Ubuntu repository:
```
sudo apt-get install sun-java6-jdk
```

Then run the NetBeans installer.

---

