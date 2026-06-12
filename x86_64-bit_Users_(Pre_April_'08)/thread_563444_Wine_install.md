---
title: "Wine install"
date: 2007-09-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by magikx21 on 2007-09-30
I am trying to install Wine on an AMD64 box running Kubuntu Fesity and when I got into Add/remove packages and search for Wine the logo and text for Wine is greyed out. Why is this and how can I go about installing Wine now?

---

### Post by sirgogo on 2007-09-30
This is because the repositories have not been added to your manager.

An easy way to install wine is through the terminal.

So open up a terminal window and type in (the best way is to copy and paste all this stuff):

*wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -*

Now add it to your repositories:
[I]
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list](http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/winehq.list[/I]

So now it is in your repositories and you can install it using your manager. But better yet (and quicker too!) you can install them using the terminal by typing:

*sudo apt-get update*

and then:
[I]
sudo apt-get install wine[/I]


Let me know how it goes!

---

### Post by magikx21 on 2007-09-30
Ok, thanks I got it all up and running. On my PC with the 32bit version I didn't have to do this, so I thought that I messed something up.

---

