---
title: "codebeamer"
date: 2007-12-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by praxis22 on 2007-12-16
Having spent an evening wrangling this for the wife, I figured I drop in an FYI, just in case anyone should come a searching.

Basically codebeamer 4.2.4 GA Linux does work on ubuntu, but not on 64bit. It refuses to even install, and if you do unzip it into place, the version of Java that comes with it, doesn't even run. Just gives you "file not found" when you do anything with it. 

With the 32bit version of Gutsy server, it's a different matter entirely, installs clean, and once you've setup the mysql database it works.

The only gotcha is you have to manually edit /etc/mysql/my.cnf, and comment out the binding to 127.0.0.1 otherwise you get Java stack trace errors when you try to login.

I've yet to get it so it'll speak to external browsers, but now I'm going to bed :)

---

