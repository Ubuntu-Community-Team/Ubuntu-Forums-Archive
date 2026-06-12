---
title: "Problem with scandinavian letters in Skype on amd64"
date: 2007-05-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by lemonade on 2007-05-05
I was just wondering if anyone else has had problem with scandinavian characters in Skype v1.3.0.53 chat-window. Everytime I type something to chat-window scandinavian characters å,ä,ö appear as two white box-shapes (like missing character) in textarea, but messages I receive don't have this error. I haven't noticed same happening on 32-bit Ubuntu, but I have two amd64 machines affected with this same error.

I quickly tested new 1.4 alpha too, but it didn't give those white box-shapes at all - not allowing to type scandinavian letters at all.

I quickly browsed through forums but haven't found any other who has had same problem, so I was wondering if anyone other has encountered this?

---

### Post by Ledah on 2007-05-05
I had this problem with Opera :D. Try ```
sudo ln -s -T /usr/lib64/locale /usr/lib32/locale
```

---

### Post by lemonade on 2007-05-05
Thanks, that fixed it.

---

### Post by beneedict on 2007-05-23
Works wonderful also with umlauts!!
Thank's a lot!

---

