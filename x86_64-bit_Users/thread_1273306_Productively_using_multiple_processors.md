---
title: "Productively using multiple processors"
date: 2009-09-23
forum: x86 64-bit Users
---

### Post by pcal on 2009-09-23
Hi Folks,

I'm running an AMD quad system with 64bit 9.04, and would like to make what seems like a better use of the processors.

I understand that the os allocates work between the processors as it sees fit and the application has be to multi threaded to derive the maximum benefit. However, it seems to me that it should be possible to instruct the system which processor to run any given application on. If for example, I wanted to run 2 or more instances of the same program - it should boost performance by being able to specify each instance to a different processor. Alternatively, it should be possible to allocate a desktop to a processor so that any application run on that desktop would be directed to that processor.

Is this possible in 9.04?

If not, is it a practical request to put for any future version?

Regards,

Pcal

---

### Post by timgood on 2009-09-24
I'm not sure about choosing processors for tasks, but this howto shows how to limit the amount of processors for tasks. Perhaps you could use this?
[http://www.howtoforge.com/how-to-limit-cpu-usage-of-a-process-with-cpulimit-debian-ubuntu](http://www.howtoforge.com/how-to-limit-cpu-usage-of-a-process-with-cpulimit-debian-ubuntu)

Hope this helps.

---

### Post by toupeiro on 2009-09-24
I believe what you are wanting to do is set the CPU affinity of your applications.  Unless you are very knowledgeable about how the software you are using was written, I strongly advise against this. However, if you wish to experiment, continue reading.

[http://www.cyberciti.biz/tips/setting-processor-affinity-certain-task-or-process.html](http://www.cyberciti.biz/tips/setting-processor-affinity-certain-task-or-process.html)

---

### Post by pcal on 2009-09-24
Thanks guys...

That is one interesting article! I see I have a lot of playing around to do.

Regards,

Pcal

---

