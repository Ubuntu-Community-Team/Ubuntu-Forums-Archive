---
title: "java plugin in firefox"
date: 2008-08-14
forum: x86 64-bit Users
---

### Post by jim_in_dorris on 2008-08-14
Using amd64 bit ubuntu. i have successfully installed jre1.6.0_07 32 bit java runtime, and java -version returns the version properly, but I can't get a java plugin in firefox.  I feel really stupid tonight, nothing seems to go properly. What in extreme caffeine land am I doing wrong?

---

### Post by zxscooby on 2008-08-14
Did you follow this guide?
[https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins?highlight=%2864%29%7C%28flash%29%7C%28bit%29](https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins?highlight=%2864%29%7C%28flash%29%7C%28bit%29)
Worked for me.

---

### Post by wilbbe01 on 2008-08-14
I think there is a couple choices and the one from sun doesn't work as well on 64 bit as the other one.  I don't think I used that guide and after glancing at it I think I woudl go in a different direction if I were trying to get it working on my machine right now.  I think the guide I found to be better was a post somehwere on these forums.

I don't remember the exact details but it basically went as follows.  Install both versions of the jre and the free java plugin takes care of firefox.  Then install the sun stuff and do the command to choose what "java" means at the command line to be the sun version (sorry can't think of it right now, something with defaults maybe).  If you don't program in java or anything I would say isntall the open jre stuff and you should be fine.

---

### Post by yct on 2008-08-14
If you're using Hardy, go to Applications -> Add/Remove, select "All available applications", type "flash" into the search box, check Macromedia Flash, then type "java plugin", check Icedtea Java Plugin, click Apply Changes.

---

### Post by Thelasko on 2008-08-14
> Install both versions of the jre and the free java plugin takes care of firefox. Then install the sun stuff and do the command to choose what "java" means at the command line to be the sun version (sorry can't think of it right now, something with defaults maybe). If you don't program in java or anything I would say isntall the open jre stuff and you should be fine.
I haven't been able to get that method to work.  The free Java plugin goes to the free version of Java no matter what.

I recommend installing the Open JDK plugin, along with Open JDK, and uninstalling everything else.  Sure, some sites don't work, but half of them will be fine.  I've found that having more than one version of Java on my machine just causes problems.

[My posts]("http://ubuntuforums.org/showthread.php?t=883878") on [the subject.]("http://ubuntuforums.org/showthread.php?t=880764")

---

### Post by wilbbe01 on 2008-08-14
The reason I wanted the sun version was for programming reasons, otherwise I would have used the free one only as well.  The code I was mentioning earlier which would allow you to select what "java" and "javac" mean at the commandline is as follows.

```
sudo update-alternatives --config java
```

You could run the above command to verify other things as well like javac.

I think it always uses the free plugin even with "java" calling the sun version, I never looked to be sure, but my java only worked in browsers when I had the free one, and I wasn't about to use the free stuff for my programming.  Installing them both never seemed to cause any problems for me.

---

### Post by Thelasko on 2008-08-14
I have had a breakthrough with Java tonight.  [Please read my thread.]("http://ubuntuforums.org/showthread.php?t=890143")

---

