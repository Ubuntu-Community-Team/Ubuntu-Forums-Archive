---
title: "Halo!"
date: 2008-10-11
forum: Wine
---

### Post by Unanimated on 2008-10-11
Oh my god, I got Halo installed and everything, and when I run it... My monitor conveniently says "Cannot Display Video Mode." My insides almost collapsed... How do I change the video mode so my monitor can display it? It's a Dell E172FP.

---

### Post by asdfoo on 2008-10-11
> **Unanimated said:**
> Oh my god, I got Halo installed and everything, and when I run it... My monitor conveniently says "Cannot Display Video Mode." My insides almost collapsed... How do I change the video mode so my monitor can display it? It's a Dell E172FP.


Either run winecfg and set a virtual desktop to play windowed or it seems you need to pass a commandline option to halo to run at the desired refresh rate see here [http://appdb.winehq.org/appview.php?iVersionId=2720](http://appdb.winehq.org/appview.php?iVersionId=2720)

---

### Post by david_kt on 2008-10-11
> **Unanimated said:**
> Oh my god, I got Halo installed and everything, and when I run it... My monitor conveniently says "Cannot Display Video Mode." My insides almost collapsed... How do I change the video mode so my monitor can display it? It's a Dell E172FP.

According to [this]("http://ubuntuforums.org/showthread.php?t=486986") instruction, you should use wine 39 to be sure to get Halo working. But how will you install wine 39? Compile it from the source code.

If you do not know how to compile it,[this]("http://ubuntuforums.org/showthread.php?t=942269") thread will welp you to compile wine very easily, and have multiple wine at the same time. So, you could try different version of wine at the same time. I have not tried it with wine 39 though. 

DK

---

### Post by asdfoo on 2008-10-11
> **david_kt said:**
> According to [this]("http://ubuntuforums.org/showthread.php?t=486986") instruction, you should use wine 39 to be sure to get Halo working. But how will you install wine 39? Compile it from the source code.


It should work fine under latest Wine, it's reported to be ok with  1.1.5... there is no need to use a version over a year old.

---

### Post by Unanimated on 2008-10-11
I would test all that right now, but I'm having some X server mouse and keyboard issues... [http://ubuntuforums.org/showthread.php?t=937914]("http://ubuntuforums.org/showthread.php?t=937914")

---

### Post by david_kt on 2008-10-11
> **asdfoo said:**
> It should work fine under latest Wine, it's reported to be ok with  1.1.5... there is no need to use a version over a year old.

You are right, but below things make me confused:
1. they still put warning in that page:
 
```
Warning
With wine 0.9.43 + Halo locks up for many people. If this happens, revert to 0.9.42.

```

2. the "how to" still mentioned about wine 39 failing to use wine 42. At least they should update that page if it is not relevant any more, or, is it still relevant?


FYI: I still run wine 0.9.43 on 10 computers to run office 97. The most suitable wine so far and have tried many newer wines and always give me different kind of problems. So, I give up and stick with 0.9.43 until now.

DK

---

