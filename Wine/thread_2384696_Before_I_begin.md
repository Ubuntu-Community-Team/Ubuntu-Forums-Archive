---
title: "Before I begin"
date: 2018-02-10
forum: Wine
---

### Post by Lloydb39 on 2018-02-10
I want to try Wine, specifically to use dBase, but like a good user I went to the sticky notes. They are dated 10 years ago! Is this useful information? Do I just install it from the software center and proceed from there?

---

### Post by RobGoss on 2018-02-10
Just took a look in the Ubuntu center it seems to be working for most users until this day. I would just give it a try and see how it goes

---

### Post by Lloydb39 on 2018-02-12
Well, I did. When I tried to start dBase, nothing happened although Wine seems to be running and I got no error message. so....

---

### Post by mastablasta on 2018-02-13
did you run it from terminal? 

wine *nameofprogram *

still no error message?

---

### Post by Lloydb39 on 2018-02-13
Thanks. I got this:

wine: cannot find L"C:\\windows\\system32\\dbase.exe"

---

### Post by #&amp;thj^% on 2018-02-13
I don't see where you first ran:
```
winecfg
```

---

### Post by Lloydb39 on 2018-02-13
Is that necessary? I have the Wine configuration wizard. I used it to tell it to allow dBase. Software Center seemed to install it properly so I didn't know I had to go to the terminal for anything. I thought I could right click on the dBase exe file and tell it to run under Wine. No?

---

### Post by mastablasta on 2018-02-19
winecfg configures the wine. it's a GUi tool not a CLI (terminal based) one.

[https://wiki.winehq.org/Winecfg](https://wiki.winehq.org/Winecfg)

i am not sure what the configuration wizzard does. it could be it does the same thing. but perhaps it missed a setting?



in any case, the error message you posted says that wine has problem finding the file itself. 

i would start by browsing to the file and then run it from file manager or better yet and for diagnostic purposes open terminal at said location and then try to run it.

---

