---
title: "Video Crashes"
date: 2008-07-15
forum: x86 64-bit Users
---

### Post by heinzbitte on 2008-07-15
I've been noticing that when I sometimes have more than one flash video open my video display will crash and I will be in the terminal/tty/cli/whatever it is called.  I don't really know the commands that well so I just have to ctrl alt del and restart my computer.

Today I noticed that if I try at all to go to circuit city's website it will do this. 

I have an ati radeon 9550 and I can give more information if you ask.

---

### Post by heinzbitte on 2008-07-17
...

---

### Post by heinzbitte on 2008-08-02
It has been happening more recently.  And now sometiems when I have only one video open.

---

### Post by Yellow Pasque on 2008-08-02
What video driver are you using, the open-source ati/radeon driver or the fglrx/Catalyst driver?

Also, what version of Flash are you using? (about:plugins in the URL bar)

When you get crashed to the terminal, try running these commands to get error messages:
```
dmesg
cat /var/log/Xorg.0.log
```
The error messages should be at the end, but if you need to see back further, use dmesg | more or cat /var...log | more

---

### Post by heinzbitte on 2008-08-03
> **Temüjin said:**
> What video driver are you using, the open-source ati/radeon driver or the fglrx/Catalyst driver?

Also, what version of Flash are you using? (about:plugins in the URL bar)

typing fglrxifno gets me
```

einzbitte@Crapbox:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon 9550 / X1050 Series
OpenGL version string: 2.1.7412 Release

```

    File name: npwrapper.libflashplayer.so
    Shockwave Flash 9.0 r124

I have a 64 bit system.

I'll try that command next time it happens.

Also is there anyway to restart the video without restarting the computer?

---

### Post by heinzbitte on 2008-08-03
Ok I think this is what you wanted

Fatal Server Error:
Caught Signal 11.  Sever aborting

(II it may be 11) AIGLX: Suspending AIGLX Clients for VT switch.

---

