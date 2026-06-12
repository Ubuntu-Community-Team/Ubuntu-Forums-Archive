---
title: "Installing Simplify Media error"
date: 2008-11-03
forum: x86 64-bit Users
---

### Post by suzypeppercorn on 2008-11-03
I am trying to install simplify media on the new 64 bit 8.10. I had it installed on a 32 bit 8.04 but i am having no luck compiling on this system.

Everytime i run the installer i get this error.

```
./SimplifyMedia: error while loading shared libraries: libdns_sd.so.1: cannot open shared object file: No such file or directory

```

i have tried looking up this error on google and in the package manager and i have had no luck. does anyone know what this means. am i missing a package?

any help? thanks

---

### Post by suzypeppercorn on 2008-11-04
does anyone even know what libdns_sd.so.1 is? i cant find out anything about it?

---

### Post by Yellow Pasque on 2008-11-04
```
sudo apt-get install libavahi-compat-libdnssd-dev
```

---

### Post by suzypeppercorn on 2008-11-05
i installed that and restarted and when i try to compile i still get the same error.

Is there any other packages that might be worth a try?

---

### Post by mattwynne on 2008-11-06
getlibs fixed it for me.

See this thread here:
[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

Basically you install getlibs by downloading and running the .deb package, then run getlibs ./SimplifyMedia once to fetch all the libraries you need.

---

### Post by suzypeppercorn on 2008-11-06
Thanks for the help. That worked for me. I never knew about this and this will really help when compiling programs.

Thanks

---

### Post by fizyxnrd on 2009-03-06
Sorry to resurrect a very old thread, but I've got a problem with the same program/configuration.  I'm running Simplify Media on 8.10 AMD x64.  I have installed simplify media on three other machines (all Windows) and they all talk to each other with no problem.
After I installed, Simplify Media started up just fine, but stopped with the message "Updating statistics...".  Twice it actually showed the other devices that I have logged in, but it was unable to connect to them.  I've made sure that all my windows firewalls allow Simplify Media.  Is there some blocking in Intrepid that I don't know about, or some alternate port that needs to be unblocked on the windows side of things?

Thanks

---

