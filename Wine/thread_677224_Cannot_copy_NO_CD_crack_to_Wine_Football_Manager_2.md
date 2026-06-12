---
title: "Cannot copy NO CD crack to Wine Football Manager 2008 folder"
date: 2008-01-24
forum: Wine
---

### Post by grebarton on 2008-01-24
I need to copy a NO CD .exe for Football Manager 2008 from my desktop to my successfully installed Wine Football Manager 2008 folder.

So far I am at a loss as to how to do this.

Any ideas?

---

### Post by Limpan on 2008-01-24
Wine has it's own, hidden folder, so you'll have to copy it to ~/.wine/drive_c/something/something

---

### Post by Mze on 2008-01-24
While in your home folder.

Press CTRL+H  to see hidden folders.

Copy file you want into .wine directory>>Program Files>>"whatever game you installed"

Remember to press CTRL+H once again to stop seeing hidden files

---

### Post by grebarton on 2008-01-25
I know where to copy it but i'm simply asking what the command would be exactly?

---

### Post by alex_anthony on 2008-01-30
<code>
cp /path/to/file /path/to/where/you/want/it
e.g
cp /home/user/fm.exe /home/user/.wine/drive_c/Program\ Files/
</code>
Btw, how did you get it to install?

---

