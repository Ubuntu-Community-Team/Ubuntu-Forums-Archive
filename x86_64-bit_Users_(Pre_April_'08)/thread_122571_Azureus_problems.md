---
title: "Azureus problems"
date: 2006-01-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by freakzilla on 2006-01-28
Azureus stopped working on my system.  I believe it was because i updated java or something.  I've tried downloading and installling the latest azureus for amd64.  I can get it to run by clicking on it in nautilus but when i run it from >applications>internet or from terminal I get this error:

Starting Azureus...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.5.0_05]
Configuring environment...
Loading Azureus:
java -Xms16m -Xmx128m -cp "/usr/bin/*.jar" -Djava.library.path="/usr/bin" -Dazureus.install.path="/usr/bin" org.gudy.azureus2.ui.swt.Main ''
Exception in thread "main" java.lang.NoClassDefFoundError: org/gudy/azureus2/ui/swt/Main
Azureus TERMINATED.

Please dumb down this explaination for me.  I'm somewhat new to linux.

---

### Post by tokyovigilante on 2006-01-29
Mine too.

I'm using the 64-bit Sun JRE 1.5, with the 64-bit 2.3.0.6 from azureus.sourceforge.net. Was working fine with a pre-Flight 3 daily build, but on dist-upgrade today from that Azureus stopped working with the (similar) error:

```
Starting Azureus...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.5.0_06]
Configuring environment...
Loading Azureus:
java -Xms16m -Xmx128m -cp "/home/ryan/System/Software/azureus/azureus/Azureus2.jar:/home/ryan/System/Software/azureus/azureus/swt.jar" -Djava.library.path="/home/ryan/System/Software/azureus/azureus" -Dazureus.install.path="/home/ryan/System/Software/azureus/azureus" org.gudy.azureus2.ui.swt.Main ''
#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0x00002aaaff6b863d, pid=6543, tid=46912501787360
#
# Java VM: Java HotSpot(TM) 64-Bit Server VM (1.5.0_06-b05 mixed mode)
# Problematic frame:
# C  [libgobject-2.0.so.0+0x2663d]
#
# An error report file with more information is saved as hs_err_pid6543.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
./azureus: line 107:  6543 Aborted                 ${JAVA_PROGRAM_DIR}java -Xms16m -Xmx128m -cp "${CLASSPATH}" -Djava.library.path="${PROGRAM_DIR}" -Dazureus.install.path="${PROGRAM_DIR}" org.gudy.azureus2.ui.swt.Main "$@"
Azureus TERMINATED.

```

I note the error is directed specifically at libgobject-2.0.so.0.

Any ideas? I really don't want to have to go back to a chroot just for Bittorrent.

---

### Post by tokyovigilante on 2006-02-03
After some fiddling I've continued to have no luck running 64 bit Java/Azureus, but did get the 32 bit version running with a minimum of effort without a chroot.

If anyone wants instructions let me know, basically just install the 32-bit sun java package with --force-architecture, then link azureus 32 bit to pango and gtk libs, and use linux32 to run it.

---

### Post by Thruth on 2006-07-24
> **tokyovigilante said:**
> Mine too.

I'm using the 64-bit Sun JRE 1.5, with the 64-bit 2.3.0.6 from azureus.sourceforge.net. Was working fine with a pre-Flight 3 daily build, but on dist-upgrade today from that Azureus stopped working with the (similar) error:
...........
I note the error is directed specifically at libgobject-2.0.so.0.

Any ideas? I really don't want to have to go back to a chroot just for Bittorrent.

Well, there's a known conflict between 2.14.x glib2 and java runtime Environment. So a downgrade to glib2 and related packages is one of the workarounds.

---

