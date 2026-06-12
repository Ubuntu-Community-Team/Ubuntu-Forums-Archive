---
title: "Can Wine run programs created in C#?"
date: 2011-11-13
forum: Wine
---

### Post by PayPaul on 2011-11-13
I downloaded a digital art program called Palinka. Palinka is written in C# and developed on and for Microsoft Windows XP. I've added the application/exe file to the list programs in Wine Config and made that exe default to a compatibility with WinXp. Right clicking on the EXE file produces a wait state cursor and then nothing else happens. I've set the properties of the file to be executable as well. What else would I need to do to install and run this program in Wine? Here is the website link to the program.

[http://www.kelbv.com/palinka.php](http://www.kelbv.com/palinka.php)

---

### Post by sanderd17 on 2011-11-13
For C#, do take a look at mono.

I know mono and Wine can also work together, but mono allone will be enough for a pure C# program.

---

### Post by directhex on 2011-11-13
> **PayPaul said:**
> I downloaded a digital art program called Palinka. Palinka is written in C# and developed on and for Microsoft Windows XP. I've added the application/exe file to the list programs in Wine Config and made that exe default to a compatibility with WinXp. Right clicking on the EXE file produces a wait state cursor and then nothing else happens. I've set the properties of the file to be executable as well. What else would I need to do to install and run this program in Wine? Here is the website link to the program.

[http://www.kelbv.com/palinka.php](http://www.kelbv.com/palinka.php)

A pure C# app, not written by chimpanzees, will run with Mono (i.e. without Wine)

A badly written C# app may work with the Windows version of Mono, installed inside Wine.

---

### Post by PayPaul on 2011-11-13
> **directhex said:**
> A pure C# app, not written by chimpanzees, will run with Mono (i.e. without Wine)

A badly written C# app may work with the Windows version of Mono, installed inside Wine.

What is Mono?

---

### Post by sanderd17 on 2011-11-14
Mono is an open source implementation of the .net framework (VB.net and C#). So if your app uses only C#, than it will probably be enough to install mono (from the software center) and do
```

mono myprogram.exe

```

---

