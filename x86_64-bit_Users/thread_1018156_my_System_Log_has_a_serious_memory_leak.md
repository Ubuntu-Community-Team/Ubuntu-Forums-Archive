---
title: "my System Log has a serious memory leak"
date: 2008-12-21
forum: x86 64-bit Users
---

### Post by ShadowTek on 2008-12-21
For the past day or two, the System Log has frozen every time I tried to 
access it from the GUI. This time, I first started System Monitor, and 
then watched the process **gnome-system-log** as its CPU usage hovered around 24%, while its memory usage endlessly jumped up at over 100MB per second.

I have rebooted since it first happened, but there is still no change. I'm not 
sure what I could have done, other than allowing whatever Ubuntu updates have become available in the past day of so.

Has anyone else experienced this?

I'm running 8.10 AMD64, with all the latest updates.

---

### Post by bmacx on 2009-01-11
I have the exact same issue.

I am using an Intel Pentium Dual T3200 on a 32-bit system.

I don't know exactly when it started (I just noticed today) but I do recall installing updates the day before through the update manager.

Too bad I can't use the log to see what is going on.

---

### Post by Yellow Pasque on 2009-01-11
You can still access logs "the old-fashioned" way. Look at /var/log/messages to see what's happening.

---

### Post by bmacx on 2009-01-11
> **Temüjin said:**
> You can still access logs "the old-fashioned" way. Look at /var/log/messages to see what's happening.

Funny thing is..... when I access it like so 'gedit messages' all the ram gets used up in about a minute and then it crashes with this message.

GLib-ERROR (recursed) **: /build/buildd/glib2.0-2.18.2/glib/gmem.c:175: failed to allocate 16 bytes
aborting...
Aborted

---

### Post by cariboo on 2009-01-11
You can have a look at the logs in a terminal by using the following command:

```
cat /var/log/messages | less
```

Then use the space bar to scroll down.

Jim

---

### Post by bmacx on 2009-01-14
> **cariboo907 said:**
> You can have a look at the logs in a terminal by using the following command:

```
cat /var/log/messages | less
```

Then use the space bar to scroll down.

Jim

Ok, so now things are getting weirder.  Today I was able to access the gnome system log with no problem.  However, most of the history does not show up, and it only goes back to Jan 13.  I am not sure if that is normal behavior or not.  The previous messages are still archived in .gz files.  I went ahead and took your advice but instead of using messages I used messages.0.

I got the following repeated set of messages.
Jan 10 02:09:22 brians-lappy-2 kernel: [ 7383.163863] Pid: 0, comm: swapper Not tainted 2.6.27-9-generic #1
Jan 10 02:09:22 brians-lappy-2 kernel: [ 7383.163865]  [<c037c4b6>] ? printk+0x1d/0x1f
Jan 10 02:09:22 brians-lappy-2 kernel: [ 7383.163870]  [<c0122b8a>] dequeue_task_idle+0x2a/0x40
Jan 10 02:09:22 brians-lappy-2 kernel: [ 7383.163874]  [<c012107f>] dequeue_task+0xcf/0x130
Jan 10 02:09:22 brians-lappy-2 kernel: [ 7383.163878]  [<c012112a>] deactivate_task+0x1a/0x30
Jan 10 02:09:22 brians-lappy-2 kernel: [ 7383.163881]  [<c037cad3>] schedule+0x4b3/0x790
Jan 10 02:09:22 brians-lappy-2 kernel: [ 7383.163885]  [<c03810a5>] ? notifier_call_chain+0x35/0x70
Jan 10 02:09:22 brians-lappy-2 kernel: [ 7383.163900]  [<f88659da>] ? acpi_idle_enter_simple+0x18b/0x193 [processor]
Jan 10 02:09:22 brians-lappy-2 kernel: [ 7383.163912]  [<c01028cd>] cpu_idle+0xbd/0x140
Jan 10 02:09:22 brians-lappy-2 kernel: [ 7383.163912]  [<c036ee83>] rest_init+0x53/0x60

I should also mention that yesterday I did try to move the archived messages around to see if that did anything but had moved them back when I saw no change.

---

