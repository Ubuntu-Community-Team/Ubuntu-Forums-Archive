---
title: "Winetricks won't open in Lubuntu 12.10"
date: 2012-11-10
forum: Wine
---

### Post by PrinceOfJudah on 2012-11-10
I've installed Wine and when I click on Winetricks nothing happens. This was not an issue in Ubuntu 12.04. I am now using Lubuntu 12.10.

---

### Post by Bloodrat on 2012-11-25
Acessories - open LXTerminal

sudo apt-get install zenity

voila

---

### Post by tnasniv on 2013-01-28
Thanks it worked.

---

### Post by archmagus501 on 2013-01-29
> **Bloodrat said:**
> Acessories - open LXTerminal

sudo apt-get install zenity

voila
I have the same problem with Winetricks, but when I run "apt-get install zenity" in LXTerminal:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package zenity is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'zenity' has no installation candidate

---

