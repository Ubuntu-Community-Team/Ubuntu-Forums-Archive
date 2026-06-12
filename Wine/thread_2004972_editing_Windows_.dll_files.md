---
title: "editing Windows .dll files"
date: 2012-06-16
forum: Wine
---

### Post by Starmartyr on 2012-06-16
I have been trying to find out why I can't open and edit a .dll file.  It's in my wine directory, system32/winsta.dll.  When I try to open it it is unreadable.  i have tried gedit, kwrite and a couple others.  What encoding-decoding do I need?

System: Ubuntu 12.04
Wine 1.5.2

---

### Post by forrestcupp on 2012-06-16
You can't decompile dll's. They are compiled binaries. There's no way to see the code they originally wrote to create the dll, either in Windows or Linux.

If it happens to be a dll written in .Net, you can purchase [.Net Reflector](http://www.reflector.net/) to decompile it back to C# or VB. But two things to note are that there's no way for it to know the names of variables, classes, functions, etc. the devs used, and also, most Windows system dll's are not written in .Net. Also, you'd have to use that program from Windows, not Linux.

You're probably just out of luck.

---

### Post by jmfal on 2012-06-16
Are you having problems with a .dll because of some kind of virus or malware?

They can be replaced.

I seen a thread in the win7 forums with a list of .dll files and instructions on how to install.

---

### Post by sandyd on 2012-06-16
> **Starmartyr said:**
> I have been trying to find out why I can't open and edit a .dll file.  It's in my wine directory, system32/winsta.dll.  When I try to open it it is unreadable.  i have tried gedit, kwrite and a couple others.  What encoding-decoding do I need?

System: Ubuntu 12.04
Wine 1.5.2

the dll is compiled from source code.
The only way to edit it is to get the wine source code, edit it there, and recompile.

---

### Post by forrestcupp on 2012-06-17
> **sandyd said:**
> the dll is compiled from source code.
The only way to edit it is to get the wine source code, edit it there, and recompile.

Wow. I never thought about the Wine dll source code being available. That's right.

But I guess another question is, why in the world do you need to edit the code of a dll? There's probably another solution.

---

### Post by philinux on 2012-06-17
Moved to wine forum

---

