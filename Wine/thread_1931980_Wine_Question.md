---
title: "Wine Question"
date: 2012-02-26
forum: Wine
---

### Post by Coolmariorocks on 2012-02-26
Will Wine slow down my desktop computer running Ubuntu 10.10?  I'm thinking about installing wine on it but I'm scared it will slow down the computer.. note: the computer is old it was made back in 2003...

---

### Post by sir.sargento on 2012-02-26
Im pretty sure wine itself will be fine.. I think it depends more on what programs you will be using wine to run.. Wine itself is not heavy on resources but it sure would be if you are trying to use wine to run a new game or resource heavy program.

---

### Post by howefield on 2012-02-26
Thread moved to the "*Wine*" forum.

---

### Post by grahammechanical on 2012-02-26
Wine is not an emulator not is a virtual machine. You do not run the Windows operating system in Wine. So, why should it slow down your machine?

What Windows program do you want to use with Wine? If that program ran slow on a 2003 machine under Windows then it most likely run slow on a 2003 machine in Wine.

I use a windows program in Wine. It is a library reader type of program. It does not use many resources.

I have just used the top command to monitor CPU and memory usage while this program loads.

For a few seconds wine boot.exe is running using 0.5% of memory. Then that closes as wine server takes over using 0.6% of memory and 1% of CPU. And it is only active when the loaded Windows program is active.

I have 1GB memory and a 2.4GHz dual core CPU from about 2007. So, a machine with a slower CPU and less memory will show a higher percentage usage of resources. Just as in the case of having double the memory will reduce the percent memory usage figures by half.

The components of wine are only being used when the Windows program needs to interact with the Ubuntu operating system. Such as when the application window need to be re-drawn.

[http://www.winehq.org/]("http://www.winehq.org/")

Regards.

---

