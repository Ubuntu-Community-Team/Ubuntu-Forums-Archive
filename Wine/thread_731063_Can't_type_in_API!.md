---
title: "Can't type in API!"
date: 2008-03-21
forum: Wine
---

### Post by coolgamer512 on 2008-03-21
I am using Wubi Ubuntu Fiesty Fawn (7.04)

I typed the following code in a terminal and it went smoothly:

wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add 

So I looked and it is now on the trusted API key list (or trusted software providers). Then I tried to go to the 3rd party software to add the following API line:

sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list](http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/winehq.list

The Add Source button remains greyed out.

What am I doing wrong?

---

