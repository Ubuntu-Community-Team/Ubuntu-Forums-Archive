---
title: "compiling and installing new wine version (updating files)"
date: 2008-03-18
forum: Wine
---

### Post by Mr.Johnny on 2008-03-18
I usually compile and install the latest wine myself, but I'm not sure if the files in the .wine directory are updated automatically.

Is there anything I should do ensure that wine's native files are updated/replaced with the new version ones?

Because I noticed an app still had problems when I installed 0.9.57, but deleting the .wine folder and reinstalling the app fixed it, therefore my question.

(I hope there's a way, because it's a mess having to reinstall everything when you upgrade wine)

thanks

---

### Post by Mr.Johnny on 2008-03-19
anybody?

---

### Post by happyhamster on 2008-03-19
First make sure the previous wine is unistalled before installing the compiled version. After installing wine, you can update it to use the previously installed programs with the command:

wineprefixcreate

---

### Post by Mr.Johnny on 2008-03-21
perfect ;)

---

