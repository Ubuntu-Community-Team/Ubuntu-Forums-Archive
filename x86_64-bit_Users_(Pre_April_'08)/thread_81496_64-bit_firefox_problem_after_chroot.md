---
title: "64-bit firefox problem after chroot"
date: 2005-10-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by Reducer on 2005-10-24
I had a great working 64-bit Breezy system, until I tried the chroot thing to get a 32-bit Firefox working w/ Flash.  Everything ran fine following the excellent how-to I found in these forums, however now when I launch 64-bit Firefox from the terminal by typing 'firefox', I get an error that says "Segmentation Fault" then it kicks me back to the command line.

Running the 32-bit Firefox from chroot works fine.

I tried re-installing Firefox using Synaptic, but no dice.  Any ideas?

Thanks.

---

### Post by wmcbrine on 2005-10-24
Maybe you have some 32-bit plugins installed in your profile? I'm not even sure if that's possible with Firefox, but I know it was with old Mozilla (Seamonkey). Anyway, if you install them globally (in the chroot's /usr/lib/mozilla-firefox/plugins), and remove them from the profile (~/.mozilla/firefox/whatever), you should be OK.

I can't think of any other way for the chroot to mess up the 64-bit version.

---

### Post by Reducer on 2005-10-24
Okay,  I did that, and we're making progress!!  I still seg-faults, but now it gives me an exact error:

```
LoadPlugin: failed to initialize shared library libXt.so [libXt.so: cannot open shared object file: No such file or directory]
LoadPlugin: failed to initialize shared library libXext.so [libXext.so: cannot open shared object file: No such file or directory]
Segmentation fault

```

Thanks for your help so far, how can I fix this?

Update:

I fixed it.  I re-installed firefox using synaptic, then deleted the 'flash' plug-in files in the ~/.mozilla/ directory.  Thanks!

---

