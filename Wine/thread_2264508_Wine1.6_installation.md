---
title: "Wine1.6 installation"
date: 2015-02-08
forum: Wine
---

### Post by BISHAL_SANTRA on 2015-02-08
I am trying to install wine program. I first tried it from Ubuntu(14.04) software center but it gave some depedency error. Then I tried it with terminal but it failed. What do I do?
Find attached the error message I got using Software center.

---

### Post by Bucky Ball on 2015-02-08
*Thread moved to **Wine**.*

Welcome. This is the place. Hopefully you will have better luck here. ***Installations & Upgrades*** is for installing and upgrading the Ubuntu OS. ;)

If this is a new install, have you updated? Try these commands in a terminal, one after the other hitting enter between each. 

```
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

Then try and install Wine from the SCentre again.

Report any and all errors. 

PS: Please attach large pics by using 'Go Advanced' when editing a post, or 'Adv Reply' when creating one, and clicking on the paperclip icon. Thanks.

---

### Post by BISHAL_SANTRA on 2015-02-08
> **Bucky Ball said:**
> *Thread moved to **Wine**.*

Welcome. This is the place. Hopefully you will have better luck here. ***Installations & Upgrades*** is for installing and upgrading the Ubuntu OS. ;)

If this is a new install, have you updated? Try these commands in a terminal, one after the other hitting enter between each. 

```
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

Then try and install Wine from the SCentre again.

Report any and all errors. 

PS: Please attach large pics by using 'Go Advanced' when editing a post, or 'Adv Reply' when creating one, and clicking on the paperclip icon. Thanks.

I ran all the commands u gave in terminal.  But I am still getting the same errors.

---

### Post by ajgreeny on 2015-02-08
If I run ```
sudo apt-get install -s wine1.6
```to simulate what you are attempting to do everything is fine.

I note that several of the packages that are dependencies for you but can not be found, do not seem to show at all as needed in my output, or are already installed on my system (Xubuntu 14.04.1 64bit).

Tell us more about your system and any added repos, eg PPAs that you have added.  Also make sure that the universe and multiverse repos are enabled in your software sources.

Something very odd is going on here and it would be good to know why you have this problem, which should not be happening!

---

### Post by BISHAL_SANTRA on 2015-02-08
> **ajgreeny said:**
> If I run ```
sudo apt-get install -s wine1.6
```to simulate what you are attempting to do everything is fine.

I note that several of the packages that are dependencies for you but can not be found, do not seem to show at all as needed in my output, or are already installed on my system (Xubuntu 14.04.1 64bit).

Tell us more about your system and any added repos, eg PPAs that you have added.  Also make sure that the universe and multiverse repos are enabled in your software sources.

Something very odd is going on here and it would be good to know why you have this problem, which should not be happening!

This is all I can get [ATTACH=CONFIG]259828[/ATTACH]
I am not sure if it is the complete list of PPAs.

---

### Post by Bucky Ball on 2015-02-08
Perhaps remove or disable this added PPA:

[http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) trusty main

Uninstall any Wine you have installed, then:

```
sudo apt-get autoremove
sudo apt-get update
sudo apt-get install wine1.6
```

... and tell us what happens.

---

