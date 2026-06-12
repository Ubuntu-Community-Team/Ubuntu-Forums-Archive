---
title: "init Apache2 simply don't works"
date: 2007-06-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by marcs on 2007-06-08
It's no the first time that I'm trying to install apache2 and php on ubuntu, on an old installation of feisty all worked fine. Now i've made a fresh new installation of feisty and upgraded all the packages at first install today. Then i've tried to install apache2 and php5 in the common way with aptitude... all worked fine, but now when i try to init apache2 with sudo /etc/init.d/apache2 start i got nothing no error message or a warning... nothing... but apache2 don't start, but no error message, so i'm totally clueless.

Anybody have an idea ? It's some bug related to the latest updates ?
Tell me what informations or config files or log files you need.

i'll keep looking on this problem and send the solution if i'll find it.

thx for your time & support.

oh i'm using a 64bit version, so i posted here...

---

### Post by kidders on 2007-06-09
Hi there,

> **marcs said:**
> i'm using a 64bit version, so i posted here.

This is unlikely to be a 64-bit issue. Your system logs (or apache's logs) will probably (hopefully!) contain some explanation for why apache won't start. Watch for changes as you try to start apache, and post anything you think might be relevant. With luck, its a configuration issue.

---

### Post by Kilz on 2007-06-09
You might want to disable php, or any loaded modules. Then see if apache starts. Then slowly add them to see where the problem lies.

---

### Post by marcs on 2007-06-11
> **kidders said:**
> Hi there,



This is unlikely to be a 64-bit issue. Your system logs (or apache's logs) will probably (hopefully!) contain some explanation for why apache won't start. Watch for changes as you try to start apache, and post anything you think might be relevant. With luck, its a configuration issue.

Hi the problem is that the logs are totally blank. I've already check them.

> **Kilz said:**
> You might want to disable php, or any loaded modules. Then see if apache starts. Then slowly add them to see where the problem lies.

I'll try it that way.

---

### Post by marcs on 2007-06-12
Solved.

I've removed the Apache2 package with synaptic selecting the option for remove all files including the configuration ones. Then i've removed with an rm the /etc/apache2/ directory. Then i've installed the package again.  

All works now. I guess it was a configuration problem. who knows ?

---

