---
title: "v4l-dvb problem installing"
date: 2006-09-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by asgardfleet on 2006-09-04
Hey

I am trying to get by Dvico Fusionhdtv dvb-t dual digital card going. Have followed many step and well I have probably done this before but this time I am having trouble.

Installing v4l-dvb

I am getting this error message:

[COLOR="Blue"]geoff@desktop:~/Downloads/v4l-dvb$ make
make -C /home/geoff/Downloads/v4l-dvb/v4l
make[1]: Entering directory `/home/geoff/Downloads/v4l-dvb/v4l'
Updating/Creating .config
File not found: /lib/modules/2.6.15-26-amd64-generic/build/.config at ./scripts/make_kconfig.pl line 30.
make[1]: *** No rule to make target `.myconfig', needed by `config-compat.h'.  Stop.
make[1]: Leaving directory `/home/geoff/Downloads/v4l-dvb/v4l'
make: *** [all] Error 2[/COLOR]

I have the kernel-headers installed, but they exist in /usr/src and in /lib/modules/2.6.15-26-amd64-generic there is no build directory.

So if anyone has any ideas about how i get my missing build directory, please let me know

Thanks

---

### Post by mulvila on 2007-04-06
I guess you need to have exactly the right kernel headers installed. The package should be linux-headers followed by the output of uname -r command.

In my case I had the linux-headers-2.6.17 package installed but I had to install linux-headers-2.6.17-386. Then the installation worked.

Hope this helps, with a delay.

Marko

---

