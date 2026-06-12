---
title: "Installed Flash, but it disappeared!"
date: 2007-08-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by hackle577 on 2007-08-07
After I got my new computer up and running yesterday, I installed Flash using [this guide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_.2864-bit.29_Mozilla_Firefox_.28only.29"). I added the command to my Sessions list so it would activate on every boot. But when I came home from work today, Flash videos (YouTube, etc.) didn't show up.

I tried enetering "nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so" manually in the terminal, but that returned "nspluginwrapper: /usr/lib/mozilla/plugins/libflashplayer.so is not a valid NPAPI plugin"

Help? Thanks!

---

### Post by Cappy on 2007-08-07
Remove that session command you added and try this:

Kilz's  Flash 9 install script for AMD64 (nspluginwrapper)
[http://ubuntuforums.org/showthread.php?t=476924](http://ubuntuforums.org/showthread.php?t=476924)

---

### Post by hackle577 on 2007-08-07
No dice, it didn't work. No noticeable difference.

---

### Post by Cappy on 2007-08-07
```

$ nspluginwrapper -i /usr/lib/nonexistingfile
nspluginwrapper: /usr/lib/nonexistingfile is not a valid NPAPI plugin

```

The error probably means you are missing that file.
You could 
```

cd /usr/lib/mozilla/plugins/
ls -la

```
and see if it is in there.

---

### Post by hackle577 on 2007-08-07
It's there.

---

### Post by hackle577 on 2007-08-08
Bumpity bump bump. Help? I've tried several scripts and methods from the forums, with no luck.

---

