---
title: "Well.... WINE"
date: 2007-09-18
forum: Wine
---

### Post by Melganis on 2007-09-18
ok, so i accidently set the desktop window to an extremely small size, and can no longer actually change it back, so i can't run winecfg as i can only see the tabs, and not what is below that, can anyone tell me what to do?

---

### Post by splintercellguy on 2007-09-18
You'll have to edit ~/.wine/user.reg and remove this line:
"Desktop"="640x480"

---

### Post by deadlydeathcone on 2007-09-19
I happened upon this when searching through Wine's documentation for things to add to my wine script:

```
wine explorer /desktop=desktop,1024x768 winecfg.exe
```

---

