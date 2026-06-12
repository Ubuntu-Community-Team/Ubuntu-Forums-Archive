---
title: "java error running earthcomber"
date: 2006-07-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by jamesrw on 2006-07-26
```
java.lang.NumberFormatException: For input string: "142-02"
        at java.lang.NumberFormatException.forInputString(NumberFormatException.java:48)
        at java.lang.Integer.parseInt(Integer.java:477)
        at java.lang.Integer.parseInt(Integer.java:518)
        at com.earthcomber.javatray.JavaTray.main(JavaTray.java:40)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:324)
        at com.exe4j.runtime.LauncherEngine.launch(Unknown Source)
        at com.install4j.runtime.Launcher.main(Unknown Source)
```


I dunno what this is

---

### Post by mlind on 2006-07-26
That's an error message that application tried to parse number out of 142-02, but failed like it should. It's probably a bug or just a note.

Was the exception fatal?

---

