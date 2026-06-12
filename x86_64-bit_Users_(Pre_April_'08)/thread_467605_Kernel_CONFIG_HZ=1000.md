---
title: "Kernel: CONFIG_HZ=1000"
date: 2007-06-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by kidders on 2007-06-07
Hi guys,

I'm wondering if anyone has anything earth-shattering to say about setting Ubuntu's kernel timer frequency to 1,000 Hz.

I recently bought my first dual core AMD64 (a 4600+), and I've been looking for ways to make my Ubuntu a bit leaner & meaner. I came to Ubuntu via Gentoo (which is maybe a slightly strange transition to make!), so I'm sort of accustomed to trying to find ways of improving my box's performance.

I'm finding it quite hard to separate the crap from the truth when it comes to the negative side-effects of setting CONFIG_HZ=1000 on a dual core processor. Since I did it (about an hour ago), I've noticed *dramatic* positive ones. :-) I'd really appreciate your comments.

---

### Post by RAOF on 2007-06-08
CONFIG_HZ=1000 shouldn't really have any noticable difference unless you have some really latency-critical apps (like realtime audio, where you want the smallest possible buffers).

You should end up with slightly lower latency (but not substantially lower) and also slightly lower maximum througput, since there'll be more interruptions to your processes.  It'll also reduce battery life & increase heat dissipation when the CPU is idle, but you probably don't care about that.

Without hard data (= benchmarks), I'm skeptical about any improved performance you are seeing.  Human beings are extremely good at seeing what they expect to see :).

---

### Post by kidders on 2007-06-08
> **RAOF said:**
> Human beings are extremely good at seeing what they expect to see :).I'm always very conscious of the placebo effect when I tweak things, which is why I was surprised by the degree of the difference. For instance, my Firefox, bluetooth kb/mouse, and one or two interface-related things seem much less sluggish. I wonder if I'd still feel any difference if I randomised my grub's default kernel selection hehe.

Thanks for your comments. :-) I was mostly curious about whether I might do any damage ... you see, I don't run anything that would get a major boost out of lots & lots of interrupts.

**Edit:** Oh heck... you're a developer! Thanks for your time!

---

