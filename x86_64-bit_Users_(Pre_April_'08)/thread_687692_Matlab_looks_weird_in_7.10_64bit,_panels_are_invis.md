---
title: "Matlab looks weird in 7.10 64bit, panels are invisible"
date: 2008-02-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by PureW on 2008-02-04
Hello, I have Ubuntu 7.10 64bit, and I have some trouble with Matlab. Specifically things being invisible. If you look at this image:
[[img]http://pici.se/thumbs/t_EyigXAKnk.gif[/img]](http://pici.se/204211)
You'll see that it differs from this screenshot: (It's from a mac, but you should get the idea.
[link](http://mac.softpedia.com/screenshots/13-555_3.png)

The File, etc, menu's are there, just invisible. What causes this? Could it be Compiz, everything else works?

---

### Post by kbless7 on 2008-02-04
I had the same problem when I installed my matlab. The problem is matlab uses the wrong java. If you type "java -version" in the command window it will probably say java 5 when your most likely using java 6. If you run the following code before you start matlab it should fix it. It just exports your version of java to matlab. You might have to change it slightly. Just make sure that it point to your location of java.

```
export MATLAB_JAVA=/usr/lib/jvm/java-6-sun/jre
```

-Matt

P.S.  You can refer to this thread for a more in depth version.   [http://ubuntuforums.org/showthread.php?t=672625&highlight=kbless7&page=3](http://ubuntuforums.org/showthread.php?t=672625&highlight=kbless7&page=3)

---

### Post by PureW on 2008-02-05
Thank you, that did the trick!

---

### Post by kbless7 on 2008-02-05
> **PureW said:**
> Thank you, that did the trick!


Glad to hear. Enjoy the powers of matlab. :)

---

