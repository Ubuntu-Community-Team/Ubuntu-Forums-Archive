---
title: "&quot;invalid command tcl_findLibrary&quot; through Wine."
date: 2015-08-28
forum: Wine
---

### Post by jorgep2 on 2015-08-28
Good day, forum. 
 
I am having some issues trying to run a .exe through Wine recently. 
The .exe is called CoilSnake (SNES ROM hacks tool), and for the previous week I've been having troubles running it. 
 
I check the log of the .exe in C:\users\root\Temp\ and this is what I get: [TABLE="width: 90%, align: center"]
[TR]
[TD][/TD]
[/TR]
[TR]
[TD="class: code"]Traceback (most recent call last): 

  File "gui.py", line 9, in <module> 
  File "coilsnake\ui\gui.pyo", line 714, in main
  File "coilsnake\ui\gui.pyo", line 327, in main 
  File "coilsnake\ui\gui.pyo", line 331, in create_gui 
  File "Tkinter.pyo", line 1810, in __init__ 
     
_tkinter.TclError: invalid command name "tcl_findLibrary"[/TD]
[/TR]
[/TABLE]
 
It has to do with something related with TK/TCL. 
 
Thing is that this .exe was working before. 
I think I updated TexStudio and installed FreeCAD previous to this occurring. 
 
I've been searching all around but haven't found anything reliable. 
 
Any help?

---

### Post by lisati on 2015-08-28
*Thread moved to **Wine**.*

---

