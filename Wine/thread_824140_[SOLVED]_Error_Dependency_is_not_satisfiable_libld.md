---
title: "[SOLVED] Error: Dependency is not satisfiable: libldap2"
date: 2008-06-09
forum: Wine
---

### Post by S3loth on 2008-06-09
Trying to install Wine 0.9.52. It gives me this error if I try to install anything under Wine 0.9.60, but I need the others to play Jedi Knight. Anybody know what the problem with it is?

---

### Post by Stargazer989 on 2008-06-10
i get this same error. i haven't found anything so far :(

---

### Post by aspicNOR on 2008-06-11
Yo!

I got the same error trying to install a earlier version of Wine (0.45)

I found this: [http://packages.ubuntu.com/gutsy/i386/libldap2/download](http://packages.ubuntu.com/gutsy/i386/libldap2/download)

Installed manual (by downloading and letting synaptic handle the rest), and then I got to install Wine :)

---

### Post by Burger on 2009-01-28
Well, as for me it didnt help. libldap2_2.1.30-13.4_i386.deb from [http://packages.ubuntu.com/gutsy/i386/libldap2/download](http://packages.ubuntu.com/gutsy/i386/libldap2/download) requested libgnutls13_1.6.3-1ubuntu0.3_i386.deb , and the last asked for libopencdk8_0.5.13-2_i386.deb.
The libgnutils and libopencdk were insalled, but while installation of the libdap2 it said that it conflicts with libdap-2.4-2 and cannot install libldap2_2.1.30-13.4_i386.deb.
What to do?

---

### Post by jmail524 on 2009-02-01
I am having the same problem.  I am running Ubuntu 8.10 and trying to install WINE 0.9.54.  I managed to download and manually install libopencdk8, libgnutls13 and libdap2.  But when I try to install WINE it still complains about the libdap2 dependency not being satisfied.

I can install WINE 1.0.1 without any problems. (Except none of my Windows programs run under anything newer than 0.9.54)

Any other thoughts?

Thanks.
Brian

---

### Post by marcelo.m87 on 2009-06-15
man install the package with the command 
sudo dpkg --ignore-depends=libldap2 -i wine-version.deb
works to me!
Glad to help!
By!

---

### Post by CharlieBros on 2009-07-23
Sorry, i am new in this forum but well I NEED HELP!
i am install perfectly wine 0.9.52 for this comand
sudo dpkg --ignore-depends=libldap2 -i wine-version.deb
but the wine configuration is not  run!! HELP

---

