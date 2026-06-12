---
title: "Trying to add WINE Repository"
date: 2014-01-25
forum: Wine
---

### Post by Brendan_Doyle on 2014-01-25
I can't seem to ind the edit -> software sources that WINEs website wants me to find on the software center.

EDIT: I did it through the synaptic packager.

---

### Post by monkeybrain20122 on 2014-01-27
In synaptic go to Settings > Repositories > Other Software, click "add" and enter the apt line for the ppa  (ppa:ubuntu-wine/ppa) and click "add source". Then close the dialogue box and go to the upper left corner to click "reload" to update the database.

Alternatively you can add ppa in the terminal as follows:

```
sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update
```

The 'sudo apt-get update" is the same as reloading in synaptic.

---

