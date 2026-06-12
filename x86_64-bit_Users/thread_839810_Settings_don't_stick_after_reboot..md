---
title: "Settings don't stick after reboot."
date: 2008-06-24
forum: x86 64-bit Users
---

### Post by onering on 2008-06-24
New installation of Ubuntu 8.04.  

1) I installed EnvyNG and the nVidia options.  8600GTSOC card.  I run the nVidia x-Server settings by running "sudo nvidia-setting" and change the resolution.  The resolution looks fine until I reboot, then it goes back to the original default of 1600x1200.

2) After a reboot, Firefox seems to loose my cookies.  I have to "relogin" to websites that I already told it to remember.  This only happens on a reboot, not a close and reopen of Firefox.

Help... :confused:

---

### Post by beniwtv on 2008-06-25
1) Just as silly question, did you press 'Save' in nvidia-settings? Did it give any error? What is the resulting /etc/X11/xorg.conf? (Post it here)

2) Maybe Firefox does not really exit. Try to go to the System monitor and see if firefox exits after you close it. That may explain the difference between reboot/close. 

Another cause could be you saving cookies into /tmp? (See your settings) -> This directory gets wiped on reboot.

Also check that you don't have enabled the automatic cleaning of your personal data in firefox's preferences.

Cheers,

---

