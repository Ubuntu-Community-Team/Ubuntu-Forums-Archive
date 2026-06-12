---
title: "Visual studio 6 doesn't build/compile programs"
date: 2008-05-12
forum: Wine
---

### Post by razlken on 2008-05-12
Hi, I've installed Wine with no problems, and I'm trying to make Vs 6 run on it for some university projects, I can't really change it since the professor wants us to use THIS! program -.-

anyway since i got a desktop with it already installed i copied the installation directory directly to the wine "program files" folder, it gave me a dll error so i copied "mfc42.dll" to the "windows\System 32" folder.i opened Visual C++ & it worked, but doesn't compile or build any projects it gives me an error

> EM.DLL

this required file cannot be loaded please re-install Microsoft visual C++

so is there a solution? Please really need it. thanks in advance!

---

### Post by dmn_clown on 2008-05-12
Wine isn't the best environment for visual studio, write your code in linux, cross-compile with mingw32 to test, then find an open windows box in a computer lab to install visual studio 6 on and use that for your final assignment.

---

### Post by razlken on 2008-05-12
ok i downloaded and installed it. ahem...how do i make it work? i'm still a newbie in ubuntu so don't understadn from where should i open it form any help would be great.

---

### Post by noerrorsfound on 2008-05-12
Visual Studio 6 doesn't even implement the C++ standard correctly. I can't believe any professor would only allow the use of a program from 1998.

You can get a free version of Visual C++ 2008 from Microsoft.
[Visual Studio 2008 "Express Editions"](http://msdn.microsoft.com/en-us/express/future/bb421473.aspx)

---

