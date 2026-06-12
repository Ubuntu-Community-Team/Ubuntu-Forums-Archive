---
title: "Newbie Time"
date: 2008-04-16
forum: Wine
---

### Post by JemW on 2008-04-16
I just know I'm going to make a fool of myself here, but here goes anyway:

I just successfully installed Wine 0.9.59 on 7.10 32 bit. I have never used it before and I'm new to Ubuntu (and to Linux). I picked up some advice elsewhere on how to install a Windows XP app by running **wine 'path/applicationinstall.exe'** in a Terminal, This seemed to work and the application started. I then closed the app...and, hmmm...I'm missing something here - I can't find it! Where did it install it? I've tried browsing the Wine c: Drive...

Thanks.

---

### Post by mbadawi23 on 2008-04-16
It should be under Applications->Wine->Programs

and wine has a fake windows c drive usually under your home folder:
```
cd ~/.wine/drive_c/
```

---

### Post by JemW on 2008-04-16
> **mbadawi23 said:**
> It should be under Applications->Wine->Programs

and wine has a fake windows c drive usually under your home folder:
```
cd ~/.wine/drive_c/
```

Nothing under Applications | Wine | Programs

I can change into that fake drive, but how do I then create a Menu Shortcut?

---

### Post by mbadawi23 on 2008-04-18
So you have the programs available in the fake folder?

---

