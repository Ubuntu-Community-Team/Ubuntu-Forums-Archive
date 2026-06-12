---
title: "More CPU for certain processes"
date: 2009-11-11
forum: x86 64-bit Users
---

### Post by Sin@Sin-Sacrifice on 2009-11-11
I am toying around with encoding video and such and wish to see some of it go faster. I'm not too familiar with how all of it works but I have a basic concept of priorities and threading and how information is processed and used by the CPU. I noticed, though, that most of my software is only using about 30% of each core at highest priority and was wondering if there is a way I can tell it to use more. I may be missing something in my understanding of how things work here or in all of this computer stuff entirely but maybe someone here can enlighten me? Is there a way to tell a process to use up more of the resources?

---

### Post by dcstar on 2009-11-11
> **Sin@Sin-Sacrifice said:**
> I am toying around with encoding video and such and wish to see some of it go faster. I'm not too familiar with how all of it works but I have a basic concept of priorities and threading and how information is processed and used by the CPU. I noticed, though, that most of my software is only using about 30% of each core at highest priority and was wondering if there is a way I can tell it to use more. I may be missing something in my understanding of how things work here or in all of this computer stuff entirely but maybe someone here can enlighten me? Is there a way to tell a process to use up more of the resources?

```
man nice
```

---

### Post by Sin@Sin-Sacrifice on 2009-11-11
Thank you very much. I wondered about nice. You're a saint.

---

### Post by lensman3 on 2009-11-13
By the way you can nice a nice.  So it is possible to "nice nice nice cp something_from something_to".  Each nice, I think, sets the priority down 4 points, so 3 nice's in a row will move it down 12.

---

### Post by Sin@Sin-Sacrifice on 2009-11-15
According to what I've read I would much rather ```
nice -n -20 ffmpeg...etc
``` That command gave ffmpeg almost 90% of my quad core while doing nothing else. I converted a movie from ogv @ 954MB to an mp4 @ 318MB and almost equal quality in 5 min. I was quite impressed. I may try to nice the nice in that manner though... see what happens.

---

