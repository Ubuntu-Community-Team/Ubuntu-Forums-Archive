---
title: "Freeze after RAM upgrade"
date: 2008-07-13
forum: x86 64-bit Users
---

### Post by ephracis on 2008-07-13
Hi there,

I am using Ubuntu Hardy Heron (8.04) and I just added 2 more gig of RAM (now I have a total of 5 gig).

When I fire up VMware the computer completely hangs after a while (actually while reverting a snapshot of one of the machines).

So, my question now is:

Is there a way to start an application (in my case VMware) in some sort of sandbox where I can debug it, and prevent it from hanging the whole system? Maybe I will get enough information to be able to file a bug report.

---

### Post by goexplode on 2008-07-13
Can you post any kind of error logs?

I'd be more concerned about it being a faulty memory stick, this can be quite common with new memory. Have you tried running Memtest86+? That should give you an idea of whether it is a problem with the memory stick. There should be an entry in your Grub boot menu for Memtest86+ (it comes installed by default, I believe). Let it run for a long time, preferably overnight, since one or two passes probably won't be enough. If it does find any errors then it will let you know.

If you come back with no errors from Memtest86+, then it is possible that it could be a problem with VMware, and it may be possible to troubleshoot from there.

---

### Post by ephracis on 2008-07-14
I just did a memtest with 5 passes and 0 errors. So it still seems that it is an software error.

I am not sure if it's specific to vmware, tho. It may be just a symptom. I've noticed freezes without vmware running. Though they are very rare and still, I've never been able to run vmware without a freeze within a short period of time.

What error logs should I look at?

---

### Post by Sef on 2008-07-14
> I just did a memtest with 5 passes and 0 errors. So it still seems that it is an software error.

You should run it about 8 hours.

---

### Post by ephracis on 2008-07-14
So that's the help I get? I ran it for 5 but I should've run it for 8? Well, just to prove you wrong I will run it again tonight and I will run it for 10 passes and I bet there will be no errors.

So, just to cut some time: when the test will show us that the problem is in the software world how can I debug this freeze?

---

### Post by goexplode on 2008-07-14
> When I fire up VMware the computer completely hangs after a while (actually while reverting a snapshot of one of the machines).

Does the hanging only occur with a specific virtual machine? Have you tried creating a clean virtual machine and putting it through the regular uses and had issues with hanging?

> I am not sure if it's specific to vmware, tho. It may be just a symptom. I've noticed freezes without vmware running. Though they are very rare and still, I've never been able to run vmware without a freeze within a short period of time.

What error logs should I look at? 

I think /var/log/messages would be a good start, fire up gnome-system-log and have a look.

Although, if the freezing still occurs even without VMware running, then it is more likely that the problems may be resulting from faulty hardware. If you have a second machine that uses the same type of memory then you could always just stick the new modules in it to see if you have any problems. If you get problems there then you know the memory sticks are probably bad.

I think there is still some important information that might also be helpful, such as your motherboard manufacturer and model; and the brand, size, and speed of your memory. Also, are you using a dual channel motherboard?

Troubleshooting memory can be tricky. I recently tried to upgrade some memory in my system, I thought I had got some bad sticks too, but it turned out that my BIOS wasn't playing well with the dual channel configuration.

You can always try exchanging the memory.

---

