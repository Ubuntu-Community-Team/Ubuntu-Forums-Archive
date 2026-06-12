---
title: "IceCat on Ubuntu 64 bit"
date: 2008-04-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by JemW on 2008-04-14
Hope I'm still posting in the right place...

Mailto links in IceCat do not work. Any ideas?

---

### Post by ikonia on 2008-04-14
can you give us more information

what version of ubuntu
what version of icecat
where you got icecat
how you installed icecat
what the error message / problem is
what you expect it to do

The question you've asked is like me saying "my food doesn't taste nice"

I've not told you what the food is, 
where I got it
how it was prepared
or why I don't like it.

---

### Post by Kilz on 2008-04-14
> **JemW said:**
> Hope I'm still posting in the right place...

Mailto links in IceCat do not work. Any ideas?

From the Common Issues section of the howto.

```
[B]
Email[/B]
You must setup what program is called for some things. There is [a post on the settings for email]("http://ubuntuforums.org/showpost.php?p=2582830&postcount=11") 
```

---

### Post by JemW on 2008-04-14
> **Kilz said:**
> From the Common Issues section of the howto.

```
[B]
Email[/B]
You must setup what program is called for some things. There is [a post on the settings for email]("http://ubuntuforums.org/showpost.php?p=2582830&postcount=11") 
```

OK, I sort of understand. I can add this to about:config, but I don't understand how to set the path to Evolution. This is my lack of Linux knowledge - I don't know where to look or what the actual filename should be. I'd be grateful if you could help me with that. Sorry...sigh...so much to learn...

---

### Post by Kilz on 2008-04-14
> **JemW said:**
> OK, I sort of understand. I can add this to about:config, but I don't understand how to set the path to Evolution. This is my lack of Linux knowledge - I don't know where to look or what the actual filename should be. I'd be grateful if you could help me with that. Sorry...sigh...so much to learn...

[this will help]("http://www.ss64.com/bash/"). Its a list of commands, one of them is which. ```
which evolution
``` will return the location of the file. applications executables are normally the name of the application in linux.
In my Feisty install its /usr/bin/evolution

---

### Post by JemW on 2008-04-14
> **Kilz said:**
> [this will help]("http://www.ss64.com/bash/"). Its a list of commands, one of them is which. ```
which evolution
``` will return the location of the file. applications executables are normally the name of the application in linux.
In my Feisty install its /usr/bin/evolution

Thanks Kilz, that worked. What are the other about:config tweaks for on that post - do I need them? And what should they point to if I do...

---

### Post by Kilz on 2008-04-14
> **JemW said:**
> Thanks Kilz, that worked. What are the other about:config tweaks for on that post - do I need them? And what should they point to if I do...

That depends on what you want and what you use.

---

