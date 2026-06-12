---
title: "What does Ubuntu Desktop do?"
date: 2007-12-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by John Jason Jordan on 2007-12-29
Since I cannot get Usplash working in Gutsy x86_64 (yes, I've read all the threads and nothing works), I decided to install splashy. In order to install splashy I had to uninstall Ubuntu Desktop.

My very dim understanding is that the function of Ubuntu Desktop is to keep track of what you have installed so that Update Manager will work. Indeed, I uninstalled Ubuntu Desktop two weeks ago and Update Manager keeps saying I am up to date. That sounds suspicious.

Can anyone shed more light on this? Is there someplace where Ubuntu Desktop is documented?

---

### Post by BreathEasy on 2007-12-29
Ubuntu Desktop is a meta-package that links several "important" packages together. Remove one that ubuntu desktop links with, and you'll get the message that ubuntu desktop will be removed as well. The package doesn't actually contain anything useful, merely links to other packages. It can be safely removed without trouble.

Not sure what's going on with this problem. I've used usplash in x64_64 Gutsy before, using the "startup-manager" package and downloading a **64-bit compatable usplash file** someone had made.

---

