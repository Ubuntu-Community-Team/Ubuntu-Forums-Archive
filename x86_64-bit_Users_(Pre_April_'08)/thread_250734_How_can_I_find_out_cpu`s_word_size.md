---
title: "How can I find out cpu`s word size?"
date: 2006-09-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by metafile on 2006-09-04
Is there any way to find out cpu`s word size, using only bash?
"uname -a" and "cat /proc/cpu" aren`t correct answers, because sometimes they don`t say anything on topic.

---

### Post by SlCKB0Y on 2006-09-05
It might help if you explain why you need to do this.

---

### Post by metafile on 2006-09-05
At first, I had to create a shell script that works differently, according to processor`s word. Then I realized, that I don`t know the way to get the information using bash.

---

### Post by kuja on 2006-09-05
```
lshw -class cpu | grep width | cut -d : -f 2
```

If lshw's cpu width is indeed the same as the word size.... then this could work.

---

