---
title: "kmsg error causing crash"
date: 2008-11-25
forum: x86 64-bit Users
---

### Post by phantomcircuit on 2008-11-25
My system eventually hangs on a dd command reading from /proc/kmsg.

/proc/kmsg contains the following repeated infinitely.

> <3>[ 5724.547216] bad: scheduling from the idle thread!
<4>[ 5724.547218] Pid: 0, comm: swapper Tainted: P          2.6.27-7-generic #1
<4>[ 5724.547220] 
<4>[ 5724.547220] Call Trace:
<4>[ 5724.547223]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40
<4>[ 5724.547225]  [<ffffffff8023c436>] dequeue_task+0x96/0xe0
<4>[ 5724.547227]  [<ffffffff8023c4d3>] deactivate_task+0x23/0x30
<4>[ 5724.547230]  [<ffffffff80500685>] thread_return+0x108/0x3c3
<4>[ 5724.547232]  [<ffffffff8026d12e>] ? sched_clock_idle_wakeup_event+0xe/0x10
<4>[ 5724.547235]  [<ffffffff80210ecd>] cpu_idle+0xad/0x110
<4>[ 5724.547237]  [<ffffffff804f0446>] rest_init+0x66/0x70
<4>[ 5724.547239]

---

