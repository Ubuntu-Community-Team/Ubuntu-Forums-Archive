---
title: "Wine program to recognize another wine program"
date: 2015-06-04
forum: Wine
---

### Post by erick10 on 2015-06-04
[CENTER]
[/CENTER]
[SIZE=6][SIZE=3]Hello,
As the title suggests, I need one program to interact with another.

[/SIZE][/SIZE][SIZE=6][SIZE=3]I've been told that how wine works is that they run in different posix threads or what not, and if that's true; can I run both of those programs in one thread?

Anyways, I would like to hear a solution. Thank you.
[/SIZE]
[/SIZE]

---

### Post by TheFu on 2015-06-05
Every process has at least 1 thread. Every running program has at least 1 process. 
No, you cannot run 2 programs in 1 thread.  But I don't think that has anything to do with what you want to achieve. 

Please add specifics to your question.

---

