---
title: "How do I remove opera so I can try a clean install"
date: 2008-02-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by reverend1313 on 2008-02-02
Total newbie question. I totally screwed up my Opera install trying to get flash to work. Whats the best practice for completly removing a program.. such as opera.

---

### Post by Kilz on 2008-02-02
That depends on how it was installed. Was it a deb file or another type of file?

---

### Post by reverend1313 on 2008-02-02
Yeah I just installed it from a DEB file, I tried to do the little add/remove program but it wont let me remove the check box from the Opera listing.

---

### Post by Kilz on 2008-02-02
There are other ways of removing software. You can search in Synaptic , find the software, click on the box and select uninstall. [Here is a good page to learn about Synaptic.]("http://www.monkeyblog.org/ubuntu/installing/") You can also use the terminal
```
sudo apt-get remove opera
``` should uninstall opera.

---

### Post by zvacet on 2008-02-02
Before you remove it maybe you want to save your addressbook and bookmarks.Just export them in your home directory or on Desktop.After that open your **home directory>view>show hidden files>.opera.**Delete that folder,because it contains Opera settings.If you want to install Opera again and add flash plugin read [this](http://www.opera.com/linux/docs/plugins/install/#java).I know it is pointed to Java but if you look better you will find instructions for flash.

---

### Post by zvacet on 2008-02-02
Forgot to ask wich version do you run?I know that 9.25 have issues with flash but if you upgrading to 9.5 beta solve that issue.

---

### Post by reverend1313 on 2008-02-02
I'm running the new 9.50 64bit alpha. Ill go give that a try in a sec.

---

### Post by reverend1313 on 2008-02-02
Sweet thanks, that worked. Uninstalled it and installed the latest alpha release and flash loves me again ;).

---

### Post by rpwdh on 2008-05-26
> **reverend1313 said:**
> Total newbie question. I totally screwed up my Opera install trying to get flash to work. Whats the best practice for completly removing a program.. such as opera.

Thanks for asking the question... I did the same thing!

---

