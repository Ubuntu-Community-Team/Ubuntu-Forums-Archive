---
title: "Running winecfg from a directory other than ~/.wine"
date: 2008-09-01
forum: Wine
---

### Post by Omega234 on 2008-09-01
Hello, everyone!

I've recently installed wine 1.1.0 in its own little directory: [FONT="Courier New"]/home/omega/Wine_Bottles/1.1.0[/FONT].  I've run [FONT="Courier New"]/home/omega/Wine_Bottles/1.1.0/bin/wineprefixcreate --prefix /home/omega/Wine_Bottles/1.1.0/main[/FONT], and the prefix was successfully created (there are files in it and whatnot).  However, I can't manage to run [FONT="Courier New"]winecfg[/FONT] out of this new prefix - it always runs out of [FONT="Courier New"]/home/omega/.wine[/FONT].  How can I get around this?  If I can't, is there something else I should do instead?

Just to detail:  I've been running [FONT="Courier New"]winecfg[/FONT] with the full path name, I've set [FONT="Courier New"]WINEPREFIX[/FONT] to be "[FONT="Courier New"]/home/omega/Wine_Bottles/1.1.0/main[/FONT]" and run [FONT="Courier New"]/home/omega/Wine_Bottles/1.1.0/bin/winecfg[/FONT], I've tried doing it all as one command with [FONT="Courier New"]env WINEPREFIX="/home/omega/Wine_Bottles/1.1.0/main" /home/omega/Wine_Bottles/1.1.0/bin/winecfg[/FONT], but it continues to run out of [FONT="Courier New"]/home/omega/.wine[/FONT].

I'd rather not have to create a link from [FONT="Courier New"]/home/omega/.wine[/FONT] to [FONT="Courier New"]/home/omega/Wine_Bottles/1.1.0/main[/FONT], because I intend to install multiple different versions of wine (so that I always have a stable version for each program, but so I can try them on newer releases without worrying about losing everything).

All help is appreciated!

---

### Post by Bios Element on 2008-09-01
To run winecfg for a secondary wine directory you run this. Not quite sure this is what you need but here ya go.
```

env WINEPREFIX="*path to directory*" winecfg

```

---

### Post by Omega234 on 2008-09-07
Sorry for the late reply - I've been gone.

That works fine now.  Thanks for the help!

---

