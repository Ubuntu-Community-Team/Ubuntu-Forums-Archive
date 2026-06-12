---
title: "Xchm won't view CHM files!"
date: 2005-08-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by front243 on 2005-08-27
Hi,

I have tried to install the xchm package, but this far I have been unable to view any CHM files with it!

I have tried I think at least 10 different chm files without luck.

I did a search on this forum, and there was one more with the same problem, so do anybody know if I need to configure anything or are there any alternatives to xchm on AMD64.

I noticed in my search there was a link to a gnochm deb-package, but that was for i386 architecture.

---

### Post by Corbelius on 2005-08-28
[http://tamir.nooms.de/wiki/doku.php?id=packages](http://tamir.nooms.de/wiki/doku.php?id=packages)

The request has been made, tomorrow tries to compile it ;)

---

### Post by front243 on 2005-08-28
[QUOTE=Corbelius][http://tamir.nooms.de/wiki/doku.php?id=packages](http://tamir.nooms.de/wiki/doku.php?id=packages)

The request has been made, tomorrow tries to compile it ;)[/QUOTE]
 Thank you very much! I will keep my eyes open for it :)

---

### Post by mariguango on 2005-09-06
I found the same problem with xCHM, but i don't find this package in your repository. May be i search in wrong place?  :???:

---

### Post by casperl on 2006-10-23
Had a similar problem:

[http://xchm.sourceforge.net/faq.html]("http://xchm.sourceforge.net/faq.html")

[INDENT]Q: xCHM displays the HTML source code of the pages instead of properly rendering it. Can I fix this? 

A: That depends. The problem might be that an application such as Crossover Office has already registered the .chm extension in your ~/.mime.types file. Most likely that can be solved by commenting out the relevant lines.[/INDENT]

I prefer a new app for Dapper : gnochm

[INDENT]**sudo apt-get gnochm**[/INDENT]

---

