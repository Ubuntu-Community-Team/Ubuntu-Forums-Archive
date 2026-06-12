---
title: "kernel panic"
date: 2006-05-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by parsival on 2006-05-29
Hi guys.

kbubtu 6.06 on a 4 cpu opteron machine

kernel panic: not syncing     --  uncorrected machine error.


someone told me that I could turn off this machine checking. How can I do 
that? is it a good idea?

Bye
Rob

---

### Post by Ptero-4 on 2006-05-29
Are you sure you're running the smp kernel? Maybe using a regular kernel for monoprocessor machines on a dual or quadprocessor system causes unexpected results.

---

### Post by parsival on 2006-05-29
No -- I am not sure. I just assumed that the ios image would have an smp kernel. I am looking for some release notes now.

Bye

---

### Post by parsival on 2006-05-29
I entered a boot parameter --  nomce -- and now it all works!

Bye

---

