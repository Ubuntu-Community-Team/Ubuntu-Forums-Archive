---
title: "Java and Iceweasel"
date: 2007-09-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by Seisen on 2007-09-27
I am trying to get Java to verify on Java.com. I installed java by using this link here [https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins?highlight=%28amd64%29]("https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins?highlight=%28amd64%29")
Flash works fine and I installed the iceweasel.tar.gz file version 2.0.0.6. I have done the about:config and still nothing. I am stumped on why it isn't working.

---

### Post by Kilz on 2007-09-27
Where did you install iceweasel to? Could you also please tell me where you got iceweasel 2.0.0.6?

---

### Post by Seisen on 2007-09-27
Same location as if I had installed Firefox according to that link that I gave. I got it from here [http://gnuzilla.gnu.org/download/]("http://gnuzilla.gnu.org/download/")

---

### Post by Kilz on 2007-09-27
Thanks I wasnt aware that 2.0.0.6 was released. I downloaded it and was able to just symlink a sun java 1.5 plugin into the plugin folder and it worked. I was also wondering where you installed it , because the default in that howto is /usr/local/firefox32. I was wondering if you perhaps had placed it in an iceweasel folder. Bit if thats where you installed it what do you get back from 
```
ls -al /usr/local/firefox32/plugins
```

---

