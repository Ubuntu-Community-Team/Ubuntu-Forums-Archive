---
title: "Kilz: Include this in your script"
date: 2007-06-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by rivera151 on 2007-06-18
I wanted to upload the .so file for the Adobe Reader browser plugin, but it was too big.  In any case, I was thinking since one of your scripts already includes installing Adobe Reader 32-bit, just include in your nspluginwrapper script the command

```

nspluginwrapper -i nppdf.so

```

Worked like a charm for me!  INow I have acroread in Firefox 64!  If you need the .so file let me know where I can send it to you, but it's in the Adobe Reader tarball anyways.

---

### Post by scourge on 2007-06-19
Do you mean that the same script that installs the Flash plugin should also automatically install Adobe Reader? I wouldn't like that. I think Evince is ten times better, and it's 64-bit.

---

### Post by kuja on 2007-06-19
scourge: no, he just wants the script to run create a wrapper for the plugin if it's installed so it will work in 64-bit browsers.

---

### Post by Kilz on 2007-06-19
> **kuja said:**
> scourge: no, he just wants the script to run create a wrapper for the plugin if it's installed so it will work in 64-bit browsers.

Exactly! I like easy scripts that do one thing. But the script does install Flash, as well as the wrapper. But once the script is installed all it takes is that command to make acrobat reader work. To tell the truth, I like Evince a lot better. While it doesn't make the browser a reader, it shows pdf's very nicely. That and cbr files in the one in Feisty.

---

### Post by Cappy on 2007-06-19
I use Evince on Linux and Foxit Reader on Windows. Adobe Reader is just so slow to load and browse .. I hate it.

---

