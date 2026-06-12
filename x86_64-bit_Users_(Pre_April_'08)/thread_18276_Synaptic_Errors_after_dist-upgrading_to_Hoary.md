---
title: "Synaptic Errors after dist-upgrading to Hoary"
date: 2005-03-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by oc3lot on 2005-03-05
Hey all, 

I'm new to Ubuntu, but I'm REALLY impressed. I've found other distros of Linux really cumbersome but find Ubuntu easy to use and I've learned a lot so far.. Anyway, my question...

I dist-upgraded to Hoary, but whenever I use the Synaptic Package Manger to install anything, I get the following error whenever it completes:

[I]E: postfix:  subprocess post-installation script returned error exit status 1
E: at:  dependency problems - leaving unconfigured
E: mailx:  dependency problems - leaving unconfigured
E: mutt:  dependency problems - leaving unconfigured
E: anacron:  dependency problems - leaving unconfigured
E: postfix-tls:  dependency problems - leaving unconfigured
E: ubuntu-base:  dependency problems - leaving unconfigured
E: lsb:  dependency problems - leaving unconfigured[/I]

What happened? Is there anything I can do to fix this?

Any help would be appreciated. 

Cheers!

---

### Post by kubla on 2005-03-06
From the command-line you could try:

sudo apt-get install --fix-missing

Ian

---

### Post by oc3lot on 2005-03-07
Awesome.. I'll give that a try when I get home..

Thanks much!

---

