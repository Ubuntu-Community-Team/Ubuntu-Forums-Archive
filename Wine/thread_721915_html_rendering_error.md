---
title: "html rendering error"
date: 2008-03-11
forum: Wine
---

### Post by gawdin on 2008-03-11
I am trying to use wine to execute an executable file (shock!!!) when it runs it asks me to install Gecko, so i do but then it says html rendering is disabled... how do I enable this so that I can see the link page that the executable brings up?

---

### Post by fwre01 on 2008-07-12
I also have the same problem when trying to run iexplorer (im not sure of the ie version) i have Wine 1.1.0. I am prompted to install gecko when it starts up, i click the install button and nothing happens, the dialoge box disappears and i get the "html rendering is disabled" message appear.

---

### Post by prshah on 2008-07-12
> **gawdin said:**
> I am trying to use wine to execute an executable file (shock!!!) when it runs it asks me to install Gecko, so i do but then it says html rendering is disabled... how do I enable this so that I can see the link page that the executable brings up?

> **fwre01 said:**
> I also have the same problem when trying to run iexplorer (im not sure of the ie version) i have Wine 1.1.0. I am prompted to install gecko when it starts up, i click the install button and nothing happens, the dialoge box disappears and i get the "html rendering is disabled" message appear.

How did you install WINE? did you add the winehq apt repository (budgetdedicated.com) to your software sources as [suggested here?]("http://www.winehq.org/site/download-deb") If you did, then it should download and install Gecko fine.

If for some reason it cannot download and install Gecko, and you want to do so manually, see [http://www.winehq.org/pipermail/wine-users/2007-June/027385.html](http://www.winehq.org/pipermail/wine-users/2007-June/027385.html)

---

### Post by fwre01 on 2008-07-13
Hmmmmm....coincidentally, i just got a Wine update and then i clicked the install button and it went away and did something, now it works when i use the command 
```
wine iexplore.exe http://www.google.com
```

Thanks tho!

---

