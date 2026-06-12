---
title: "[SOLVED] Gnumeric broken"
date: 2007-08-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by a-musing amazon on 2007-08-27
I've recently had a problem trying to run gnumeric (amd64).

Previously its been working OK. Originally I had installed it with Dapper and I've successfully ungraded through Edgy to Feisty, however a few days ago it stopped working.Nearly everything else, including other part of Gnu-office, such as Abiword, is working OK (FWIW I'm am trying to sync my WM6 phone and can't get SyncCE to work properly).

Anyway, running it in a terminal I get the message:

$ gnumeric
gnumeric: error while loading shared libraries: libgsf-gnome-1.so.113: cannot open shared object file: No such file or directory

Now the problem is that I have the Feisty version running and libgsf-gnome-1.so.113 is the library for the Dapper version. I do have libgsf-gnome-1.so.114. If I add libgsf-gnome-1.so.113 from the archives to /usr/lib/ it then starts asking for another Dapper library libgsf-1.so.113. If I add this it then leads to an internal error in another .so library.

I have tried reinstalling (including a comlete remove and install) all the relevant packages (gnumeric, goffice, libgsf-1-114 and libgsf-gnome-114) and this makes no difference. In case there was a problem with my mirror I have tried more than one.

The gnumeric binary is dated 2007-03-26 19:54, so seem to be the up to date version.

If I download the Feisty sources and run ./configure I get the error message:

"Requested 'libgoffice-0.3 >= 0.3.7' but version of libGOffice is 0.3.5", even though I have the up to date dev package.

So, anyone any suggestions as what the problem might be and/or how I can get gnumeric working again?

Marjorie

---

### Post by michael37 on 2007-08-30
> **a-musing amazon said:**
> I've recently had a problem trying to run gnumeric (amd64).

Previously its been working OK. Originally I had installed it with Dapper and I've successfully ungraded through Edgy to Feisty, however a few days ago it stopped working.Nearly everything else, including other part of Gnu-office, such as Abiword, is working OK (FWIW I'm am trying to sync my WM6 phone and can't get SyncCE to work properly).

Anyway, running it in a terminal I get the message:

$ gnumeric
gnumeric: error while loading shared libraries: libgsf-gnome-1.so.113: cannot open shared object file: No such file or directory

Now the problem is that I have the Feisty version running and libgsf-gnome-1.so.113 is the library for the Dapper version. I do have libgsf-gnome-1.so.114. If I add libgsf-gnome-1.so.113 from the archives to /usr/lib/ it then starts asking for another Dapper library libgsf-1.so.113. If I add this it then leads to an internal error in another .so library.

I have tried reinstalling (including a comlete remove and install) all the relevant packages (gnumeric, goffice, libgsf-1-114 and libgsf-gnome-114) and this makes no difference. In case there was a problem with my mirror I have tried more than one.

The gnumeric binary is dated 2007-03-26 19:54, so seem to be the up to date version.

If I download the Feisty sources and run ./configure I get the error message:

"Requested 'libgoffice-0.3 >= 0.3.7' but version of libGOffice is 0.3.5", even though I have the up to date dev package.

So, anyone any suggestions as what the problem might be and/or how I can get gnumeric working again?

Marjorie

I think you have an old broken lingering 1-113 libgsf library somewhere around.  Run ldd /usr/bin/gnumeric and let's see where it tries to pick it.  

Also, check what libraries you have:
ls -l /usr/lib/libgsf*

---

### Post by a-musing amazon on 2007-08-30
Thanks Michael,

there aren't any stale libgsf-1.so.113 around (its not finding them that is causing the error). However what ldd /usr/bin/gnumeric found was:

  libgoffice-0.so.3 => /usr/local/lib/libgoffice-0.so.3 (0x00002b6f2234c000)
  .....
  libgsf-gnome-1.so.114 => /usr/lib/libgsf-gnome-1.so.114 (0x00002b6f2528c000)
  libgsf-1.so.114 => /usr/lib/libgsf-1.so.114 (0x00002b6f25491000)

The problems is in goffice since I find:

$ ls -l /usr/lib/libgoff*
lrwxrwxrwx 1 root root      21 2007-08-26 16:33 /usr/lib/libgoffice-0.so -> libgoffice-0.so.3.0.7
lrwxrwxrwx 1 root root      21 2007-08-26 16:30 /usr/lib/libgoffice-0.so.3 -> libgoffice-0.so.3.0.7

and 

$ ls -l /usr/local/lib/libgoff*
-rwxr-xr-x 1 root root    2676 2006-12-26 14:35 /usr/local/lib/libgoffice-0.la
lrwxrwxrwx 1 root root      21 2006-12-26 14:35 /usr/local/lib/libgoffice-0.so -> libgoffice-0.so.3.0.5
lrwxrwxrwx 1 root root      21 2006-12-26 14:35 /usr/local/lib/libgoffice-0.so.3 -> libgoffice-0.so.3.0.5

ie. there was a stale version of goffice in /usr/local/lib.

Deleting that and I now have my gnumeric working again :).

best regards,

Marjorie

---

### Post by michael37 on 2007-08-30
Mark this thread SOLVED :biggrin:=D>:biggrin:

---

