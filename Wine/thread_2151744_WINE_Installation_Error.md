---
title: "WINE Installation Error"
date: 2013-06-05
forum: Wine
---

### Post by miotklad on 2013-06-05
I'm new to using Ubuntu and got recommended a download which was infact this program (WINE) 

After going on the website and looking on YouTube on how to install it I had a go and mutiple times I have got an error message and have looked for a fix for this problem, I still can't find one.  

I am using the version of Ubuntu 12.04 and the error code that I get when trying to install is - 

```
The following packages have unmet dependencies:
wine1.4: PreDepends: dpkg (>= 1.15.7.2~) but 1.16.1.2ubuntu7.1 is to be installed
         Depends: libc6 (>= 2.14) but 2.15-0ubuntu10.4 is to be installed
         Depends: wine1.4-amd64 (= 1.4.1-0ubuntu1~precise1~ppa4) but 1.4.1-0ubuntu1~precise1~ppa4 is to be installed
         Depends: wine1.4-i386 (= 1.4.1-0ubuntu1~precise1~ppa4) but it is a virtual package
```

Many thanks for your help!

---

### Post by monkeybrain2012 on 2013-06-05
I don't know what the Youtube video tells you, But the easiest way is to simply install it from the Software Centre, just locate Wine and then click to install and that's it.

---

### Post by miotklad on 2013-06-05
> **monkeybrain2012 said:**
> I don't know what the Youtube video tells you, But the easiest way is to simply install it from the Software Centre, just locate Wine and then click to install and that's it.

Done that and via the terminal. On both occastions I get that error message.

---

### Post by Annadin on 2013-06-05
I would just go to [http://www.winehq.org/download](http://www.winehq.org/download) , and upack the package using sudo dpkg <pkgname>, thats how i ended up having to do it

---

### Post by monkeybrain2012 on 2013-06-05
Instead of installing Wine1.4, You should just install Wine, there may be a minor version difference,

---

