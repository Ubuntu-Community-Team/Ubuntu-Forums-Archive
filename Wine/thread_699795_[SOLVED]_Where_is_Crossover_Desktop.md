---
title: "[SOLVED] Where is Crossover Desktop?"
date: 2008-02-17
forum: Wine
---

### Post by A-dogg on 2008-02-17
Sorry if this is in the wrong category...

I have MS Office XP installed in Crossover Pro and somehow managed to save a .doc file to my desktop... except it's not my LINUX desktop, it's the phantom Windows desktop Crossover creates. I need to delete the file for security reasons and can't seem to find out where the heck that phantom Windows desktop is and how to access it.

In the real Windows, you can right-click and delete/copy/whatever a file from any open dialogue (save/open) box. But it seems you can't do that here. 

So I can locate this file from within Office (running in Crossover), but I can't right-click delete, or get to it directly.

Any advice?

GOT IT: Crossover creates a folder in the drive_c\Windows directory called "Profiles". Inside, there's a "crossover" folder and inside that there's a "Desktop" folder. Bingo.

---

