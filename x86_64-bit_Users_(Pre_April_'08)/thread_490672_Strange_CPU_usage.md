---
title: "Strange CPU usage?"
date: 2007-07-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by elfstone214 on 2007-07-02
I was previously using 32bit Ubuntu Feisty and just recently had to switch to amd64 Feisty. I have noticed that whenever I open my 64bit engineering applications the CPU load now (with amd64) reaches nearly 100%. With 32bit Ubuntu the CPU load was very small compared to now. Is this normal? I am wondering if the OS is simply using the CPU more efficiently meaning using all the resources available or if there is actually something wrong? I had a similar problem in my laptop where Ubuntu was sucking up too much CPU power for no reason.

I have a 64bit CPU (Core 2 Duo running at 3.4GHz) with 4gig RAM and I am using 2.6.20-16-generic kernel

---

### Post by dabl on 2007-07-03
In a console window, enter```
 top
``` and let's see what is using all of your CPU bandwidth.

---

### Post by Mr_bleu on 2007-07-03
I ran the "top" command in terminal and get gzip using 75% cpu usage?  If I click on  system monitor, gzip isn't even listed as sleeping.

---

### Post by dabl on 2007-07-03
Interesting!

Well, I'm no guru, but you don't need gzip running with 1% of your CPU, much less 75%! So there's a clue for you!

:)

---

