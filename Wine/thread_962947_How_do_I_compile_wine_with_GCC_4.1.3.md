---
title: "How do I compile wine with GCC 4.1.3?"
date: 2008-10-29
forum: Wine
---

### Post by deearar on 2008-10-29
Hope this doesn't belong in the newbie forum but it's a Wine issue too so I hope you can help.

I have some software which won't install. I've been searching and reading forums, and there is a bug report on winehq that says if I compile Wine with GCC 4.1.3 then it should work.

Unfortunately I am an ubuntu newbie and don't know how to do that. I've recompiled other packages but unfortunately this time I don't know where to start.

Could someone help me or point me in the right direction? I am running Hardy.



The post I read specifically reads,
"I can confirm that the bug is fixed when I compiled wine with "./configure CC=/usr/bin/gcc-4.1"." Unfortunately I think I need step by step instructions. Should I uninstall my current Wine first?

Thanks!

---

### Post by YokoZar on 2008-10-29
> **deearar said:**
> Hope this doesn't belong in the newbie forum but it's a Wine issue too so I hope you can help.

I have some software which won't install. I've been searching and reading forums, and there is a bug report on winehq that says if I compile Wine with GCC 4.1.3 then it should work.

Unfortunately I am an ubuntu newbie and don't know how to do that. I've recompiled other packages but unfortunately this time I don't know where to start.

Could someone help me or point me in the right direction? I am running Hardy.



The post I read specifically reads,
"I can confirm that the bug is fixed when I compiled wine with "./configure CC=/usr/bin/gcc-4.1"." Unfortunately I think I need step by step instructions. Should I uninstall my current Wine first?

Thanks!
Which bug?

---

### Post by YokoZar on 2008-10-29
By the way, Hardy defaults to GCC 4.2 (Intrepid uses 4.3), and GCC 4.0 and 4.1 were the ones giving us problems in the past with copy protection.

---

### Post by deearar on 2008-10-30
Bug 13114. Comment 6

[http://bugs.winehq.org/show_bug.cgi?id=13114](http://bugs.winehq.org/show_bug.cgi?id=13114)

Basically, the bug is that if you buy DVDFab Plat, the registration code will not "take." It will accept it but upon restart of the program, it reverts back to the Trial version.

---

