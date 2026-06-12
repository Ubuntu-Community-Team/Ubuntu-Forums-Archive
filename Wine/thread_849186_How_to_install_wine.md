---
title: "How to install wine"
date: 2008-07-04
forum: Wine
---

### Post by that_is_lg on 2008-07-04
:confused:I'm usin' Ubuntu 8.04. I don't know how to install wine. Help me.
I'm a chicken, help me

---

### Post by thefishki345 on 2008-07-04
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

that should show you how to download wine, I am not sure if it is the lates version, once you have downloaded it, in the terminal (applications-accessories-terminal) type: wine
and then:

wine --version

if it says something like:
wine-1.0 or wine-1.10 thats the latest versions,

if it says something like:

wine-9.23 or wine 9.50 they arent the latest versions.

hope that helped...

---

### Post by barney385 on 2008-07-04
Wine isn't in the repo's?

I'm running update manager right now or I would check...

---

### Post by cogadh on 2008-07-04
Wine is in the repos. 0.9.59 is in the main repos and 1.0 stable is in the backports repo. For regular users, it is better to use Wine 1.0 stable from the backports instead 1.1.0 unstable from the WineHQ repository.

---

### Post by KamalGurung on 2008-07-05
It is showing too much dependencies , also winbind :( I am using 8.04 LTS where do I find this Winbind :( New to Ubuntu.

---

### Post by cogadh on 2008-07-06
All of Wine's dependencies are available through the normal Wine repositories. If you just install Wine from one of the repositories using Apt (or Synaptic), it will automatically install all the dependencies for you.

---

