---
title: "Wine Not Showing in the App Launcher"
date: 2018-04-17
forum: Wine
---

### Post by open4epl on 2018-04-17
I installed wine 3.0 but it's not showing up in the App Launcher in version 18.4. What's the solution?

---

### Post by mc4man on 2018-04-17
wine (in ubuntu) now ships without any .desktop files so there's nothing to find in apps or even the context menu on .exe files.
Pretty stupid..
I use this version for 18.04, it includes all the .desktop & menu files.
[https://launchpad.net/~zorinos/+archive/ubuntu/wine-testing](https://launchpad.net/~zorinos/+archive/ubuntu/wine-testing)

---

### Post by open4epl on 2018-04-17
> **mc4man said:**
> wine (in ubuntu) now ships without any .desktop files so there's nothing to find in apps or even the context menu on .exe files.
Pretty stupid..
I use this version for 18.04, it includes all the .desktop & menu files.
[https://launchpad.net/~zorinos/+archive/ubuntu/wine-testing](https://launchpad.net/~zorinos/+archive/ubuntu/wine-testing)

Thanks a bunch & it has Win10 & it's 3.0. =d>

---

### Post by armrek on 2018-04-21
> **mc4man said:**
> wine (in ubuntu) now ships without any .desktop files so there's nothing to find in apps or even the context menu on .exe files.
Pretty stupid..
I use this version for 18.04, it includes all the .desktop & menu files.
[https://launchpad.net/~zorinos/+archive/ubuntu/wine-testing](https://launchpad.net/~zorinos/+archive/ubuntu/wine-testing)

I installed it like this:
sudo add-apt-repository ppa:zorinos/wine-testing
sudo apt-get update
sudo apt-get upgrade
But cannot see wine any where ?

---

