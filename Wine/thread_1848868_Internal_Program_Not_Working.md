---
title: "Internal Program Not Working"
date: 2011-09-23
forum: Wine
---

### Post by JaySeeJC on 2011-09-23
I have a program at work I need to run and I don't have access to the source code. It is a windows program written ages ago and others in my office have had the same issues. The output from wine is as follows

```
wine ./programname.EXE 
fixme:int:DOSVM_Int10Handler Get Font Information - Not Supported
fixme:int:DOSVM_Int16Handler Get Extended Shift States - Not Supported
fixme:int:DOSVM_Int10Handler Set Background/Border Color: 0/0
```and then it just hangs there, repeating the last message every 60 seconds. I really need this program for my work and really don't want to have to dualboot just for this on piece of software.

NOTE: My system wide wine version is 1.3.28 and I am running ubuntu 10.04
ALSO NOTE: According to co-workers that have been here longer than me, it is not a DOS program.

UPDATE: I have gotten the program working, but when i close some of the spawned windows, the whole program crashes with this error message from the console:
[CODE]fixme:font:WineEngRemoveFontResourceEx (L"XppNat.dll", 0, (nil)): stub[CODE]

---

### Post by dino99 on 2011-09-24
report this issue on winehq bugzilla

---

