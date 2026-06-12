---
title: "Quartus II 7.2 Installing"
date: 2008-06-19
forum: Wine
---

### Post by player999 on 2008-06-19
Hi! Anybody installed Quartus II 7.2 commercial version on Ubuntu Hardy Heron. I saw it in supported applications list on winehq site. But I think will be some problems with license manager (when I tried to install OrCad FlexLM install showed me some error that TCP/IP not installed). So if anybody successfully installed OrCad or Quartus, write plz about installation process step by step.](*,)](*,)](*,)

---

### Post by cogadh on 2008-06-19
It's on the applications list, but I wouldn't call it supported, it only has a bronze rating, which means it barely runs at all. However, the last time it was tested was with Wine 0.9.33, so it may be worth it to give it a try with 1.0. Run the installation from the terminal and post the output if it has any problems.

---

### Post by player999 on 2008-06-20
Installing was successful, but not at all. Some drivers didn`t installed, but i don`t not need them. When i try to start Quartus there is some error with memory. See terminal messages in attachment.:-k

---

### Post by cogadh on 2008-06-20
[http://wiki.winehq.org/PreloaderPageZeroProblem](http://wiki.winehq.org/PreloaderPageZeroProblem)
That will get rid of those preloader memory error messages. After applying the fix, try running it again and see what errors still remain.

BTW - You don't need to post the output as an attachment, just put it right in the post itself, using the forum [code] tags.

---

### Post by player999 on 2008-06-20
Thank you for your answer, i fixed this bug, but one f*cking problem left, this f*cking Quartus not running again. Look at this ****:

```
Running in 32-bit mode
fixme:dbghelp:validate_addr64 Unsupported address ffffffffffffe403
fixme:dbghelp:validate_addr64 Unsupported address ffffffffffffe403
fixme:dbghelp:validate_addr64 Unsupported address ffffffffffffffff
fixme:dbghelp:validate_addr64 Unsupported address fffffffffffffff 
Running in 64-bit mode
quartus.exeTrying to load PE image for unsupported architecture (AMD-64)
Trying to load PE image for unsupported architecture (AMD-64)
wine: could not load L"C:\\altera\\72\\quartus\\bin64\\quartus.exe": Bad EXE format for 
```

In bug list, you showed me, i didn`t find it.
Yes, i`m running AMD Turion 64

---

### Post by cogadh on 2008-06-20
Ah, you are running on a 64-bit system. Do you have the ia32-libs package installed (I don't know if that is a default package or not)?

---

### Post by player999 on 2008-06-20
Yes, I have newest version of ia32-libs.

---

