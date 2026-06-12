---
title: "HowTo: Get The Latest Wine"
date: 2007-11-27
forum: Wine
---

### Post by Cochise on 2007-11-27
**1.** Remove the wine that comes with Ubuntu (if you've installed it)(sudo apt-get remove wine)

**2.** Open a terminal and type:

> wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

**3.** Type:

> gksudo gedit /etc/apt/sources.list

**4.** Add one of the following to your sources.list

> ## Wine, Ubuntu Hardy Heron (8.04):
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) hardy main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) hardy main

> ## Wine, Ubuntu Gutsy Gibbon (7.10):
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) gutsy main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) gutsy main

> ## Wine, Ubuntu Feisty Fawn (7.04):
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) feisty main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) feisty main

> ## Wine, Ubuntu Edgy Eft (6.10)
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main

> ## Wine, Ubuntu Dapper Drake (6.06)
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

**5.** Type the following:

> sudo apt-get update

**6.** Type the following:

> sudo apt-get upgrade

**7.** To install wine either type:

> sudo apt-get install wine

Or by using the Synaptic Package Manager under System->Administration.

------------------------------------------------------------------------------
Edited on 15/05/08 - Added Hardy Heron (8.04)

---

