---
title: "Start .exe programm after reboot (without logging in)"
date: 2014-02-14
forum: Wine
---

### Post by sunshineh on 2014-02-14
[COLOR=#000000][FONT=Arial][/FONT][/COLOR][COLOR=#000000][FONT=Arial]Hi, [/FONT][/COLOR]
I have an[COLOR=#000000][FONT=Arial] ubuntu server 10.4 and an application (.exe) which is running under wine, has a graphical user interface and need an internet connection. Now it is very important for me, that this application starts after a reset automatically.[/FONT][/COLOR]

I tried it with the following line in my rc.local (but it doesn't start :-( )
```
wine /root/.wine/drive_c/Program\ Files\ (x86)/Programname.exe
```

How can I do that??

---

### Post by ian-weisser on 2014-02-14
If you put it in rc.local, it's likely to fail for two reasons:

1) The system has not assigned a DISPLAY that the application can use. That's a catastrophic error for any GUI application. Users get assigned a DISPLAY when they login for their applications to use. GUI applications cannot run during the interval after startup but before login. The X server starts when you login.

2) Unless you specify in your script, it will run as root instead of you. If root had a DISPLAY (it doesn't), the application would show up on that display instead of yours. Yes, each user can be assigned a different display.

Do you really need the application to run a startup, before login?
If so, is a headless version available?

---

### Post by sunshineh on 2014-02-15
Thanks for your answer. I have no headless version of this application AND I neet that it run's as soon as possible after a reboot from my provider.
I don't want a automatic root login without password...

---

