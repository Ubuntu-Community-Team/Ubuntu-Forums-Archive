---
title: "[SOLVED] Why is Wine not being updated?"
date: 2007-12-07
forum: Wine
---

### Post by BattleGnome on 2007-12-07
Hi,

I am running ubuntu 7.10 and have installed Wine through the package manager.

My wine version is 0.9.46, I noticed on the official wine site the version is now at 0.9.50. I am just wondering why an update has not come through the ubuntu update manager?

Under update sources I have Main, Universe, Restricted and multiverse enabled.

---

### Post by cogadh on 2007-12-07
The only way to get the latest Wine is to add the official Wine repositories to apt. By default, the Ubuntu repositories will only have the version of Wine that was out when your version of Ubuntu was released. In the case of Gutsy, that means 0.9.46. 

To add the official Wine repositories, follow the instructions here:
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

