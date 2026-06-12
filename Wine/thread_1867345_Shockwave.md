---
title: "Shockwave"
date: 2011-10-22
forum: Wine
---

### Post by SkyeFerret on 2011-10-22
I need Shockwave for school videos, but apparently it's not Linux compatible. I'm pretty sure there's a way to get around that by installing the plugin on Firefox in Wine, but I'm not sure - is it possible, and how can I do it? If not, is there anything else I can do? I don't like having to rely on my desktop computer just to view a video.

---

### Post by dcottingham on 2011-11-02
I have been attempting this too. You might want to refer to this:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=20531](http://appdb.winehq.org/objectManager.php?sClass=version&iId=20531)

It gives instructions on installing shockwave. Of course, you first need firefox, and as that page says, you need version 3.6.3 or older. If you get a current winetricks, you can say "sh winetricks firefox35" and get version 3.5.

I've been trying to get both flash and shockwave working at the same time, and have not yet succeeded. But if you just want shockwave, I believe following the recipe on that page will work.

---

### Post by SkyeFerret on 2011-11-03
So, wait, how do I get Wine to get the .msi file?

(Also, whoa, blast from the past with FF3.5)

---

### Post by dcottingham on 2011-11-03
You get the msi file by doing "sh winetricks shockwave".

I just remembered another thing. If you use winetricks to install firefox 3.5, winetricks will put it in its own private little WINEPREFIX. I think you need to set WINEPREFIX to the right thing for firefox 3.5 before you run the msiexec thing.

---

### Post by dcottingham on 2011-11-03
To expand on that prefix thing a bit, when I did it I had to set WINEPREFIX to $HOME/.local/share/wineprefixes/firefox35

---

