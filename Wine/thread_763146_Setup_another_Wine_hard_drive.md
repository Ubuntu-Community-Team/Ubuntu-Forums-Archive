---
title: "Setup another Wine hard drive?"
date: 2008-04-22
forum: Wine
---

### Post by Dark Aspect on 2008-04-22
How do I setup another wine hard drive with a windows folder?

Like for example if I want to install untested software,can I just create another c_drive (like h_drive) and then run the application with out affecting my other c_drive.This would help if an application corrupted the entire c_drive.Kind of like cedega/crossover where you can have multiple bottles.

---

### Post by cogadh on 2008-04-22
Use the "wineprefixcreate" command to create a new "fake Windows" directory with a unique name:
```
wineprefixcreate --prefix .name_of_wine_directory
```

BTW - the "wineprefixcreate" command is exactly how Cedega and CrossOver create their "bottles".

---

### Post by Dark Aspect on 2008-04-22
> **cogadh said:**
> Use the "wineprefixcreate" command to create a new "fake Windows" directory with a unique name:
```
wineprefixcreate --prefix .name_of_wine_directory
```

BTW - the "wineprefixcreate" command is exactly how Cedega and CrossOver create their "bottles".

Awesome,Thanks cogadh.

---

### Post by cogadh on 2008-04-22
I forgot to mention, when installing or running an application with that new directory, you need to specify it in the command:
```
env WINEPREFIX="~/.name_of_wine_directory" wine "C:\Program Files\Application\Application.exe"
```

---

