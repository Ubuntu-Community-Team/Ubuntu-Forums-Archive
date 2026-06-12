---
title: "cant install gambas"
date: 2008-08-12
forum: x86 64-bit Users
---

### Post by Existance0 on 2008-08-12
> gambas2:
 Depends: gambas2-gb-compress-bzlib2 (>=1.9.49-1) but it is not installable
 Depends: gambas2-gb-compress-zlib (>=1.9.49-1) but it is not installable
 Depends: gambas2-gb-crypt (>=1.9.49-1) but it is not installable
 Depends: gambas2-gb-db-firebird  but it is not installable
 Depends: gambas2-gb-db-mysql (>=1.9.49-1) but it is not installable
 Depends: gambas2-gb-db-postgresql (>=1.9.49-1) but it is not installable
 Depends: gambas2-gb-db-odbc (>=1.9.49-1) but it is not installable
 Depends: gambas2-gb-db-sqlite (>=1.9.49-1) but it is not installable or
 	gambas2-gb-db-sqlite2 (>=1.9.49-1) but it is not installable
 Depends: gambas2-gb-form (>=1.9.49-1) but it is not installable
 Depends: gambas2-gb-form-mdi (>=1.9.49-1) but it is not installable
 Depends: gambas2-gb-gtk (>=1.9.49-1) but it is not installable
 Depends: gambas2-gb-gtk-svg  but it is not installable
 Depends: gambas2-gb-image (>=1.9.49-1) but it is not installable
 Depends: gambas2-gb-info (>=1.9.49-1) but it is not installable
 Depends: gambas2-gb-ldap (>=1.9.49-1) but it is not installable
 Depends: gambas2-gb-net-curl (>=1.9.49-1) but it is not installable
 Depends: gambas2-gb-net-smtp (>=1.9.49-1) but it is not installable
 Depends: gambas2-gb-opengl (>=1.9.49-1) but it is not installable
 Depends: gambas2-gb-pcre (>=1.9.49-1) but it is not installable
 Depends: gambas2-gb-pdf (>=1.9.49-1) but it is not installable
 Depends: gambas2-gb-qt-ext (>=1.9.49-1) but it is not installable
 Depends: gambas2-gb-qt-kde-html (>=1.9.49-1) but it is not installable
 Depends: gambas2-gb-qt-opengl  but it is not installable
 Depends: gambas2-gb-sdl (>=1.9.49-1) but it is not installable
 Depends: gambas2-gb-settings (>=1.9.49-1) but it is not installable
 Depends: gambas2-gb-vb  but it is not installable
 Depends: gambas2-gb-v4l (>=1.9.49-1) but it is not installable
 Depends: gambas2-gb-web  but it is not installable
 Depends: gambas2-gb-xml (>=1.9.49-1) but it is not installable
 Depends: gambas2-ide (>=1.9.49-1) but it is not installable



I found some posts that there is a 64 bit package out there but all the links were dead or in a different language :\.

---

### Post by RollieMe on 2008-09-12
I have the same issue.

---

### Post by Kilz on 2008-09-12
gambas is in the universe repository. First [read here]("http://www.psychocats.net/ubuntu/sources") on how to make sure that repository is enabled, and add it if it isnt. [Then here is a guide on how to use Synaptic]("http://www.psychocats.net/ubuntu/installingsoftware#synaptic") to install applications in the repository.

---

### Post by kalaharix on 2008-09-22
Hi,

I have written a short Gambas tutorial including installation using the repository as above. It is at kalaharix.wordpress.com.

I think Gambas is ABSOLUTELY brilliant but (for me) the documentation make it a long learning curve.

rgds

---

### Post by NE Key on 2008-09-26
Thanks for that, I was stuck with version 2.0 but have now jumped to 2.8 using your method. 

I have become a fan of Gambas but the documentation is a bit light.

Have you found these sources ?

