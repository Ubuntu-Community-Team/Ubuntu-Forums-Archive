---
title: "Wine Error"
date: 2007-08-28
forum: Wine
---

### Post by xspikeyhairx on 2007-08-28
Ok, so I just installed Wine but... When I try to run it a get an error message.... Here is a copy of what happened in the terminal.

matt@matt-desktop:~$ sudo wine
Password:
Usage: wine PROGRAM [ARGUMENTS...]   Run the specified program
       wine --help                   Display this help and exit
       wine --version                Output version information and exit
matt@matt-desktop:~$ wine PROGRAM
wine: could not load L"c:\\windows\\system32\\PROGRAM.exe": Module not found
matt@matt-desktop:~$

Could you help me?:confused:

---

### Post by cogadh on 2007-08-28
**Never** run Wine with sudo, it will be bad. 

Click on the "Stuff I've learned about Wine" link in my sig for the basics on how to use Wine.

---

### Post by xspikeyhairx on 2007-08-28
... this doesn't help me. I still get an error message saying

wine: could not load L"c:\\windows\\system32\\PROGRAM.exe": Module not found

this is making me mad:mad:

---

### Post by cogadh on 2007-08-28
That's because all you typed in the terminal was "wine". Wine requires you to specify a Windows executable to run, like this:
```
wine application.exe
```
Obviously, change "application.exe" to whatever executable you are trying to run.

---

### Post by splintercellguy on 2007-08-29
cding to where you installed the app would help mucho, along with perhaps specifying a path in the param to wine?

---

