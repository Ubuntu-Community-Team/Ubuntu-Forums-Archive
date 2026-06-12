---
title: "trubble installing"
date: 2008-07-03
forum: Wine
---

### Post by carrarin on 2008-07-03
carrarin@ubuntu:~/Programs/wine-1.0$ make install
bash: make: command not found
carrarin@ubuntu:~/Programs/wine-1.0$ ./tools/wineinstall
Wine Installer v1.0

Running configure...

checking build system type... i686-pc-linux-gnuoldld
checking host system type... i686-pc-linux-gnuoldld
checking whether make sets $(MAKE)... no
checking for gcc... no
checking for cc... no
checking for cl.exe... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

Configure failed, aborting install.

how do i fix., by the way im new to the forums. 
so ill just sit back and :popcorn: any help would be appreciated

---

### Post by cogadh on 2008-07-03
Use the precompiled Ubuntu package, instead of compiling it yourself. To get Wine 1.0, you just need to [enable the Ubuntu backports repository](https://help.ubuntu.com/community/Repositories/Ubuntu) or if you want to use the latest unstable version of Wine, add the [WineHQ repository](http://www.winehq.org/site/download-deb).

If you need to compile it yourself for some reason, then first you need to install the build-essentials package, plus any dependencies for Wine:
```
sudo apt-get install build-essential
sudo apt-get build-dep wine
```
Then you should be able to run the usual make commands.

---

