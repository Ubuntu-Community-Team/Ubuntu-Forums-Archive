---
title: "installing game"
date: 2008-10-19
forum: Wine
---

### Post by sporkling on 2008-10-19
ok im trying to install a game call counter strike from a disc. but instead of a install screen poping up this does [IMG]http://i443.photobucket.com/albums/qq153/sporkme101/Screenshot.png[/IMG]with weird symbols and things what do i do?

---

### Post by MaxIBoy on 2008-10-19
Type this into a terminal: 
```
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list -O /etc/apt/sources.list.d/winehq.list
```
Then, follow these instructions (IMPORTANT: skip to step 2.3 of the instructions, as that above command will install a much more up-to-date version of WINE than what they're linking to.)
[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games)

---

