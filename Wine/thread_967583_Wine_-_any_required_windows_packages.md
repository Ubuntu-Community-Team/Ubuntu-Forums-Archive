---
title: "Wine - any required windows packages?"
date: 2008-11-02
forum: Wine
---

### Post by KOTAPAKA on 2008-11-02
OK here is the thing. Wine is working fine. I can install and run programs. However when I run them they are not working properly. For instance Cambridge dictionary can't find any word. I've come to the conclusion that I might need some windows packages such as .Net or similar. Do I need any of those with wine and if yes which ones?

---

### Post by asdfoo on 2008-11-02
> **KOTAPAKA said:**
> OK here is the thing. Wine is working fine. I can install and run programs. However when I run them they are not working properly. For instance Cambridge dictionary can't find any word. I've come to the conclusion that I might need some windows packages such as .Net or similar. Do I need any of those with wine and if yes which ones?

Usually the AppDB [http://appdb.winehq.org](http://appdb.winehq.org) is a good place to check if there are any additional steps to get your program working.

If your program does not completely work, it does not always mean that something is missing, it just means that Wine has a bug which affects your application.  

Is there any terminal output if you run the app by opening a terminal, cd'ing to the install directory and running it manually?

eg. cd ~/.wine/drive_c/cambridge/
wine cambridge.exe

---

