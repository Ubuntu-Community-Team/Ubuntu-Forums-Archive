---
title: "How do I start programming on Feisty x64?"
date: 2007-06-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by ecs_pf5 on 2007-06-08
I'm used to programming small GUI and console apps for Windows x86-32 systems, using development environments like gcc, Liberty BASIC, Visual Studio, & MS dot NET BASICs.

I had a brief look at gambas, but it doesn't seem to be supported yet on Ubuntu x64. There are rumblings about Liberty BASIC coming onto Linux, but it's not ready yet.

What IDE's are available right now for programming in simple C and/or BASIC on Ubuntu 64? I have Feisty 7.04 installed at the mo.

Bearing in mind, I'd like to be able to write small GUI apps but am only a fairly inexperienced hobby programmer, with next to no knowledge of coding outside Windows. I'm much happier in BASIC than C.

---

### Post by manual_overide on 2007-06-08
monodevelop will let you write stuff in .NET, you might also want to check out glade if you want to write gnome applications

---

### Post by Cappy on 2007-06-08
Python is the recommended language for Ubuntu programmers.
There is a thread on it here:
[http://ubuntuforums.org/showthread.php?t=333867](http://ubuntuforums.org/showthread.php?t=333867)

There is also Gambas that is a lot like Visual Basic:
[http://ubuntuforums.org/showthread.php?t=333867](http://ubuntuforums.org/showthread.php?t=333867)

---

### Post by kuja on 2007-06-08
KDevelop is a pretty versatile IDE worth checking out.

---

### Post by jusmurph on 2007-06-08
[http://book.opensourceproject.org.cn/distrib/ubuntu/unleashed/](http://book.opensourceproject.org.cn/distrib/ubuntu/unleashed/)

There is a chapter on that regarding starting programming in ubuntu.

---

### Post by incubus on 2007-06-09
ecs,

I also recommend (switching to) Python.  Here are my personal reasons:

1. The language is clear, simple, and favors elegance in solving problems.

2. It runs in several platforms and even has different implementations: Java (Jython), .NET (IronPython), not to mention PyPy.

3. Large and good library, so you can start doing fancy things right away.  From GUIs, scientific computation, machine learning, web frameworks, databases, statistics, to mere simple scripts: you name it and import it.

4. Great, nice, and active community that is constantly improving the language.

You may also consider Ruby and Lisp, if you want to be bold.  I've gone through this before and I would suggest you to take a few days to try different things before making the commitment.  After you make your decision, work hard to convert your brain to the new paradigm -- don't look back for a while.  Challenge yourself with solving small problems, then go to more complicated ones.

For GUIs you can take a look at wxPython, PyGTK, and PyQT.  I've tried the first one before and it's very simple to use.

Oh, I almost forgot to mention.  Check this out: [http://showmedo.com/](http://showmedo.com/)

Best,

incubus

---

### Post by ecs_pf5 on 2007-06-09
I've started by having a good look at Python.

How easy is it to port Python sourcecode written for Ubuntu, to Windows? I know that's like asking how long string is :p

wxPython looks really good although I'm only just beginning to look into it

[edit]

I just managed to use Python and wxPython to write and test a small 'hello world' GUI app on Ubuntu.

Then I moved to a Windows machine and recompiled it as a Windows GUI app, using the Windows versions of Python, wxPython and py2exe with absolutely no modification to the source code itself. Really impressed with that :)

mono looks interesting..

---

### Post by incubus on 2007-06-10
Good to hear that, ecs.  Looks like you're progressing very fast.

If you're interested in mono and .NET, check voidspace's webpage:
[http://www.voidspace.org.uk/ironpython/index.shtml](http://www.voidspace.org.uk/ironpython/index.shtml)

He develops using IronPython and he posts articles on it frequently.  If I remember correctly, he has some on writing GUIs right away.  I myself am very ignorant on the subject.  I'm not a graphical person.

Best,
incubus

---

### Post by ecs_pf5 on 2007-06-10
Thanks incubus I'll check that out :)

At the moment I seem to be able to write executables for Windows, using C# on Linux, but not executables for Linux, on Linux.. using Mono. I think I have the knobs and dials set wrong. My head hurts.

I just have to keep on reading I guess :p

---

### Post by damvcoool on 2008-03-01
Gambas2 now compiles for 64bit.

it works perfectly :D

---

### Post by ecs_pf5 on 2008-03-04
Thanks for the heads-up, will check it out :)

---

