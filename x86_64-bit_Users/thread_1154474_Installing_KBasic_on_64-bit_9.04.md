---
title: "Installing KBasic on 64-bit 9.04"
date: 2009-05-09
forum: x86 64-bit Users
---

### Post by mickie.kext on 2009-05-09
I have trouble installing KBasic on 64-bit ubuntu. I opened thread on the wrong place:

[http://ubuntuforums.org/showthread.php?t=1147150](http://ubuntuforums.org/showthread.php?t=1147150)

So I did not get an answer. I hope that I will be more lucky here :)

---

### Post by pixel :-) on 2009-05-10
your options
32bit

i downloaded [http://www.kbasic.com/kbasic_professional_linux.tar.gz](http://www.kbasic.com/kbasic_professional_linux.tar.gz)
i have ia32-libs installed

with getlibs

[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

he complains

No match for libQtWebKit.so.4
No match for libphonon.so.4
No match for libQtSvg.so.4
No match for libQtSql.so.4

presumably these are the only problems, but you they maybe incompatible vertions, or them selves depending on other stuff

with [http://packages.ubuntu.com/](http://packages.ubuntu.com/)
you can find in what pakages they are contained

they are contained respectively in

libqt4-webkit
libphonon4
libqt4-svg
libqt4-sql

you can install them in your system with
 
/pathToGetlibs/getlibs -p libqt4-webkit libphonon4 libqt4-svg libqt4-sql

:arrow: It will instal them in the corect places (lib32 folders) however, this bypasses apt-get, so uninstalation have to be done by hand :( .

if they are further unmet dependencies, redo the procedure.

a little bit laborious, to avoid having stuff out of the control of apt-get. You can convert the packages by hand, but this is an other topic. checkinstall gives a quick and dirty way to build packages

Windows vertion
under wine you can't read the dialogues. Maybe theres a work aroud for that.

64 bit
You can try to compile it your self, but it's not officially supported

---

