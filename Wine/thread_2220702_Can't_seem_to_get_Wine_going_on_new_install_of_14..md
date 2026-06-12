---
title: "Can't seem to get Wine going on new install of 14.04"
date: 2014-04-29
forum: Wine
---

### Post by paul1945 on 2014-04-29
Installed Ubuntu 10.04 but I cannot seem to get Wine going.
I have tried to re-install it but to no avail.
When re-installing it it comes up with the Eula for the core fonts and stops there.
I am a beginner so am probably doing something wrong.
Could someone give me the commands/procedure to sort this out?
Thanks. Paul.

---

### Post by kc1di on 2014-04-29
go to a teminal and try to install from there.  if you get any error messages post them here. 
use these commands:
```
sudo apt-get update
sudo apt-get install wine 
```

---

### Post by Bill Tetzeli on 2014-05-04
By installing Wine I assume you mean winetricks, right?  When the EULA comes up, do you TAB until the "OK" button is highlighted, then press ENTER?  The TAB and arrow keys will allow you to highlight the appropriate buttons so you can press ENTER to confirm.

BTW, this is one of those rare occasions where installing via the Software Center should prove easier than using apt-get install.  The EULA will come up as a popup window, then you just click on Agree and away you go.  Dealing with dialog boxes in the terminal can be a bit tricky if you're not used to it.

---

### Post by paul1945 on 2014-05-06
Thanks for that, did just that and it worked.
Easy as.

---

