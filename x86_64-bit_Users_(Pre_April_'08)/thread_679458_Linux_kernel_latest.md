---
title: "Linux kernel latest"
date: 2008-01-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by enoughsaid05 on 2008-01-27
Read that the latest stable linux version 2.6.24 has been released. Wonder when the server is going to upload it?

---

### Post by Kilz on 2008-01-27
> **enoughsaid05 said:**
> Read that the latest stable linux version 2.6.24 has been released. Wonder when the server is going to upload it?

The kernel that is released with a version is what usually stays with a version. I am using Feisty and it has the 2.6.20 kernel still. But you can build one yourself. Here are 2 good threads.

[http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)
[http://ubuntuforums.org/showpost.php?p=1174954&postcount=507](http://ubuntuforums.org/showpost.php?p=1174954&postcount=507)

There is also Kernelcheck that will do most of the work of building automatically.

[http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

---

### Post by Yellow Pasque on 2008-01-27
I've been experimenting with distros lately, in the never-ending quest to strike a balance between available features and stability.  I compiled and ran the rc4 version of the new kernel for a little bit, but it was apparent that it still needed work. During that time, I set up an Arch Linux system on a spare disk as a daily driver. Arch is an awesome distro, but its repository can't compare to Debian/Ubuntu, and when you want to build from source, it's nice to have a large repo to pull dependencies from.
So I rolled my own kernel, and the 2.6.24 kernel rocks. It's "tickless", so it keeps the processor utilization down nicely plus all of the other features - ([http://www.kernel.org/pub/linux/kernel/v2.6/ChangeLog-2.6.24](http://www.kernel.org/pub/linux/kernel/v2.6/ChangeLog-2.6.24)).  If you'd like to do the same, check out "The old-fashioned Debian Way" method on this guide: [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

---

