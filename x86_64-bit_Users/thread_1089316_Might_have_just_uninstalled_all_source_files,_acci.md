---
title: "Might have just uninstalled all source files, accidentally?"
date: 2009-03-07
forum: x86 64-bit Users
---

### Post by theromanone on 2009-03-07
** installed sudo apt-get install ia32-libs libc6-i386 libc6-dev-i386 lib32gcc1

In the process of trying to get a 32-bit program working for my phone, I thought I could just remove it when I decided to try a different route, so I did the "sudo apt-get remove ia32-libs libc6-i386 libc6-dev-i386 lib32gcc1" and in the process uninstalled wicd, skype and who knows what else.

What kind of damage did I just do, and how can I repair it? Thanks!

---

### Post by x33a on 2009-03-07
you'll have to see what was removed, and if it is important, you can install it like:

sudo aptitude install wicd skype etc...

---

### Post by theromanone on 2009-03-07
Ok, that's actually a good idea since the libraries that got deleted will probably be installed when I install something that got removed, such as WINE? I'll try that.

Btw, here's a terminal message I received when trying to install that phone program this time:

/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.3.2/libgcc.a when searching for -lgcc

Not sure if those libgcc may have been something I deleted?

Here's the terminal window when I origninally made my mistake:

julian@julian:~$ sudo apt-get remove ia32-libs libc6-i386 libc6-dev-i386 lib32gcc1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libmime-types-perl libnet-ssleay-perl libio-stringy-perl wine-gecko
  ttf-liberation libossp-uuid-perl libcrypt-ssleay-perl libmime-tools-perl
  xdotool libfcgi-perl gdesklets-data libnet-google-perl python-soappy
  libsoap-lite-perl python-fpconst nullmailer hddtemp libwww-search-perl
  libemail-date-format-perl libuser-perl winbind libjcode-pm-perl
  libconvert-binhex-perl libio-socket-ssl-perl libossp-uuid15
  libmime-lite-perl
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  flashplugin-nonfree gcc-4.3-multilib gcc-multilib ia32-libs lib32asound2
  lib32gcc1 lib32gomp1 lib32ncurses5 lib32nss-mdns lib32stdc++6 lib32z1
  libc6-dev-i386 libc6-i386 nspluginwrapper skype wine zsnes
0 upgraded, 0 newly installed, 17 to remove and 1 not upgraded.
After this operation, 216MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 127430 files and directories currently installed.)
Removing flashplugin-nonfree ...
Removing gcc-multilib ...
Removing gcc-4.3-multilib ...
Removing skype ...
Removing wine ...
Removing zsnes ...
Removing nspluginwrapper ...
dpkg - warning: while removing nspluginwrapper, directory `/usr/lib/firefox/plugins' not empty so not removed.
Removing ia32-libs ...
Removing lib32asound2 ...
Removing lib32stdc++6 ...
Removing lib32gcc1 ...
Removing lib32gomp1 ...
Removing lib32ncurses5 ...
Removing lib32nss-mdns ...
Removing lib32z1 ...
Removing libc6-dev-i386 ...
Removing libc6-i386 ...
Processing triggers for man-db ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Processing triggers for menu ...
Processing triggers for doc-base ...
camProcessing 1 removed doc-base file(s)...
Registering documents with scrollkeeper...

---

### Post by x33a on 2009-03-07
i think you should try re-installing these> **theromanone said:**
> flashplugin-nonfree gcc-4.3-multilib gcc-multilib ia32-libs lib32asound2
  lib32gcc1 lib32gomp1 lib32ncurses5 lib32nss-mdns lib32stdc++6 lib32z1
  libc6-dev-i386 libc6-i386 nspluginwrapper skype wine zsnes


---

### Post by theromanone on 2009-03-07
I'm may just repartition my drive and reinstall ubuntu. all my files that I ever use are on  different partition anyway.

I reinstalled the files that I removed (which I'm pretty sure replaced the original 64 bit libraries with 32 bit, messing everything up).

I reinstalled each of the programs as you suggested, and now the error went from:
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.3.2/libgcc.a when searching for -lgcc

to:


/usr/bin/ld: i386: x86-64 architecture of input file `nbhextract.o' is incompatible with i386 output
/usr/bin/ld: i386: x86-64 architecture of input file `utils.o' is incompatible with i386 output
/usr/bin/ld: i386: x86-64 architecture of input file `io.o' is incompatible with i386 output
/usr/bin/ld: i386: x86-64 architecture of input file `crc32.o' is incompatible with i386 output
/usr/bin/ld: i386: x86-64 architecture of input file `flasher.o' is incompatible with i386 output
/usr/bin/ld: i386: x86-64 architecture of input file `info.o' is incompatible with i386 output
/usr/bin/ld: i386: x86-64 architecture of input file `prompt.o' is incompatible with i386 output
/usr/bin/ld: i386: x86-64 architecture of input file `nbh.o' is incompatible with i386 output
/usr/bin/ld: i386: x86-64 architecture of input file `main.o' is incompatible with i386 output

---

### Post by x33a on 2009-03-07
are you trying to compile that program?

and yes, from the looks of it, you have 32-bit/64-bit incompatibility.

i don't know if re-installation is the last resort though. try searching for a solution first.

---

