---
title: "Path not found"
date: 2012-12-08
forum: Wine
---

### Post by CaptainThunderwolf on 2012-12-08
Hey there, my technologically superior friends. I've been having some issues with Wine recently, as you may have guessed. Whenever I attempt to play a .exe file through the "Wine Windows Program Loader" option (Right click, then the option I just mentioned), I get an error message saying, quite simply, "Path Not Found", and that's all. It's all very perplexing since it was working only hours ago, and just suddenly seemed to give up on working properly altogether. I was running Wine 1.4, and to the best of my knowledge, didn't alter any of my Wine software prior to this happening. I've already tried uninstalling then reinstalling it, oh, five or six times now, to no real avail. If anybody has any idea what's going wrong here, I'd really appreciate the help.

---

### Post by Tweak42 on 2012-12-08
> **CaptainThunderwolf said:**
> Hey there, my technologically superior friends. I've been having some issues with Wine recently, as you may have guessed. Whenever I attempt to play a .exe file through the "Wine Windows Program Loader" option (Right click, then the option I just mentioned), I get an error message saying, quite simply, "Path Not Found", and that's all. It's all very perplexing since it was working only hours ago, and just suddenly seemed to give up on working properly altogether. I was running Wine 1.4, and to the best of my knowledge, didn't alter any of my Wine software prior to this happening. I've already tried uninstalling then reinstalling it, oh, five or six times now, to no real avail. If anybody has any idea what's going wrong here, I'd really appreciate the help.

What happens when you try to run the exe via wine in a terminal?  What was the program and was it wine you uninstalled and reinstalled or the program itself?

---

### Post by CaptainThunderwolf on 2012-12-08
Not quite sure how to run Wine through terminal, since none of the programs I used it for are actually saved in its programs section. The program I attempted to run was the install for Star Wars: KoTOR, and I uninstalled then reinstalled both it and Wine.

EDIT: Alright, how about we start off with a simpler question? What is this path it's referring to, and why could it possibly not be abelt o find it?

---

### Post by Tweak42 on 2012-12-09
> **CaptainThunderwolf said:**
> Not quite sure how to run Wine through terminal, since none of the programs I used it for are actually saved in its programs section. The program I attempted to run was the install for Star Wars: KoTOR, and I uninstalled then reinstalled both it and Wine.

EDIT: Alright, how about we start off with a simpler question? What is this path it's referring to, and why could it possibly not be abelt o find it?

I'm not sure but the menu link could have have been altered, or the executable path is different.  This is why its best to run wine from a terminal so you can see the actual error messages.

The default location for the wine prefix (the equivalent windows c: drive) is ```
/home/<username>/.wine/drive_c/
```
Thus all you need to do is browse to that directory to look where your programs are installed.  Any directory that starts with a "." are hidden so you need to unhide (ctrl-H) in nautilus to see it.  In a terminal you can just 'cd' to it normally.

---

