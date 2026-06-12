---
title: "Metacity's close button"
date: 2005-11-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by henriquemaia on 2005-11-21
Hello,

I was just wondering: is there a way of making metacity's close button behave like MacOS close button?

I have searched on the internet, with no luck. I removed it on gconf, but this is not very practical.

Thanks in advance,
Henrique

---

### Post by lusepuster on 2005-11-22
What do you mean by 'like the MacOS close button'?

---

### Post by henriquemaia on 2005-11-22
When you press it, it does not 'closes' the application, rather it just hides it from you, staying open on the dock.

For me, this is the way it works best. It's rather annoying when, by mistake or other reason, you press the close button of OpenOffice and... it closes it. Specially when you have 1GB or more of ram.

---

### Post by ssam on 2005-11-22
there is a hack somewhere to keep openoffice in ram when you are not using it, and similar hacks for a few other programs.

you should notice that openoffice starts much faster after the first time you run it, as lots of stuff stays in cache.

---

### Post by Ptero-4 on 2005-11-22
That's impossible to implement in Gnome. To implement it you need two things. A way to force an app centric window operation and a instance container. The way of forcing that behavior have to be implemented in metacity, currently there's an option in gconf to trigger that behavior but haven't been implemented yet (it exist since gnome 2.2 but days that its non-functional and its benn like that all the way to gnome 2.12). And the instance container is a global menubar (the MacOS/OS X global menubar is the instance container for those OS's, and no the Dock isn't related to those functions), but due to the favoritism toward Windoze shown by SOME key developers in the gnome dev team it's unlickely that will happen. Currently your best option is OS X.

---

### Post by henriquemaia on 2005-11-22
Thanks for your reply. Very enlightening.

Oh, well, I have to «adjust» myself to what I have. Under KDE, at least I think, you can disable the close button. It's rather strange that a simple app like **alltray** can make the close button work the way I like it and metacity don't. Surely I can use **alltray** for every app, but I was just trying to know if I could do this with what comes by default in gnome.

Anyway, I appreciated your reply a lot. Thanks!

---

