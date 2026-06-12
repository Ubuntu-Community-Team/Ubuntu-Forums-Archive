---
title: "Wine Uninstallation"
date: 2008-01-17
forum: Wine
---

### Post by gwoodard on 2008-01-17
Hello, I would like to know how to properly uninstall Wine and install Wine anew (everything cleaned including programs)

---

### Post by hikaricore on 2008-01-17
```
sudo apt-get remove --purge wine
```

---

### Post by gwoodard on 2008-01-18
Thank you, I will try it once I switch over to Ubuntu

---

### Post by hikaricore on 2008-01-18
Sorry those were just the steps to remove it.

I kinda just assumed you already had it installed and didn't see the end half of your post.  O.o
To install it you'd need to already have the universe repos or the WINE repos at budgetdedicated enabled.

```
sudo apt-get install wine
```

---

### Post by Faud on 2008-01-19
```

sudo apt-get remove --purge wine*

```
destroyed my gnome...no joke. I cant do anything now. I cant even open a terminal

---

### Post by b0rka7a on 2008-01-19
Why not just:
```
sudo apt-get remove wine
rm -r ~/.wine
```
and then
```
sudo apt-get install wine
```
What does "--purge" do ?

---

### Post by hikaricore on 2008-01-19
> **Faud said:**
> ```

sudo apt-get remove --purge wine*

```
destroyed my gnome...no joke. I cant do anything now. I cant even open a terminal

O.o  That was a typo..  I've fixed it now.

I've tested this out and it seems to remove a hell of a lot of packages, tho I can't imagine why.  You should pay attention to the items being removed before pressing Y in a terminal.  When in doubt, ask questions.

---

### Post by hikaricore on 2008-01-19
> **b0rka7a said:**
> Why not just:
```
sudo apt-get remove wine
rm -r ~/.wine
```
and then
```
sudo apt-get install wine
```
What does "--purge" do ?

Purge removes any program configuration files/directories.  Aka the .wine folder without the extra step.

---

### Post by Faud on 2008-01-19
Well here I am back after a fresh install.

Hikaricore. I didnt attack you or your code in any way in my thread and the reason is because I knew better then to put that * there but I figured ahhh what the heck 
#1 Ubuntu easy reinstall FTW
#2 Seperate home partation ftw
#3 Hikaricore owes me coffee, double win.
I was just warning that there was a typo.
But hey, the bonus is that Im much more awake now :guitar:

PS. I do want that coffee though =P

---

