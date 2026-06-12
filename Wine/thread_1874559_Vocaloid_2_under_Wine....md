---
title: "Vocaloid 2 under Wine..."
date: 2011-11-03
forum: Wine
---

### Post by luks255 on 2011-11-03
Ok, so, another problem. I could upgrade wine to 1.3.15.
Installed Vocaloid2 Miku Hatsune. All went great.
Then I tried to run it. This is the terminal output:

```
lucas@stoews-desktop:~$ cd .wine/drive_c/Prog*/VOCALOID2
lucas@stoews-desktop:~/.wine/drive_c/Program Files/VOCALOID2$ wine VOCALOID2.exe
fixme:ntdll:find_reg_tz_info Can't find matching timezone information in the registry for bias 180, std (d/m/y): 0/00/0000, dlt (d/m/y): 0/00/0000
lucas@stoews-desktop:~/.wine/drive_c/Program Files/VOCALOID2$ 

```

Any suggestion?

EDIT: Whoops, 1.3.15 isn't last version... Gonna check with 1.3.26 (That according to WineHQ APPDB, Vocaloid2 runs flawlessly under that version .-.)

-luks255

---

### Post by luks255 on 2011-11-04
Allright, tried with WINE 1.3.26, still the same:

```
fixme:ntdll:find_reg_tz_info Can't find matching timezone information in the registry for bias 180, std (d/m/y): 0/00/0000, dlt (d/m/y): 0/00/0000
```

Any help? =S

---

### Post by luks255 on 2011-11-04
Ok I managed to get it to work. But, it won't let me play any audio, like if I do the preview thingie, it would throw this:

"Cannot output wave (Undefined external error.)"

Any help?

EDIT: It seems like downgrading to 1.2.2 solved the problem (y)

---

