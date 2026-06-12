---
title: "New to Ubuntu - Need help installing  LMC Movie Catalog!"
date: 2007-09-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by daws0n on 2007-09-20
I have used Ant Movie Catalog for years, and while it emulates well using Wine it's a little sluggish... I'd much prefer to use the Linux port LMC, but I'm having trouble installing it. The site includes an 1385 deb, but since I'm on 64bit Ubuntu thats no good. I've downloaded the source, and tried to compile it with ./configure but I get the following error message -

checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether ln -s works... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking dependency style of gcc... none
checking for perl... perl
checking for perl version greater than or equal to 5.8.4... ok
checking for perl module LWP::UserAgent... ok
checking for perl module URI::Escape... ok
checking for perl module POSIX... ok
checking for a Python interpreter with version >= 2.3.4... python
checking for python... /usr/bin/python
checking for python version... 2.5
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.5/site-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.5/site-packages
checking for Python include path... /usr/include/python2.5
checking for Python library path... /usr/lib/python2.5/config
checking python extra libraries... 
checking python module: qt... yes
checking python module: stringtemplate... no
configure: error: failed to find required module stringtemplate

Does anyone know how to fix this or where to download the stringtemplate module?
Thanks!
Dawson

---

### Post by daws0n on 2007-09-20
Ok, I've done some searching and found someone with a similar problem and have insalled all the packages as advised.

[http://ubuntuforums.org/showthread.php?t=346381](http://ubuntuforums.org/showthread.php?t=346381)

Still no luck, I'm well and truly stumped :(

---

### Post by Kilz on 2007-09-20
looks like you need some python dev package. But why isnt the 32bit deb any good to you. If you just need the application to work and are not performance isnt an issue. why not force install it. [Here is a guide to installing 32bit application]("http://tghc.org/32apps.php")s.

---

### Post by daws0n on 2007-09-21
Thanks for the tip, have tried out the install force architecture with in the terminal, but I get another missing package error. Trouble is, this package has been updated to a new one (which i've already installed) so I cannot install the one it requires without a conflict...

It pains me to say, but so far Ubuntu has been a major pain to get working... I found some great tools such as automatix2 and usb adsl manager that got me up and running in no time but for a lot of other things it's been tough.  It seems a great alternative for non demanding users who just want net/word processing but I've had a hard time adjusting to the permissions and  installations, and the fact that a lot of the programs I install don't even enter the main menu. And as far as ati TV-Out goes setting up the output geometry and output via a command line is tedious!

I'll keep it dual booted for a little while longer, but I can see me sticking to Windows XP for a long time yet.

---

