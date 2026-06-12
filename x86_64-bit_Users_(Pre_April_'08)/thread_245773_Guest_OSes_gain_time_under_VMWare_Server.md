---
title: "Guest OSes gain time under VMWare Server"
date: 2006-08-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by dullroar on 2006-08-28
Under both Ubuntu and Xubuntu 6.06.1 on AMD64 when I run VMWare Server and then run a 32-bit Windows XP SP2 guest under that, the guest's (XP's) clock gains time - the more CPU intensive the processing in the guest, the more time it gains (under really heavy load you can watch the clock minutes in the XP guest go up ever 10 seconds or so). After doing research, I have made sure:

1) VMWare Tools is installed on the guest and is set to sync with the host's time.

2) The host is booted with clock=pit kernel parameter.

Neither has helped.

Has anyone else seen this? Have you fixed it? If so, how?

Thanks.

---

### Post by anotherMichael on 2006-08-28
Try setting in the following property in your virtual machine definition file (*.vmx)

tools.syncTime = "TRUE"


I had similar problem although with reverse configuration: my host at work is Win XP and Ubuntu  is the guest. 

Thre is more related info pdf whitepaper: Timekeeping in VMware
Virtual Machines avaialble somewhere from vmware website.

---

### Post by dullroar on 2006-08-28
Thanks. I have tried that. In fact, that gets set when you set VMWare Tools to sync time with the host.

This is apparently a well-known issue with 64-bit AMD processors running VMWare - [http://www.vmware.com/community/thread.jspa?threadID=51781&tstart=90](http://www.vmware.com/community/thread.jspa?threadID=51781&tstart=90). However, nothing mentioned in that thread has helped.

---

### Post by dullroar on 2006-09-09
Actually I finally figured this one out, thanks to some hints in this thread:

[http://www.vmware.com/community/thread.jspa?threadID=51781&messageID=471488#471488](http://www.vmware.com/community/thread.jspa?threadID=51781&messageID=471488#471488)

It turns out that for me disabling powernowd plus booting with kernel parm clock=pit did the trick. So if you are having this issue on AMD64 running 32-bit guests, along with making sure VMWare Tools is installed,  tools.syncTime = "TRUE" is in the .vmx file and the kernel is booted with clock=pit, you may want to try and disable powernowd (or powersaved, or cpufreqd, or whatever applies to you).

Hope it helps.

---

