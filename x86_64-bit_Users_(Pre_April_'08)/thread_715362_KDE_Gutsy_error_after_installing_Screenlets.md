---
title: "KDE Gutsy error after installing Screenlets"
date: 2008-03-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by Sack on 2008-03-04
Hello, 
I'm running the x86 version of kubuntu. I recently tried out screenlets version 0.0.12. I found that version to be a little buggy and for some reason shortly afterwards I couldnt access any of my hard drives through konqueror. I thought it was a minor problem so I tried restarting my comp and now after I type in my password it stops the loading at "Initializing System Settings" and puts me back where I put in my password. I can log in through failsafe and access everything through command line, this is where I uninstalled the screenlets files based on code that is on their forums. I was wondering how I can check my logs to find out what the problem is or if anyone else has had this problem and knows what I need to do.

Thank you.

---

### Post by prince_niceguy on 2008-03-05
to start off and get into your kde session just login into fail safe terminal and rename the .kde to .kde.org

now login into kde.

---

### Post by Sack on 2008-03-06
Sorry, I'm a little bit new to the layout of Kubuntu. This is a file that is inside my home directory, correct?

---

### Post by prince_niceguy on 2008-03-06
sorry, didnt realise it.

yes the file would be in your home directory. when you login in to failsafe terminal run the following command

```
mv .kde .kde.bak
```

now log out and login. you kde setting would be reset. if it is problem with kde setting then this would fix it.

---

