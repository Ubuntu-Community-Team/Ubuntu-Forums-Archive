---
title: "Unable to install anything using adept"
date: 2008-04-27
forum: x86 64-bit Users
---

### Post by sonshadowcat on 2008-04-27
I'm trying to install the restricted drivers but I keep getting an error that says theres an error commiting changes and that downloading the packages or the commit would break packages.


At first I thought there might be just something wrong with that specific package but it turns out I can't install anything anymore. This is odd since I was installing things just fine earlier.


Anyone have any ideas?

---

### Post by stmiller on 2008-04-28
Try this in the konsole:
```

sudo apt-get -f install

```

---

### Post by beartard on 2008-04-28
That's the main reason I absolutely *despise* adept.  If something minor happens to one package, it aborts all installs and wipes away all the package choices you've made.  I use Synaptic under KDE and have for a long time.  It's the best thing Ubuntu has going for it as far as graphical package management.

---

