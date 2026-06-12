---
title: "Problems using Ubuntu Software Center"
date: 2009-11-08
forum: x86 64-bit Users
---

### Post by minnewt on 2009-11-08
(keep in mind I'm a major newbie to this.. running Karmic Koala on a 64bit Acer)

Hey guys, I'm having a lot of issues with Ubuntu Software Center. Anytime I try to install anything other than updates.. it will stop at halfway and give me this error:

```
installArchives() failed: (Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 129242 files and directories currently installed.)
Removing amarok ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
/sbin/ldconfig.real: File /usr/lib/libQtCore.so.4.5 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/liblzma.so.0 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libQtCLucene.so.4.5.2 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libQtCLucene.so.4 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libQtCore.so.4 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libQtCore.so.4.5.2 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/liblzma.so.0.0.0 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libQtCLucene.so.4.5 is empty, not checked.
Setting up liblzma0 (4.999.8beta-0ubuntu2) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing liblzma0 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libqtcore4 (4.5.3really4.5.2-0ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libqtcore4 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libqt4-xml:
 libqt4-xml depends on libqtcore4 (= 4.5.3really4.5.2-0ubuntu1); however:
  Package libqtcore4 is not configured yet.
dpkg: error processing libqt4-xml (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-dbus:
 libqt4-dbus depends on libqt4-xml (= 4.5.3really4.5.2-0ubuntu1); however:
  Package libqt4-xml is not configured yet.
 libqt4-dbus depends on libqtcore4 (= 4.5.3really4.5.2-0ubuntu1); however:
  Package libqtcore4 is not configured yet.
dpkg: error processing libqt4-dbus (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-script:
 libqt4-script depends on libqt4-dbus (= 4.5.3really4.5.No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
2-0ubuntu1); however:
  Package libqt4-dbus is not configured yet.
 libqt4-script depends on libqtcore4 (= 4.5.3really4.5.2-0ubuntu1); however:
  Package libqtcore4 is not configured yet.
dpkg: error processing libqt4-script (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqtgui4:
 libqtgui4 depends on libqtcore4 (= 4.5.3really4.5.2-0ubuntu1); however:
  Package libqtcore4 is not configured yet.
dpkg: error processing libqtgui4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-designer:
 libqt4-designer depends on libqt4-script (= 4.5.3really4.5.2-0ubuntu1); however:
  Package libqt4-script is not configured yet.
 libqt4-designer depends on libqt4-xml (= 4.5.3really4.5.2-0ubuntu1); however:
  Package libqt4-xml is not configured yet.
 libqt4-designer depends on libqtcore4 (= 4.5.3really4.5.2-0ubuntu1); however:
  Package libqtcore4 is not configured yet.
 libqt4-designer depends on libqtgui4 (= 4.5.3really4.5.2-0ubuntu1); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libqt4-designer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-network:
 libqt4-network depends on libqtcore4 (= 4.5.3really4.5.2-0ubuntu1); however:
  Package libqtcore4 is not configured yet.
dpkg: error processing libqt4-network (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-phonon:
 libqt4-phonon depends on libqt4-dbus (= 4.5.3really4.5.2-0ubuntu1); however:
  Package libqt4-dbus is not configured yet.
 libqt4-phonon depends on libqtcore4 (= 4.5.3really4.5.2-0ubuntu1); however:
  Package libqtcore4 is not configured yet.
 libqt4-phonon depends on libqtgui4 (= 4.5.3really4.5.2-0ubuntu1); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libqt4-phonon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-sql:
 libqt4-sql depends on libqtcore4 (= 4.5.3really4.5.2-0ubuntu1); however:
  Package libqtcore4 is not configured yet.
dpkg: error processing libqt4-sql (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-qt3support:
 libqt4-qt3support depends on libqt4-designer (= 4.5.3really4.5.2-0ubuntu1); however:
  Package libqt4-designer is not configured yet.
 libqt4-qt3support depends on libqt4-network (= 4.5.3really4.5.2-0ubuntu1); however:
  Package libqt4-network is not configured yet.
 libqt4-qt3support depends on libqt4-sql (= 4.5.3really4.5.2-0ubuntu1); however:
  Package libqt4-sql is not configured yet.
 libqt4-qt3support depends on libqt4-xml (= 4.5.3really4.5.2-0ubuntu1); however:
  Package libqt4-xml is not configured yet.
 libqt4-qt3support depends on libqtcore4 (= 4.5.3really4.5.2-0ubuntu1); however:
  Package libqtcore4 is not configured yet.
 libqt4-qt3support depends on libqtgui4 (= 4.5.3really4.5.2-0ubuntu1); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libqt4-qt3support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-svg:
 libqt4-svg depends on libqtcore4 (= 4.5.3really4.5.2-0ubuntu1); however:
  Package libqtcore4 is not configured yet.
 libqt4-svg depends on libqtgui4 (= 4.5.3really4.5.2-0ubuntu1); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libqt4-svg (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libsoprano4:
 libsoprano4 depends on libqt4-dbus (>= 4.5.1); however:
  Package libqt4-dbus is not configured yet.
 libsoprano4 depends on libqt4-network (>= 4.5.1); however:

```

I've tried doing a bunch of random things, but I know its basically stabbing in the dark... which is how I managed to mess up Linux Mint and which is why I'm now trying Ubuntu.
I've tried doing
sudo dpkg --configure -a
and force install, I've tried updates, using package manager but the same error pops up everytime I try to install a new program.

What to do?

---

### Post by lavinog on 2009-11-08
Have you tried synaptic?

It looks like a dependency issue.
Try reloading the repositories first (the reload button in synaptic)
Then do a update, then try and install your program

---

