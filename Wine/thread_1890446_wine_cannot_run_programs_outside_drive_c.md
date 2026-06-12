---
title: "wine cannot run programs outside drive c"
date: 2011-12-03
forum: Wine
---

### Post by Nublet on 2011-12-03
I'm running lubuntu with wine 1.3. When I try to run a program outside wine's own drive c, I get response such as this:
```
/media/sda5/g/Fallout$ wine falloutw.exe 
wine: cannot find L"unix\\media\\sda5\\g\\Fallout\\falloutw.exe"

```
It used to work fine. Making a symlink within .wine/dosdevices/c: is a quick and dirty solution, but I'm hoping for something a bit less dirty. Any ideas?

---

### Post by ergo-proxy on 2011-12-04
Hmm try click on it? Try to copy it to a different place?

---

### Post by 8Kuula on 2011-12-04
Add path to winecfg drives tab?

---

### Post by Nublet on 2011-12-04
Clicking or running in the terminal doesn't make a difference. As I have said, running programs anywhere outside wine's own drives prompts similar response.
I can't try the winecfg solution, since I don't have access to that computer right now, but it always worked just fine before (and it JUST worked, without any changes to any config files), so I've been wondering if maybe I've broken something, or maybe someone else did?

---

### Post by desktorp on 2011-12-06
I've noticed on more than one occasion, that in the process of installing Fallout, every file and folder is converted to lower-case, leaving the game unplayable.  I have experienced variations on this; in one situation the program would load, only to crash after the intro video.. another time I could not even get the program to launch.  I realize it's probably not the situation here, but make sure case-sensitivity isn't the problem.

---

