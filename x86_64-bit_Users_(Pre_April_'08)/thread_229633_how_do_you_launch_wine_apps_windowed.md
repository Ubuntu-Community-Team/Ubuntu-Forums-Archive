---
title: "how do you launch wine apps windowed"
date: 2006-08-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by cocteau on 2006-08-04
hi

I've been googling for an answer to this but I can't seem to find one. When launching an application with winelauncher is there a switch to open it windowed and prevent wine from taking over my screen?

---

### Post by Kilz on 2006-08-04
> **cocteau said:**
> hi

I've been googling for an answer to this but I can't seem to find one. When launching an application with winelauncher is there a switch to open it windowed and prevent wine from taking over my screen?

Type in windcfg in the terminal. On the Graphics tab is a checkbox for Emulate a virtual desktop. If you have no applications listed on the Applications tab this will be default for all applications since default settings is all thats there. You can make this apply to all prograsms or just one. 
To make it apply to just one, add the application on the Applications tab, highlight it, then click the Emulate virtual desktop checkbox. Then click apply.

---

### Post by cocteau on 2006-08-04
Brilliant! However now the desktop arrows graphics is on top of the pointer in the game but I can live with that. I'm only messing around until I get my code for cedega :)

---

### Post by cocteau on 2006-08-04
> **cocteau said:**
> Brilliant! However now the desktop arrows graphics is on top of the pointer in the game but I can live with that. I'm only messing around until I get my code for cedega :)

Ooops... solved my own problem. I had for some reason removed the tick in 'allow window manager to manage created windows'... pointer is now as it should be.

---

