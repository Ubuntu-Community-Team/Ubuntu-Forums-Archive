---
title: "How do I run .exe files in a directory that has a space in the name?"
date: 2007-12-16
forum: Wine
---

### Post by chumchum on 2007-12-16
Hello all
I am using a dual boot between windows XP and Ubuntu 7.04 Festy Fawn. I first installed it just to try out, but it turns out I love Linux now ^^
However I still would like to be able to run .exe applications, so I now have wine (version: 0.9.33-0ubuntu1) but how can I run .exe files from their location on Windows since there is a space in the directory name "Program files" I have an error message saying "Could not find medi/[...]/Program", the only solution I have figured is to copy my programs in a folder on my Linux desktop, of course this is a waste of HDD space in my mind, so how can I speciffically tell wine that the folder's name IS "Prgram files" and NOT just "Program"?
Thank you all in advance
P.S: Renaming my windows folders is NOt an option since it would screw up all the shortcuts and programs that work with each other and rely on other files etc...

---

### Post by Stemp on 2007-12-16
Hi chumchum,

Add a** \** before the space eg :
```
/Program\ Files/Rockstar\ Games/
```

---

### Post by skroops on 2007-12-16
or put quotes around the path 

wine "C:\Program Files\World of Warcraft\WoW.exe"

---

