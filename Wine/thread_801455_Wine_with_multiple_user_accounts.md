---
title: "Wine with multiple user accounts"
date: 2008-05-20
forum: Wine
---

### Post by freesitebuilder on 2008-05-20
I have three other users on my PC besides my own account. I'm running Ubuntu 8.04, I installed wine under 7.10

How do I determine which wine apps can be run by all users? I've installed WoW for my sons, but they have to run it on my account at the moment, which means resetting all my desktop effects every time I want to use my account!

I've set the properties to allow execution by others, but it doesn't appear on their menus or in the "Browse C/:" window. What else do I need to do?

TIA

---

### Post by elvinatom on 2008-05-20
Wine creates it's working directory (.wine) into every users home directory and I do believe that wine insists it to belong to the user that's running it (which makes it impossible to run Joe's wine apps as Bill). I'm far from an expert so you might wanna google around about that - I wouldn't know how to change it.

---

