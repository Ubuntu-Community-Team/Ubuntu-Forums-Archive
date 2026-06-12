---
title: "Problems with Komodo on acer Ferrari"
date: 2007-05-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by lolmc on 2007-05-27
I'm trying to run Komodo 1.3 on Feisty but get the following message in the console when i run it:

/opt/Komodo-3.5/lib/mozilla/komodo-bin: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory

I used to run it fine on Mandriva 2006 and 2007 but since switching to Ubuntu I cannot get past this error.I have searched in vain on these forums for a previous answer so have posted this new request.
Can anyone help with this?
BTW - the lib it is asking for is actually in stalled - I checked with slocate:

lol@acer:~$ slocate libgtk-x11-2.0.so.0
/usr/lib/libgtk-x11-2.0.so.0.1000.11
/usr/lib/libgtk-x11-2.0.so.0

Hope someone can help
lolmc

---

### Post by david_2001 on 2007-05-27
I don't know Komodo but suspect that you are trying to run a 32-bit application on 64-bit Ubuntu.  If that's correct then you will need to install ia32-libs-gtk, which will drag in the basic ia-32libs package as well.  You may also need some of the other lib32 packages but try the minimum first.

---