[http://gambasdoc.org/help/lang](http://gambasdoc.org/help/lang)
[http://forum.stormweb.no/index.php](http://forum.stormweb.no/index.php)

---

### Post by -kg- on 2008-11-30
I was having the same issue upon finding this thread.  I followed all the instructions (I really think I had all this accomplished) and found the same problem.  Upon attempting to install Gambas from Synaptic:

> gambas2:
 Depends: gambas2-gb-compress-bzlib2 (>=1.9.49-1) but it is not installable
 Depends: gambas2-gb-compress-zlib (>=1.9.49-1) but it is not installable
 Depends: gambas2-gb-crypt (>=1.9.49-1) but it is not installable
 Depends: gambas2-gb-db-firebird  but it is not installable
 Depends: gambas2-gb-db-mysql (>=1.9.49-1) but it is not installable
 Depends: gambas2-gb-db-postgresql (>=1.9.49-1) but it is not installable
 Depends: gambas2-gb-db-odbc (>=1.9.49-1) but it is not installable
 Depends: gambas2-gb-db-sqlite (>=1.9.49-1) but it is not installable or
 	gambas2-gb-db-sqlite2 (>=1.9.49-1) but it is not installable
 Depends: gambas2-gb-form (>=1.9.49-1) but it is not installable
 Depends: gambas2-gb-form-mdi (>=1.9.49-1) but it is not installable
 Depends: gambas2-gb-gtk (>=1.9.49-1) but it is not installable
 Depends: gambas2-gb-gtk-svg  but it is not installable
 Depends: gambas2-gb-image (>=1.9.49-1) but it is not installable
 Depends: gambas2-gb-info (>=1.9.49-1) but it is not installable
 Depends: gambas2-gb-ldap (>=1.9.49-1) but it is not installable
 Depends: gambas2-gb-net-curl (>=1.9.49-1) but it is not installable
 Depends: gambas2-gb-net-smtp (>=1.9.49-1) but it is not installable
 Depends: gambas2-gb-opengl (>=1.9.49-1) but it is not installable
 Depends: gambas2-gb-pcre (>=1.9.49-1) but it is not installable
 Depends: gambas2-gb-pdf (>=1.9.49-1) but it is not installable
 Depends: gambas2-gb-qt-ext (>=1.9.49-1) but it is not installable
 Depends: gambas2-gb-qt-kde-html (>=1.9.49-1) but it is not installable
 Depends: gambas2-gb-qt-opengl  but it is not installable
 Depends: gambas2-gb-sdl (>=1.9.49-1) but it is not installable
 Depends: gambas2-gb-settings (>=1.9.49-1) but it is not installable
 Depends: gambas2-gb-vb  but it is not installable
 Depends: gambas2-gb-v4l (>=1.9.49-1) but it is not installable
 Depends: gambas2-gb-web  but it is not installable
 Depends: gambas2-gb-xml (>=1.9.49-1) but it is not installable
 Depends: gambas2-ide (>=1.9.49-1) but it is not installable


I don't understand what is going on here, as much as I've studied over the last several weeks.  Obviously the rest of you are using Gambas on 64 Bit Architectures (right?) and I already have Gambas installed on my 32-bit duo-core laptop, but I can't seem to get it to install on my AMD64 desktop I assume because of the above uninstallable dependencies.

One thing I've noticed; now that I performed the above operations, Synaptic no longer asks for my password upon launch (I haven't tried installing anything yet, except for Gambas).  It always used to before.  Does this mean anything?

P.S. - I already have Anjuta successfully installed.  I'm learning C and C++ first until I can get Gambas installed.

---

### Post by SteveDee on 2008-12-03
> **kalaharix said:**
> Hi,

I have written a short Gambas tutorial including installation using the repository as above. It is at kalaharix.wordpress.com.

I think Gambas is ABSOLUTELY brilliant but (for me) the documentation make it a long learning curve.

rgds

Great tutorial.

I was wondering what the plain "Graphical Application" type referred to.

---

### Post by chongzi35 on 2008-12-03
High temperature **[cast steel valves](http://www.valvesupplier.net/cast-steel-gate-valves.htm)** are designed and manufactured to provide reliable shutoff and smooth operation under a high temperature environment. The specified bolt torque is maintained during valve assembly, using specialized torque limiting equipment, to prevent valves from leaking between the valve body and bonnet and providing reliable long term operation once the [cast steel valve]("http://www.valvesupplier.net/cast-steel-gate-valves.htm") is put into service.

---

### Post by kalaharix on 2008-12-05
thanks!

As I understand it, Graphical Application type will automatically choose the toolkit relevent to your Linux installation (typically GTK for Gnome and QT for KDE). I think the idea is that it makes for more flexiblity when moving an installation package from one environment to another.

I have read of users on the forum who distrust QT under Gnome though I have never had a problem.

Gambas under GTK has (at least) one problem in that it cannot use the printer commands. Linux is so flexible that this is not insurmountable and judicious use of shell commands can be used to work around the problem.

I remain a great fan of Gambas for my kind of data programming. Apart from the language itself, the IDE is just brilliant.

With regard to the other installation problems in the thread, I must admit that I have never used 64bit Ubuntu on the one AMD64 box I have. I have always stuck to the i386 Ubuntu on the AMD64 machine. Works fine for me but then I never was a speed freak.

---

