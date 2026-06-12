---
title: "EXTREMELY low FPS on HL2"
date: 2008-01-20
forum: Wine
---

### Post by Cardamar on 2008-01-20
Here's the problem:

I'm trying to run HL2 under Wine 0.9.53 and I'm getting incredibly low FPS. 10 to be exact. I just can't get anything over that. No matter what settings I used, be they extremely high or extremely low, I just CAN'T get anything above 10fps. Even if I turn my effects off, I still only get 10. This doesn't make any sense, considering my specs ((which are listed in my signature)). Can anyone provide any help at all here? Also, my drivers are downloaded using Envy.

I thought that the new Wine might be the problem, so I tried to downgrade to .52 ((which worked fine for me)), but I got this output:
```

colin@GLaDOS:~$ /home/colin/Desktop/wine-0.9.52/tools/wineinstall
WINE Installer v0.75

You're running this from the wrong directory.
Change to the Wine source's main directory and try again.
```

Any ideas what that's all about?

Any help is GREATLY appreciated. Thanks in advance.

---

### Post by dataless on 2008-01-20
I had the same problem running counter strike source under wine, the way i am running it atm is to run it in dx8. My fps is fine now 70+ maxed out :) 


Try putting -dxlevel 81 in the hl2 launch options and see if that helps.

---

