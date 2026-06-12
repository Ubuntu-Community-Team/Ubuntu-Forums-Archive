---
title: "Boot Problems"
date: 2007-10-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by MadhavS on 2007-10-22
I have been running 64-bit Gutsy for a few days now (c'mon, it was released last thursday) and only today I ran into a problem.

The last modification did to my system before this was in my 32-bit gutsy ( i am running windows, gutsy 32bit, and gutsy 64 bit), in which i mounted the volume of my 64 bit gutsy.

However, when i booted today, it finished about 5% of the loading bar before it displayed this message and stopped working:

init: unable to execute "/bin/sh" for rcS: No such file or directory
init: rcS main process (2639) terminated with status 255
init: Unable to execute "/bin/sh" for rc-default: No such file or directory
init: rc-default main process (2640) terminated with status 255

Can anyone help me out please? Thanks in advance.

---

### Post by ACLerok on 2007-10-23
Out of curiousity, what was the reason that you installed both the 32-bit and 64-bit versions?  Also, why did you decide to mount your 64-bit drive in your 32-bit OS? 

Did you make sure that your 32-bit version unmounted the 64-bit drive correctly?  Can you boot into recovery mode?

---

### Post by MadhavS on 2007-10-24
I cannot boot into 64-bit recovery mode, it still ends up with the same error message. How should i check if the 64-bit volume mounted in my 32-bit has unmounted properly?

---

### Post by ACLerok on 2007-10-25
If you type "mount" in a terminal window without any arguments, it'll show you all of the partitions/drives that are currently mounted.  

try doing what they said in this thread:

[http://ubuntuforums.org/archive/index.php/t-390146.html]("http://ubuntuforums.org/archive/index.php/t-390146.html")

---

