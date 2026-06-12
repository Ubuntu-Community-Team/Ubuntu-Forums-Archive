---
title: "Multi renamer for xfce"
date: 2008-06-11
forum: x86 64-bit Users
---

### Post by DachaArh on 2008-06-11
Is there some multi renamer for xubuntu that would allow me to rename several .mp3 files at once.
I need something like this :
my songs now are :
Abba - Dancing queen_www.example.com.mp3
Abba - Waterloo_www.example.com.mp3
Abba - Honey honey_www.example.com.mp3
Abba - So long_www.example.com.mp3
Abba - Money, money, money_www.example.com.mp3

and I have about 100 songs like that and I want to remove _www.example.com from all of them 
Is this possible with some application ?

thanks

---

### Post by DachaArh on 2008-06-11
I found GPrename, and it did a great job

---

### Post by Jouke74 on 2008-06-11
Under XFCE there is a tool called "Bulk Rename". Unless you de-installed it, I think it is most likely to be found under the accessories menu. As a precaution and from my own experience I suggest you make a backup before you start :lolflag:

---

### Post by nunki on 2008-06-11
From a terminal, navigate to the mp3 directory and type something like
```

ls *.mp3 | while read FILE; do
>a=`echo $FILE | sed 's/_www.example.com//'`
>echo "Moving $FILE -> $a"
>mv "$FILE" "$a"
>done

```

---

