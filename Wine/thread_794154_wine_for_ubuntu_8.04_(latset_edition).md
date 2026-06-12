---
title: "wine for ubuntu 8.04 (latset edition)"
date: 2008-05-14
forum: Wine
---

### Post by micho119 on 2008-05-14
hi all,
I need a wine for latest ubuntu edition
i hope u can help me

---

### Post by cogadh on 2008-05-14
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

### Post by cesarpachon on 2008-05-15
hello, I tried the instructions there, but it does not exist a file called hardy.list in that server. you can check it by yourself: enter at [http://wine.budgetdedicated.com/apt/sources.list.d/](http://wine.budgetdedicated.com/apt/sources.list.d/) and you can see the following files:
[ ]	dapper.list	18-Jan-2007 22:17 	151
[ ]	edgy.list	18-Jan-2007 22:17 	139
[ ]	etch.list	26-May-2007 21:49 	160
[ ]	feisty.list	26-May-2007 21:47 	181
[ ]	gutsy.list
so, it there is no way to install for ubuntu 8.04 (handy)
:(

---

### Post by Half-Left on 2008-05-15
> **cesarpachon said:**
> hello, I tried the instructions there, but it does not exist a file called hardy.list in that server. you can check it by yourself: enter at [http://wine.budgetdedicated.com/apt/sources.list.d/](http://wine.budgetdedicated.com/apt/sources.list.d/) and you can see the following files:
[ ]	dapper.list	18-Jan-2007 22:17 	151
[ ]	edgy.list	18-Jan-2007 22:17 	139
[ ]	etch.list	26-May-2007 21:49 	160
[ ]	feisty.list	26-May-2007 21:47 	181
[ ]	gutsy.list
so, it there is no way to install for ubuntu 8.04 (handy)
:(


Just do copy this into the terminal and refresh synaptic.

```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```

```
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list -O /etc/apt/sources.list.d/winehq.list
```

---

### Post by cogadh on 2008-05-15
The Hardy list is definitely there when I visit the index. 

Just follow the instructions Half-Left posted and make sure you run "sudo apt-get update" afterwards, then run "sudo apt-get install wine".

---

