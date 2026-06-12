---
title: "How to install Wine 0.9.57"
date: 2008-03-12
forum: Wine
---

### Post by geovino on 2008-03-12
How do install wine 0.9.57? 

I have version 0.9.46 (in Gutsy) and Dreamweaver 8 and Fireworks MX are installed, but don't work very well.

Maybe this new version can run them better.

Has anyone else installed the new version of Wine?

---

### Post by 00arthuryu on 2008-03-12
add the signiture
```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```
add the repo
```
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/winehq.list
```
then do
```
sudo apt-get update
sudo apt-get install wine
```
 :)
or if you've done this already, then it should come up in the update manager, if not then
```
sudo apt-get install wine
```
hope this helps!
arthy

---

### Post by Twitch6000 on 2008-03-12
Just use update manager to update it?
The update for wine came out for ubuntu and ebain the same day wine 0.9.57 did.

---

### Post by geovino on 2008-03-13
> **Twitch6000 said:**
> Just use update manager to update it?
The update for wine came out for ubuntu and ebain the same day wine 0.9.57 did.

I just did a apt-get update and did a search for Wine and it still shows the old version. Do I have to change or add repos to install it?

---

### Post by geovino on 2008-03-13
> **00arthuryu said:**
> add the signiture
```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```
add the repo
```
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/winehq.list
```
then do
```
sudo apt-get update
sudo apt-get install wine
```
 :)
or if you've done this already, then it should come up in the update manager, if not then
```
sudo apt-get install wine
```
hope this helps!
arthy

Wine is already installed, will this install over it?

---

### Post by s3a on 2008-03-13
0.9.46 is the newest SUPPORTED version (to my knowledge), I think that's why it doesn't update through the updated. Go to : [http://wine.budgetdedicated.com/](http://wine.budgetdedicated.com/) for .debs of all Wine versions. Get the version you want and install but REMOVE THE OLDER VERSION FIRST (sudo apt-get remove wine).

---

### Post by 00arthuryu on 2008-03-15
> **geovino said:**
> Wine is already installed, will this install over it?

yes, it will update it as the repos will say that the one that you have now is the older one, and will install the new one for you :)

arthy

---

