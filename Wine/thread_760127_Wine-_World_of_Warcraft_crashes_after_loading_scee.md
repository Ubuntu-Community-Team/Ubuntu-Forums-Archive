---
title: "Wine- World of Warcraft: crashes after loading sceen"
date: 2008-04-19
forum: Wine
---

### Post by nsquawk on 2008-04-19
I have tried a lot of solutions, none of which have worked at this point. But WoW crashes and only crashes (so far) when i try to enter the game with an already existing character. If i create a new character I have no problems entering the world at all. 

X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  13 (X_GLXCreateGLXPixmap)
  Serial number of failed request:  426
  Current serial number in output stream:  427
 
Im on 6.06 with a nvidia card.

Any ideas as to why is only crashes with old characters?

---

### Post by daemonfly on 2008-04-19
Assuming you've installed it correctly...

I'm no expert, but the only thing I can see different with old chars vs new ones are old chars should already have files in WTF subfolders.

Perhaps try moving the account subfolders within /WTF to a backup directory and see if you still have the problems.

---

