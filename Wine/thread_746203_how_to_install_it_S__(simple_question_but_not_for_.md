---
title: "how to install it :S  (simple question but not for linux newbiez)"
date: 2008-04-05
forum: Wine
---

### Post by ryansdistrict on 2008-04-05
hi i am new to ubuntu
i just wanted to know how can i install wine 
i downloaded the latest package which is .tar.bz2

Please help is appreciated
Thankx

---

### Post by kostkon on 2008-04-05
No, this is not the right way to install it. First of all, *Wine* is in the *Ubuntu* repositories, so you can just open *Synaptic*, search for it and install it.

Nevertheless, the version of *Wine* in the *Ubuntu* repositories is not the latest one. 

Thus, if you want to install the latest one and get automatic updates every time there is a new version then just follow [these instructions on how to add its repository to your software sources list]("http://www.winehq.org/site/download-deb").

---

### Post by ryansdistrict on 2008-04-05
ok i opened Synaptic package manager 
and searched for *wine*
no result for it 
is this the proper way to search ?

Thanks Ubuntu rocks

---

### Post by kostkon on 2008-04-05
> **ryansdistrict said:**
> ok i opened Synaptic package manager 
and searched for *wine*
no result for it 
is this the proper way to search ?

Thanks Ubuntu rocks
Please, check if you have all of your repositories enabled, by going to *System -> Administration -> Software Sources* and checking if all of the options are selected in the first tab, i.e. *main*, *universe*, *restricted*, *multiverse*. Press *Close* and then try again to install *Wine* using *Synaptic*.

I forgot to tell you that a third way to install *Wine* is to download a .deb from [Wine's package archive]("http://wine.budgetdedicated.com/archive/index.html") and double click on it.

Nevertheless, I would recommend you to install its repository, I believe it's the best solution, since you'll get an automatic update every time there is a new version.

---

### Post by ryansdistrict on 2008-04-05
> **kostkon said:**
> Please, check if you have all of your repositories enabled, by going to *System -> Administration -> Software Sources* and checking if all of the options are selected in the first tab, i.e. *main*, *universe*, *restricted*, *multiverse*. Press *Close* and then try again to install *Wine* using *Synaptic*.

I forgot to tell you that a third way to install *Wine* is to download a .deb from [Wine's package archive]("http://wine.budgetdedicated.com/archive/index.html") and double click on it.

Nevertheless, I would recommend you to install its repository, I believe it's the best solution, since you'll get an automatic update every time there is a new version.

i went and checked all options then closed and reopened the synaptic and searched still couldnt find wine :(
by the way i got the latest stable non beta version of ubuntu

---

### Post by aoanla on 2008-04-05
Well, there's something very odd going on, then, because I can confirm that, not only does the latest, non-beta version of Ubuntu enable all repositories by default, but also, searching for "wine" in Synaptic should give you Wine 0.9.46, which is the version in said repositories.

I suggest you follow the alternate install approach, involving downloading a .deb from the link and clicking on it. ;)

---

### Post by lswest on 2008-04-05
run ```
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/winehq.list
``` in the terminal, then run ```
sudo apt-get install wine
``` it will then install the newest version.

---

