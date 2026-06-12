---
title: "AppImage files not launching after installing Wine on Ubuntu"
date: 2019-02-26
forum: Wine
---

### Post by ramesh-chandr on 2019-02-26
[FONT=Helvetica]Hi,
I am not able to launch any AppImage file after I installed Wine in my Ubuntu (18.10) system. Ubuntu considering AppImage files as Wine application.
How to reset it back to AppImage?

[/FONT]
[FONT=Helvetica]Thanks[/FONT]

---

### Post by kc1di on 2019-02-28
Hello ramesh-chandr,
Go to one of the apt image files and right click on it and under properties make sure under the permissions tab that the box is check for allow file to run as program or something similar to that, I don't have Gnome up at the moment so not sure what it says. 

also wine maybe listed as open with. delete that entry. 
Good luck.

---

### Post by ramesh-chandr on 2019-02-28
Thank you. It's working now.

---

### Post by kc1di on 2019-03-01
Glad it's working for you :)

---

