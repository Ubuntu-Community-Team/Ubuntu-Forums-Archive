---
title: "bad sound"
date: 2008-10-30
forum: Wine
---

### Post by moggy812 on 2008-10-30
i have got some games to work in wine (wine 1.1.7)
however, my sounds are not as they could be, and wanted to know if there is anything i can do to help this...
im running on ubuntu 8.04
sound card is: HDA Intel at 0xd7dfc000 irq 16 
Driver: ALSA Version 1.0.16
if there is anything else you need to know, to help me along further, i will check back here from time to time and add any additional details as required.
my thanks to all those who can help.

---

### Post by Dark9204 on 2008-10-30
Hi
I used wine 1.1.7 before, and my sound were horrible! So i downgraded to wine 1.0.1. And that solved the problem.

---

### Post by moggy812 on 2008-10-30
ok, so how should i go about down grading to 1.0.1?

---

### Post by Dark9204 on 2008-10-30
In Synaptic package manager select "complete uninstall" then go to your home dir and select "show hidden folders" and delete your .wine folder.
Then remove wine from your software sources.
Now install wine from your package manager.

---

### Post by CJNyfalt on 2008-10-31
> **Dark9204 said:**
> In Synaptic package manager select "complete uninstall" then go to your home dir and select "show hidden folders" and delete your .wine folder.
Then remove wine from your software sources.
Now install wine from your package manager.

Remember to take a backup of your .wine folder, because this also removes all programs installed under wine.

---

### Post by das letzte einhorn on 2008-10-31
I am having this issue with every single game I have installed in wine. The last wine installment I had was 1.1.5 under Hardy, then I formatted to install Intrepid and Wine 1.1.7. I imported each of the prefixes (1 per game) that I had previously in my new installation of Ubuntu. Can someone else confirm that this is a regression in wine 1.1.7, or if something is wrong with my configuration. Thanks!

---

