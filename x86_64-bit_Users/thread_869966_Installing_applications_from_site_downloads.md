---
title: "Installing applications from site downloads"
date: 2008-07-25
forum: x86 64-bit Users
---

### Post by marvlowe on 2008-07-25
I down loaded kmymoney from their web site and extracted the files to home folder. How do I actually go about installing the application?

Marv Lowe

---

### Post by logos34 on 2008-07-25
use the one already in the universe repo:

sudo apt-get install kmymoney2

---

### Post by tamoneya on 2008-07-25
right click on the .tar.gz and select extract here.  Then open terminal(applications -> accessories -> terminal) and move to the newly extracted directory.  There you just need to run: ```
./configure
```If you get some complaints about permissions or sudo just run this:```
sudo ./configure
```

---

### Post by match002001 on 2008-07-25
> **logos34 said:**
> use the one already in the universe repo:

sudo apt-get install kmymoney2

Trust me, listen to logos34 this is the easiest way without the headache.

The reason why is that you need to find the dependanceies, then after that those dependancies have dependacies and so on and so forth.

In conclusion, use Synaptic or open terminal and type in:

```
sudo apt-get install kmymoney2
```

---

### Post by marvlowe on 2008-07-25
Thanks for the help. I used the one in the universal repo: How does one fine out what all the applications that are available there. I thought that readily available applications would be found by going to Applications and Add/Remove.

Marv Lowe

---

### Post by Stele on 2008-07-25
You can use Synaptic and see all the packages available from your current repositories.

From a console:
gksudo synaptic

From the menu:
System --> Administration --> Synaptic Package Manager

---

### Post by Kilz on 2008-07-25
> **marvlowe said:**
> Thanks for the help. I used the one in the universal repo: How does one fine out what all the applications that are available there. I thought that readily available applications would be found by going to Applications and Add/Remove.

Marv Lowe

[You can also look here]("http://packages.ubuntu.com/") and search, its the package (repositories) page for Ubuntu. The Add/Remove applications is a lightweight application for only a few of the most common applications. Synaptic has everything.

---

### Post by Yellow Pasque on 2008-07-26
Synaptic has a nice search function built into it.

---

