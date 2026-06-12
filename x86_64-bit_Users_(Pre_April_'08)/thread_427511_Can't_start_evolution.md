---
title: "Can't start evolution"
date: 2007-04-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by Konstantin.Solomatov on 2007-04-29
Hello,

I have 7.04 amd64 installed on my PC, when I try starting evolution it doesn't start. When I look to the logs I find errors:
> 
Apr 29 22:26:24 kostik-desktop kernel: [11443.549897] evolution[12011]: segfault at 0000000000000000 rip 00002b6899a27092 rsp 00007fff18405458 error 4


Have anyone had something like this? Do you know any workaround for it?

When I start evolution from live cd everything seems ok.

---

### Post by kuja on 2007-04-29
Well, a segmentation fault almost always means theres a bug in the program AFAIK (well, it can be caused by hardware too, especially if the CPU is overclocked) I reccommend filing a bug report.

---

### Post by GSF1200S on 2007-05-03
> **kuja said:**
> Well, a segmentation fault almost always means theres a bug in the program AFAIK (well, it can be caused by hardware too, especially if the CPU is overclocked) I reccommend filing a bug report.

I have this problem in KDE, with any and all programs at random times. Sometimes, right after bootup, firefox, evolution (i know its GNOME), and amarok wont load. Just gives me a segfault. I bring this up even though im on a 32 bit system simply because it doesnt seem related to the system. My laptop is bone stock, and even add/remove programs (adept) will give me a segfault. 

GNOME freezes all the time, KDE wont load apps.. Im getting tired of this.. I guess I might as well try XFCE...

---

### Post by qrdl on 2007-05-03
> **Konstantin.Solomatov said:**
> Hello,

I have 7.04 amd64 installed on my PC, when I try starting evolution it doesn't start. When I look to the logs I find errors:


Have anyone had something like this? Do you know any workaround for it?

When I start evolution from live cd everything seems ok.

I had it in 7.04 and 6.10, segfault is caused by buggy plugins (IMHO). First of all start evolution in terminal and look at the output. You'll see some debug info about spamasassin, webcal etc. If so you can try to start evo in terminal with --disable-eplugin option. This disables loading of plugins (also try evolution --help to see the full list of options). In my case it helped, then you should create your mail account. Close evo and start it normally - it must work.

-----------------------
&#1055;&#1088;&#1080;&#1074;&#1077;&#1090; &#1079;&#1077;&#1084;&#1083;&#1103;&#1082;&#1072;&#1084;!

---

### Post by Konstantin.Solomatov on 2007-05-10
2qrdl. 
Thanks, it helped.

---

### Post by msghaleb on 2008-05-05
Hi everyone,

I have the same problem.

when I used --disable-eplugin it works.

But I'd like to know why is that and which plugin should we disable to make it work as it should?

Thanks for the help.

MG

---

