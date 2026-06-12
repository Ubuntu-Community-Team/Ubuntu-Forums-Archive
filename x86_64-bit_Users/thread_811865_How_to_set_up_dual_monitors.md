---
title: "How to set up dual monitors"
date: 2008-05-29
forum: x86 64-bit Users
---

### Post by jcroblesemanuelli on 2008-05-29
New to Ubuntu. Have a Dell Optiplex 745 with a Radeon X1300 series ATI graphics card.  Could someone please help me how to setup two dell monitors.  I have been trying to figure this out for hours and can't get it to work.  My two monitors worked perfectly in Windows XP but when I installed ubuntu I just see mirror monitors.

---

### Post by Prospero2006 on 2008-05-29
First, ATI support in Ubuntu is less than ideal. NVIDIA tends to run much more smoothly across the board.

1.) Make sure your ATI drivers are enabled. Use Envy for the easiest install process.

2.) Open up /etc/X11/xorg.conf
(BACK IT UP FIRST!)
add
```

Section "ServerFlags"
 Option "Xinerama" "ON"
 EndSection


```

and
```

Section "ServerLayout"
        Identifier      "Default Layout"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
       Screen "screen0"
       Screen "screen1" RightOf "screen0"
EndSection

```

This assumes that your monitors are configured as screen1 and screen0,
check through xorg.conf to be sure.

Add that stuff and do a ctrl-alt-backspace to restart the X server.

Good Luck!

---

