---
title: "Problems trying to install Wine Staging on Ubuntu 18.10"
date: 2019-01-11
forum: Wine
---

### Post by putz30002 on 2019-01-11
I am following a tutorial so that I can get World of Warcraft installed on my Ubuntu 18.10 install. The instructions I am following say to install Lutris which is wanting me to enable and install Wine Staging and links to the Wine Wiki page. But I a keep getting an error trying to add the repository and have not figured out yet what the problem is. It is beyond me and I guess my google search terms have not been good enough to deliver an answer.

Here is what I have done:

sudo dpkg --add-architecture i386
wget -nc [https://dl.winehq.org/wine-builds/winehq.key](https://dl.winehq.org/wine-builds/winehq.key)
sudo apt-key add winehq.key

What is not working for me:

Sudo apt-add-repository 'deb [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) cosmic main'

The result:

E: Malformed entry 58 in list file /etc/apt/sources.list (Component)
E: The list of sources could not be read.


Here is the Wine section of my sources.list file:

 # see the sources.list(5) manual.
deb [https://dl.winehq.org/wine-builds/ubuntu/cosmic](https://dl.winehq.org/wine-builds/ubuntu/cosmic) main

 # deb-src [https://dl.winehq.org/wine-builds/ubuntu/cosmic](https://dl.winehq.org/wine-builds/ubuntu/cosmic) main
 deb [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) cosmic main main/ main./
 # deb-src [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) cosmic main
 # deb-src [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) cosmic main
 # deb-src [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) cosmic main
 # deb-src [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) cosmic main
 # deb-src [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) cosmic main./
 # deb-src [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) cosmic main/
 # deb-src [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) cosmic main./
 # deb-src [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) cosmic main
 # deb-src [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) cosmic main/
 deb [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) cosmic/main
 # deb-src [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) cosmic/main

If my counting is correct, I believe line 58 is line 2 of the above output. What am I doing wrong?

---

### Post by CatKiller on 2019-01-12
You don't need all those entries, and several of them are malformed - I'd guess from repeated invocations from the command line.

```
deb https://dl.winehq.org/wine-builds/ubuntu cosmic main

# deb-src https://dl.winehq.org/wine-builds/ubuntu cosmic main

```
should do it. Note the space before cosmic and that it doesn't say main 3 times.

---

