---
title: "More openoffice printing problems"
date: 2005-08-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by aglauser on 2005-08-07
I've tried all of the various methods to try to get openoffice to print (removing the gnome-desktop package, installing OO2 beta via the Evolution Colt script, and manually downlowding and converting rpms), but to no avail.  I did manage to get OOo  1.9.113 to run, but I couldn't save or open documents.  The printer showed up, but nothing printed when I tried.   ](*,)   Edit: I've also tried a 32-bit chroot, but OO won't see the printer that way either.

Now I'm trying to manually install 1.9.122 using alien, but I get this error:

```

Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
        xargs -0 -r -i cp -a {} debian/openofficeorg-base
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dh_gencontrol
dpkg-gencontrol: error: current build architecture amd64 does not appear in package's list (i386)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
find: openofficeorg-base-1.9.122: No such file or directory
``` 

Sadly, I don't have any idea whether or not these errors in the .deb conversion can be fixed or how to go about trying that.  Does anyone with some alien/rpm experience suggest a way to get this base package to convert properly?

---

### Post by rplantz on 2005-09-06
I installed StarOffice, which prints just fine.

Students, teachers, staff, and researchers can download it free from Sun's website.

I like the philosophy of OpenOffice, but I need to print things.

Bob

---

### Post by mlomker on 2005-09-08
[QUOTE=rplantz]I like the philosophy of OpenOffice, but I need to print things.[/QUOTE]

hehe.  I guess I never tried to print anything because I found OO so slow that I didn't want to run it.  Being on KDE, I quickly replaced it with Koffice.

---

