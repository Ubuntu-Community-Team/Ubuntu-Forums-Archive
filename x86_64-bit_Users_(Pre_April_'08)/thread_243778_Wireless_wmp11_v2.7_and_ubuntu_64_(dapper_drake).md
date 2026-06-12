---
title: "Wireless wmp11 v2.7 and ubuntu 64 (dapper drake)"
date: 2006-08-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by biel73 on 2006-08-25
Hello!

I have installed Ubuntu 64 on my computer. It seems that it supports by itself this wireless card, but I can't get connected.
After reading a lot of threads talking about wmp11 (in this and other forums), I have tried with ndiswrapper. It installs correctly, but continue without connection.

Any ideas?

Biel.

(sorry for my english)

---

### Post by biel73 on 2006-08-26
?

---

### Post by killkoy on 2006-08-26
What do you mean by [quote=biel73]It seems that it supports by itself this wireless card[/quote]?
What kind of network are you conecting to?
Is it encrypted?
sorry about all the questions but I need more information before i can help you

---

### Post by biel73 on 2006-08-27
Thanks for your interest, killkoy. I have solved my problem!

I was trying to use ndiswrapper with 32bits windows drivers. Luckyly a friend of mine has the same card working on a "WindowsXP 64bit edition". I have borrowed its controllers and the problem has been solved. The files needed are "BCMWL564.SYS" and "netbc564.inf"
I have followed this steps:
 1. Download and install ndiswrapper package from ubuntu webpage.
 2. Add the bcm43xx module to the blacklist-watchdog file (see [http://www.ubuntuforums.org/showthread.php?t=135921](http://www.ubuntuforums.org/showthread.php?t=135921))
 3. Use ndiswrapper (there are many examples in the forum) with the files of above. 
 4. Configure the wireless card in the networking control panel (perhaps this step is due to repeat after rebooting). 

And that's all!

If this can help somebody, but needs the files above, my email is [email]biel73@gmail.com[/email]

---

