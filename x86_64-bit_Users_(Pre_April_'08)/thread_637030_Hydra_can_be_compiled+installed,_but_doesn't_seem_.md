---
title: "Hydra can be compiled+installed, but doesn't seem to work"
date: 2007-12-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by mrc_001 on 2007-12-10
I just compiled THC Hydra 5.4. It can be assumed that I did everything correctly because I already successfully did it several times on other machines.

**Now I have:**
Linux 2.6.22-14-generic running KDE 3.5.8, CPU: Intel(R)Core2CPUT7400@2.16GHz at 1000 MHz (4322 bogomips), , RAM: 1144/1984MB
Kubuntu 7.10 amd64

**The problem:**
When I type "hydra" inside the command line nothing happens. A new prompt appears immediatly, just if I typed "false". Using different arguments or running hydra as root doesn't change this.
Trying to run xhydra only the GUI appears. I can set the values, but clicking on start generates just those errors:
```

** (xhydra:12430): WARNING **: callbacks.c 529: popen_rw_unbuffered: execv() returned

** (xhydra:12430): WARNING **: /usr/local/bin/hydra

** (xhydra:12430): WARNING **: 127.0.0.1

** (xhydra:12430): WARNING **: cisco

** (xhydra:12430): WARNING **: -l

** (xhydra:12430): WARNING **: yourname

** (xhydra:12430): WARNING **: -p

** (xhydra:12430): WARNING **: yourpass

** (xhydra:12430): WARNING **: -t

** (xhydra:12430): WARNING **: 36

** ERROR **: file callbacks.c: line 544 (popen_re_unbuffered): should not be reached
aborting...
```

Thanks for your responses in advance!

---

### Post by Kilz on 2007-12-10
I for one dont feel comfortable helping someone setup a password cracker.

---

### Post by mrc_001 on 2007-12-10
I'm not that script kiddie who has fun at using nifty tools to damage other's property. I'm rather interested in securing my own machines. I administer a server with several services which could be exploited, so I want to try myself how easy/hard it is to do so. The final purpose is to make my own property better protected against those, who abuse such tools for crime.

---

### Post by cisforcojo on 2007-12-17
Haha if you don't wanna help, then don't. Password crackers aren't JUST for malice. They're really useful in protecting your own system, performing penetration testing, etc. etc. Anyway, I had that same printout printout before but can't remember exactly what I did.

Give me a step by step description of what you did you install hydra.

---

### Post by mrc_001 on 2007-12-17
[LIST=1]
[*]Downloaded Hydra:
$ wget [http://freeworld.thc.org/releases/hydra-5.4-src.tar.gz](http://freeworld.thc.org/releases/hydra-5.4-src.tar.gz)
[*]Extracted archive:
$ tar xzf hydra-5.4-src.tar.gz
[*]Executed configuration script:
$ ./configure
[*]Compile:
$ make
[*]Install:
$ sudo make install
[/LIST]

Just the default procedure as it is described in the INSTALL file. The configuration script definitely succeeded, otherwise I wouldn't have been able to run make. Hence all dependencies are satisfied.

---

### Post by Fusspils on 2007-12-17
Have you found a solution yet?  I have the exact same problem with the exact same set-up.  No info anywhere!

---

### Post by cisforcojo on 2007-12-18
Show me the printout of ./configure
Guarantee your problem is in there.

EDIT: I had it succeed on mine as well when I had that same problem, I'm not questioning that, I think it might be a libssh problem. You need 0.11. I'm not sure I can't remember exactly. That's why I just wanna see your configure.

---

### Post by mrc_001 on 2007-12-18
```

Starting hydra auto configuration ...

Checking for openssl (libssl/ssl.h) ...
                                    ... found
Checking for Postgres (libpq) ...
                              ... found
Checking for SVN (ibsvn_client-1 libapr-0.so libaprutil-0.so) ...
                              ... found
Checking for SAP/R3 (librfc/saprfc.h) ...
                                      ... NOT found, module sapr3 disabled
Get it from http://www.sap.com/solutions/netweaver/linux/eval/index.asp
Checking for libssh (libssh/libssh.h) ...
                                      ... NOT found, module ssh2 disabled
Get it from http://0xbadc0de.be/ - use v0.11!

Hydra will be installed into .../bin of: /usr/local
  (change this by running ./configure --prefix=path)

Writing Makefile.in ...

NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES
=======================================================================
ARM/PalmPilot users: please run ./configure-arm or ./configure-palm respectivly

now type "make"

```

You are right, ssh lib 0.11 is required, but the version of the package in the Ubuntu repository is 0.14 or so.
I still wonder, why whole hydra doesn't work although the script outputs the ssh module as disabled. Shouldn't the rest be working then?

Thanks a lot!

---

### Post by cisforcojo on 2007-12-19
Alright, I don't have it working perfectly either (I get child errors when I run it using a dict file that I KNOW contains the password I'm looking for and a set username) so perhaps you can help ME with that once I get you to that sort of functionality.

The problem with libssh is that the newer versions and 0.11 aren't backwards compatible so you need both.

You can get the 0.11 version here: [http://0xbadc0de.be/libssh/libssh-0.11.tgz](http://0xbadc0de.be/libssh/libssh-0.11.tgz)

```

tar zxvf libssh-0.11.tgz
cd libssh-0.11
./configure --prefix=/usr
make
sudo checkinstall

```

After this, recompile hydra but instead use 'sudo checkinstall' instead of 'sudo make install'
This makes it MUCH easier to remove. Something goes wrong, you can just type: sudo apt-get remove hydra-5.4 and it's gone.

You might run into a problem when running checkinstall, something about digits in the version. When you review the information during checkinstall before you make the .deb, you'll see the version = 'src', change that to 5.4 and you'll have no problems. This being said, before installing with checkinstall, I'd suggest going to your hydra source FIRST and typing 'sudo make uninstall'. If this doesn't work, go to /usr/local and manually remove everything you see for hydra. Like I said, it's messy. 

Hope this helps you (to where I am).

---

