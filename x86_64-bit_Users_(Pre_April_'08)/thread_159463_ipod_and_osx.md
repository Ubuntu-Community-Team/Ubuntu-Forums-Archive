---
title: "ipod and osx"
date: 2006-04-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by dombleu on 2006-04-12
Really simple problem for wich I bet there is a very simple answer....

How in the hell can I get to *write* on my HFS+ formatted Ipod or my OSX partition.

Is HFS+ writing disabled in dapper? Because it seems that wathever I may try, thoses drives will stay read-only.

Will I have to recompile the kernel with HFS+ writing enabled???

Any clue?
](*,)

---

### Post by dombleu on 2006-04-16
Solved. In a way. 

Journalised HFS+ don't mount rw, only ro.

Moving on.

---

