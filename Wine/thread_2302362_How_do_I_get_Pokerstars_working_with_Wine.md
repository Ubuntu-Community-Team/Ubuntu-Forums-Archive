---
title: "How do I get Pokerstars working with Wine?"
date: 2015-11-09
forum: Wine
---

### Post by maxlemay141 on 2015-11-09
I installed wine (version 1.6.2). I downloaded the Pokerstars setup.exe file and ran it. Now when I try to run Pokerstars the client opens up for a few seconds but crashes during the loading period. What should I do?

---

### Post by howefield on 2015-11-10
Perhaps try the latest version of wine, doing so is not exactly trivial but it isn't difficult either.

The game gets a Gold rating with Wine 1.7.44 from one user at [https://appdb.winehq.org/appview.php?iVersionId=2899](https://appdb.winehq.org/appview.php?iVersionId=2899)

---

### Post by maxlemay141 on 2015-11-11
> **howefield said:**
> Perhaps try the latest version of wine, doing so is not exactly trivial but it isn't difficult either.

The game gets a Gold rating with Wine 1.7.44 from one user at [https://appdb.winehq.org/appview.php?iVersionId=2899](https://appdb.winehq.org/appview.php?iVersionId=2899)

How do I get Wine 1.7.44?

---

### Post by howefield on 2015-11-12
> **maxlemay141 said:**
> How do I get Wine 1.7.44?

I'd first suggest uninstalling the current version that you have, if you are using Ubuntu with the Unity interface, opening the Dash, searching for Wine then right clicking the Wine icon should give you an uninstall option. Or using the command line..

```
sudo apt-get --purge remove wine
```

Then open the File Manager and press Ctrl + H keys to show hidden files and delete the .wine folder if present. Or with the command line..

```
sudo rm ~/.wine
```

Graphical instructions for installing the PPA which contains the newer Wine packages can be found [here]("https://www.winehq.org/download/ubuntu").

From the command line..

```
sudo add-apt-repository ppa:ubuntu-wine/ppa
```
```
sudo apt-get update
```
```
sudo apt-get install wine1.7
```

---

