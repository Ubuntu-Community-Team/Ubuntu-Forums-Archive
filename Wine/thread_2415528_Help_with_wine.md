---
title: "Help with wine"
date: 2019-03-27
forum: Wine
---

### Post by ymurti2 on 2019-03-27
Please can someone help me? I have installed wine but I cannot launch it. See attachment.

Thank You!

---

### Post by mastablasta on 2019-03-28
what happens if you right click on a program in file manager and select run with wine?

---

### Post by kc1di on 2019-03-28
from that screen shot it looks like you have not installed wine yet.
have you done what it said. ```
sudo apt install wine-stable 
``` ?

I would also install ```
sudo apt install wine32
```

Then try to run your windows app with this commnad (note you must use the full address to the app) ```
wine <app.exe>
``` Replace app with correct name. 

Also you may want to take a look at playonlinux it can be installed with this command ```
sudo apt install playonlinux
``` it's a front end for wine and can make running some windows apps easier. Good Luck.

---

