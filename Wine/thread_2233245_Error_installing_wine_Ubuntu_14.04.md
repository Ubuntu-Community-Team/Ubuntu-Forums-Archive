---
title: "Error installing wine Ubuntu 14.04"
date: 2014-07-07
forum: Wine
---

### Post by dlsmoker on 2014-07-07
Hi, I just installed Ubuntu 14.04 and I am trying to install Wine but [this error occures]("https://i.imgur.com/1wAMFRU.jpg") .

I already tried _[solution1]("http://askubuntu.com/questions/364798/unmet-dependencies-while-installing-wine") , [solution2]("http://askubuntu.com/questions/138530/why-do-i-get-an-unmet-dependencies-error-when-trying-to-install-wine/190424#190424") _( this particular method messed up my entire system and I had to re-install ubuntu because no command was working anymore in the terminal )

Just for the record, I could install it successfully on Ubuntu 12.10.

Any help will be appreciated.

---

### Post by ibjsb4 on 2014-07-07
Unless there is a reason you need the ppa install, why not just use the stable version located in the software center.

[https://help.ubuntu.com/community/Wine#Newer_versions_of_Wine_.28Not_Recommended.29](https://help.ubuntu.com/community/Wine#Newer_versions_of_Wine_.28Not_Recommended.29)

---

### Post by dlsmoker on 2014-07-08
> **ibjsb4 said:**
> Unless there is a reason you need the ppa install, why not just use the stable version located in the software center.

[https://help.ubuntu.com/community/Wine#Newer_versions_of_Wine_.28Not_Recommended.29](https://help.ubuntu.com/community/Wine#Newer_versions_of_Wine_.28Not_Recommended.29)

Using your method gives me the exact same error message. I also tried getting it from the "App Center", same error.

I tried to install some of the dependencies listed in the error and now only these are displayed [https://i.imgur.com/bNXMqgf.jpg](https://i.imgur.com/bNXMqgf.jpg)

---

### Post by ibjsb4 on 2014-07-08
Did you remove the ppa prior to installing from App Center?

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remove+ppa&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remove+ppa&sa=Search&cof=FORID:9)

---

### Post by dlsmoker on 2014-07-08
> **ibjsb4 said:**
> Did you remove the ppa prior to installing from App Center?

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remove+ppa&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remove+ppa&sa=Search&cof=FORID:9)

I tried to uninstall all PPAs I had but it didn't work either. IN the end I re-installed Ubuntu and I got Wine from the "Software Center" as the first thing and now it runs well.

---

### Post by ibjsb4 on 2014-07-08
Next time try ppa-manager, its in the software center :)

[http://packages.ubuntu.com/lucid-backports/ppa-purge](http://packages.ubuntu.com/lucid-backports/ppa-purge)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

