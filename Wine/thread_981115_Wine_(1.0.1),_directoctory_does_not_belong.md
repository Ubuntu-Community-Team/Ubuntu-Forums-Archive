---
title: "Wine (1.0.1), directoctory does not belong?"
date: 2008-11-13
forum: Wine
---

### Post by Refuge on 2008-11-13
I was following the steps on this website, [http://luiscosio.com/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps](http://luiscosio.com/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps) , to get my photoshop running through wine. How ever, as I do the "adobe.reg" step, my wine tells me "error: /home/ryan/.wine does not belong to you" But, it does?

How do I let wine allow me to make changes to my own wine folder?

---

### Post by cogadh on 2008-11-13
The How-To you were following did that to you. When you ran the "sudo wine" command, it gave the .wine directory root permissions, so it does not belong to you. You need to delete the .wine directory and start all over again without using sudo to run Wine (ever). To remove the .wine directory:
```
sudo rm -rf ~/.wine
```

---

### Post by Refuge on 2008-11-13
It did? How rude D:!

I'll have to find another way to get my photoshop to work then. Thanks for the help

---

### Post by cogadh on 2008-11-13
You can still use the same How-To, just don't run "sudo wine" when it tells you to. Instead, run "winecfg" to create the default Wine directories.

---

### Post by hikaricore on 2008-11-13
A simple:

> sudo chown ryan:ryan ~/.wine -R

would have done the trick, you didn't have to tell him to delete the directory :)

---

### Post by cogadh on 2008-11-14
Eh, force of habit. That solution has on my list of "standard solutions" for years now.

BTW - Nice to "see" you, its been a while.

---

