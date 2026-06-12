---
title: "Mono in wine"
date: 2011-12-05
forum: Wine
---

### Post by Nixxus on 2011-12-05
Curretly trying to install Mono in wine on my ubuntu box, and due to my ISP, i cant use X over SSH.

So is there any way to install Mono completely through terminal?
Wine seems to require the Windows version of Mono as i've tried Linux mono 2.10 (compiled from source) without any luck.

just wondering if this is possible, or if i'm wasting my time.

thanks for taking the time to read this.

---

### Post by idoitprone on 2011-12-05
```
winetricks mono210
```

[http://wiki.winehq.org/Mono](http://wiki.winehq.org/Mono)

---

### Post by Nixxus on 2011-12-05
i used Winetricks to get the mono download and almost installed, but during installatio it cried about not having a display to use. so that's what lead me here.

thanks for replying though

---

### Post by idoitprone on 2011-12-05
> **Nixxus said:**
> i used Winetricks to get the mono download and almost installed, but during installatio it cried about not having a display to use. so that's what lead me here.

thanks for replying though

download mono

```
wine msiexec /i mono-install-file.msi
```

I am using opensuse 12.1 wine-1.3.30

---

### Post by Nixxus on 2011-12-05
just tried that too, still getting same error >.<

> 
$ wine msiexec /i mono-install-file.msi
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
err:systray:initialize_systray Could not create tray window
thanks for trying though

Edit:
for anyone reading this 2-5 years in the future though google or whatever search engin is popular now:
1. Pop me a PM saying hi =3
2. followed this tutorial to get Xming runing on my shoddy ISP [http://www.math.umn.edu/systems_guide/putty_xwin32.html](http://www.math.umn.edu/systems_guide/putty_xwin32.html) .

---

### Post by johnaaronrose on 2011-12-13
I just downloaded winetricks from Wine's website. On invoking winetricks and requesting Install of an App, it does not show mono. Can you tell me where to download mono install file from?

---

### Post by Elfy on 2011-12-13
Thread moved to Wine.

---

