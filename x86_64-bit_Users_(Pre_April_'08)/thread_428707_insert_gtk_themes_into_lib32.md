---
title: "insert gtk themes into lib32"
date: 2007-04-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by cmost on 2007-04-30
Does anyone know how to add 32bit theme engines to /usr/lib32.  I can't install them from Synaptic since the repos are for amd64.  Some of my GTK 2+ themes require specific theme engines.  When I install one of these engines manually or from Synaptic, if the corresponding 32 bit engine isn't present in /usr/lib32 then some 32 bit apps (like VMware) appear with a really ugly default theme.  I know it's a minor thing but it drives me nuts.  I'd ideally like to have a corresponding 32 bit theme engine to match my 64 bit engines so that all my applications show up properly.  Thanks for the help!

---

### Post by Kilz on 2007-04-30
> **cmost said:**
> Does anyone know how to add 32bit theme engines to /usr/lib32.  I can't install them from Synaptic since the repos are for amd64.  Some of my GTK 2+ themes require specific theme engines.  When I install one of these engines manually or from Synaptic, if the corresponding 32 bit engine isn't present in /usr/lib32 then some 32 bit apps (like VMware) appear with a really ugly default theme.  I know it's a minor thing but it drives me nuts.  I'd ideally like to have a corresponding 32 bit theme engine to match my 64 bit engines so that all my applications show up properly.  Thanks for the help!

You would have to go to the [package site]("http://packages.ubuntu.com/"), download the i386 packages, extract them with ```
sudo dpkg -x packagename.deb
``` Replacing packagename with the deb's name. Then manualy copy the files in the /usr/lib directory extracted from the package to /usr/lib32 in your file system. You would have to do the same thing with any dependencies.

---

### Post by cmost on 2007-04-30
Thanks!  I'll give that a try!

---

### Post by chrisccoulson on 2007-05-01
I had to do this to get some of my themes to work when I upgraded to Feisty. I literally just extracted the contents of the i386 debs and copied the libraries to /usr/lib32/gtk-2.0/2.10.0/engines.

---

### Post by fakie_flip on 2007-06-21
That did not work for me. Are you able to get this theme working properly?

[http://gnome-look.org/content/show.php/Nimbus+%28Ubuntu+and+Debian%29?content=54755](http://gnome-look.org/content/show.php/Nimbus+%28Ubuntu+and+Debian%29?content=54755)

---

### Post by Kilz on 2007-06-22
> **fakie_flip said:**
> That did not work for me. Are you able to get this theme working properly?

[http://gnome-look.org/content/show.php/Nimbus+%28Ubuntu+and+Debian%29?content=54755](http://gnome-look.org/content/show.php/Nimbus+%28Ubuntu+and+Debian%29?content=54755)

The problem the orignal poster had was that 32bit applications looked bad. So they wanted to install a 32bit theme engine for those applications. Not use a 32bit engine for the 64bit install, that wont work.
Why not either 
a. Compile it yourself for 64bit
b. Write the person who created it and ask them for a 64bit version.

---

### Post by fakie_flip on 2007-06-25
> **Kilz said:**
> The problem the orignal poster had was that 32bit applications looked bad. So they wanted to install a 32bit theme engine for those applications. Not use a 32bit engine for the 64bit install, that wont work.
Why not either 
a. Compile it yourself for 64bit
b. Write the person who created it and ask them for a 64bit version.

I want to compile it but I can't find the source code for it. I only found a gentoo ebuild :(

---

### Post by fakie_flip on 2007-06-26
Okay, I found the source code but it seems impossible. I'm using checkinstall with no luck.

make[3]: *** [install-engineLTLIBRARIES] Error 1
make[3]: Leaving directory `/home/chris/Desktop/nimbus-0.0.6.orig/gtk-engine'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/home/chris/Desktop/nimbus-0.0.6.orig/gtk-engine'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/chris/Desktop/nimbus-0.0.6.orig/gtk-engine'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

---

### Post by fakie_flip on 2007-06-26
I am getting lots of errors about intltool even though I have it installed.

```
config.status: executing intltool commands
./config.status: line 1191: ./intltool-extract.in: No such file or directory
mv: cannot stat `intltool-extract.out': No such file or directory
chmod: cannot access `intltool-extract': No such file or directory
chmod: cannot access `intltool-extract': No such file or directory
./config.status: line 1191: ./intltool-merge.in: No such file or directory
mv: cannot stat `intltool-merge.out': No such file or directory
chmod: cannot access `intltool-merge': No such file or directory
chmod: cannot access `intltool-merge': No such file or directory
./config.status: line 1191: ./intltool-update.in: No such file or directory
mv: cannot stat `intltool-update.out': No such file or directory
chmod: cannot access `intltool-update': No such file or directory
chmod: cannot access `intltool-update': No such file or directory
config.status: executing default-1 commands
config.status: executing po/stamp-it commands
```

```
[email]chris@ubuntu:~/Desktop/nimbus-0.0.6.orig[/email]$ dpkg -l | grep intltool
ii  intltool                               0.35.5-0ubuntu2                        Utility scripts for internationalizing XML
ii  intltool-debian                        0.35.0+20060710.1                      Help i18n of RFC822 compliant config files
[email]chris@ubuntu:~/Desktop/nimbus-0.0.6.orig[/email]$ which intltool-update 
/usr/bin/intltool-update
[email]chris@ubuntu:~/Desktop/nimbus-0.0.6.orig[/email]$ which intltool-merge  
/usr/bin/intltool-merge
[email]chris@ubuntu:~/Desktop/nimbus-0.0.6.orig[/email]$
```

---

### Post by fakie_flip on 2007-06-26
The source is here. Are you able to get it compiled?

[http://www.youmustbejoking.demon.co.uk/progs.sid.html#gtk2-engines-nimbus](http://www.youmustbejoking.demon.co.uk/progs.sid.html#gtk2-engines-nimbus)

---

