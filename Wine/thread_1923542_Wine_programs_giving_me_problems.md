---
title: "Wine programs giving me problems"
date: 2012-02-10
forum: Wine
---

### Post by redmurdera on 2012-02-10
I have seen on youtube and googled people using ubuntu and Wine 1.2 to install this game Mu online and i have seen it working perfectly on other ubuntu computers.
I had trouble getting it to work on 1.3 beta but so i got 1.2 like others had and it runs fine now but i get no texts where i should have texts. like none at all.

any help would be greatt
thanks

---

### Post by oldos2er on 2012-02-10
Moved to Wine.

---

### Post by brpylko on 2012-02-10
Try installing allfonts through winetricks. (if this doesn't work(due to checksum error), install corefonts and tahoma)

---

### Post by forrestcupp on 2012-02-10
There are a couple of standard things you could try. First, in a terminal, try:
```
winetricks allfonts
```

Secondly, open your Wine Configuration, and click on the Libraries tab. In the dropdown box that says "New override for library:", find riched20, and click Add. Then click Apply and OK, and try the game again.

It may or may not fix it. Just know that installing allfonts will take a few minutes.

---

