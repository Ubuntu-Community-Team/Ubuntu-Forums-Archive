---
title: "Problems running Brain Workshop"
date: 2013-01-19
forum: Wine
---

### Post by Petkus on 2013-01-19
Hello!


With help of Wine I installed Brain Workshop, but it looks like this when I launch it - [http://i.imgur.com/zQsXK.png](http://i.imgur.com/zQsXK.png)
Otherwise, game is running just fine.
What causes letters to look so bad?


Later I tried to install that program with different Wine (playonLinux), but it didn't help and there was the same problem.

---

### Post by Toz on 2013-01-23
Bug report [here]("http://bugs.winehq.org/show_bug.cgi?id=30506").

Apparently there is a Linux version ([http://sourceforge.net/projects/brainworkshop/?source=dlp]("http://sourceforge.net/projects/brainworkshop/?source=dlp")). Just tested it and it works. Unzip and execute with:
```
python brainworkshop.pyw
```

---

