---
title: "Auto start a application on boot with wine"
date: 2008-07-26
forum: Wine
---

### Post by Deadalus on 2008-07-26
I am using password safe. I want it to autostart when ubuntu starts. I tried to use system> preferences > sessions > sessions option and tried to save the apps configuration I have running. It is working with apps for ubuntu but not for wine apps. Is there a way to make them auto start ? I hope this i doable.

---

### Post by JagDragon on 2008-07-26
Do what you did before, but the command should be (for example, opening notepad)
```

wine /home/*user*/.wine/drive_c/windows/notepad.exe

```
where *user* is your username. Did you add the wine before the command previously?

---

