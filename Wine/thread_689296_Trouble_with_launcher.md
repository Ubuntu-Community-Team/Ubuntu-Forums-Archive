---
title: "Trouble with launcher"
date: 2008-02-06
forum: Wine
---

### Post by Faud on 2008-02-06
Howdy yall I am having a bear of a time creating a launcher OR getting  EQ2 to launch in terminal.
I copied it over from windows and it sits in .wine\c:\Program Files\Sony
Everquest II\Everquest2.exe
I can play the game just fine if I
```

winefile

```
and then follow the path and double click on the exe file.
But if I try and open in terminal I either get a blank wine desktop or some error about a path error and to abort or retry with a full file scan.
Thus I cant make a launcher.
Any ideas ?
Thanks

---

### Post by happyhamster on 2008-02-06
- How did you start the application from a terminal? Did you do:

wine /path-to-executable/executable.exe, or 

wine executable.exe from within the game folder? (preferred method)

- A wine launcher should point to the mock c: disk. It should look something like this:

WINEPREFIX="/home/insert-username-here/.wine" wine "C:\Program Files\Sony
Everquest II\Everquest2.exe" 

Hope that helps.

---

### Post by Faud on 2008-02-06
I have tried
```

env WINEPREFIX="/home/ryan/.wine" wine "C:\Program Files\Sony\Everquest II\EverQuest2.exe"

```
to no avail, it gives me the box with the error message

---

### Post by happyhamster on 2008-02-06
Perhaps there's something wrong with the "c:" link in .wine/dosdevices? (just guessing).

---

