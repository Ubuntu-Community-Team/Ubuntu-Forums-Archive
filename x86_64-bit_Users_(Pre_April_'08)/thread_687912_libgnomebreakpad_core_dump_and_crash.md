---
title: "libgnomebreakpad core dump and crash"
date: 2008-02-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by misterfixit on 2008-02-04
This has started to occur after the latest automatic update:

dave@misterfixit:~$ azureus
Looking for and picking a preferred Java runtime
Use environment AZUREUS_JAVA to override
Using Java: /usr/lib/jvm/java-7-icedtea/jre/bin/java
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
Gtk-Message: Failed to load module "gnomebreakpad": libgnomebreakpad.so: cannot open shared object file: No such file or directory
DEBUG::Mon Feb 04 19:26:48 CST 2008  Data Missing /tmp/azupdater_1.8.3.zip
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00002b51a59f9e11, pid=23101, tid=1074792784
#
# Java VM: IcedTea 64-Bit Server VM (1.7.0-b21 mixed mode linux-amd64)
# Problematic frame:
# V  [libjvm.so+0x5c9e11]
#
# An error report file with more information is saved as:
# /home/dave/.azureus/hs_err_pid23101.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
Aborted (core dumped)
dave@misterfixit:~$ 

I've Googled, of course, but the pickings are slim for an answer.

---

