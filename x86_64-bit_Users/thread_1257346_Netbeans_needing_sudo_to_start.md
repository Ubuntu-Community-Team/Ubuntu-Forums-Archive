---
title: "Netbeans needing sudo to start"
date: 2009-09-03
forum: x86 64-bit Users
---

### Post by craig100 on 2009-09-03
Hi,

System: Ubuntu 9.04 x64

I've had all sorts of trouble today with java. Started with the firefox  plugin stopping working. Anyhow, in my attempts to fix that, I managed to remove the JRE and JDK (6_16) which broke my Netbeans 6.7.1 installation.

Managed to get the JRE and JDK back (though not the FF plugin yet), however, have tried many times to re-install Netbeans with PHP version. Everytime now it installs itself in a directory with root only privileges. So I don't get a desktop icon to start it. I can only start it by "sudo netbeans". In Nautilus the netbeans-6.7.1 directory has an orange emblem on it which it didn't used to.

It's been a long day, and I've probably made a schoolboy booboo somewhere, but can anyone suggest how I can get my web development system back, i.e. install NetBeans so I can start it normally?

Any help would be appreciated.

Craig:confused:

---

### Post by craig100 on 2009-09-03
Doing a sudo chown -R <username> /pathtodir/ got it all under my ownership. However, still can't start NetBeans. The spinner spins for 30 seconds then disappears. A log file is generated saying:-

# JRE version: 6.0_16-b01
# Java VM: Java HotSpot(TM) 64-Bit Server VM (14.2-b01 mixed mode linux-amd64 )
# Problematic frame:
# C  [libc.so.6+0x3158f]  catgets+0x1f

I believe it's a Compiz/Java issue. There's some talk on some threads of adding the line: export AWT_TOOLKIT=MToolkit somewhere, but I don't know where.

Has anyone had and fixed this problem?

Cheers,

Craig

---

### Post by Barafu Albino Cheetah on 2009-09-03
I have installed 6.7.1. yesterday, on 64 bit machine with compiz. Do you install netbeans from repo? It is a right way, of cause, but installing downloaded version works absolutely fine. Just install it with sudo, into /opt/netbeans or similar. 
By the way, 6/8 M1 works great too.

---

### Post by Yellow Pasque on 2009-09-04
> export AWT_TOOLKIT=MToolkit 
Do this in a terminal before you try to start netbeans;
```
export AWT_TOOLKIT=MToolkit 
```

---

### Post by craig100 on 2009-09-04
Did that in terminal then started netbeans in terminal and got this:-

#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00007f1381fcb58f, pid=17071, tid=139720784980304
#
# JRE version: 6.0_16-b01
# Java VM: Java HotSpot(TM) 64-Bit Server VM (14.2-b01 mixed mode linux-amd64 )
# Problematic frame:
# C  [libc.so.6+0x3158f]  catgets+0x1f
#
# An error report file with more information is saved as:
# /home/craig/hs_err_pid17071.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#
/home/craig/netbeans-6.7.1/bin/../platform10/lib/nbexec: line 518: 17071 Aborted                 "/home/craig/JavaJDK/jdk1.6.0_16/bin/java" -Djdk.home="/home/craig/JavaJDK/jdk1.6.0_16" -classpath "/home/craig/netbeans-6.7.1/platform10/lib/boot.jar:/home/craig/netbeans-6.7.1/platform10/lib/org-openide-modules.jar:/home/craig/netbeans-6.7.1/platform10/lib/org-openide-util.jar:/home/craig/netbeans-6.7.1/platform10/lib/locale/boot_ja.jar:/home/craig/netbeans-6.7.1/platform10/lib/locale/boot_pt_BR.jar:/home/craig/netbeans-6.7.1/platform10/lib/locale/boot_zh_CN.jar:/home/craig/netbeans-6.7.1/platform10/lib/locale/org-openide-modules_ja.jar:/home/craig/netbeans-6.7.1/platform10/lib/locale/org-openide-modules_pt_BR.jar:/home/craig/netbeans-6.7.1/platform10/lib/locale/org-openide-modules_zh_CN.jar:/home/craig/netbeans-6.7.1/platform10/lib/locale/org-openide-util_ja.jar:/home/craig/netbeans-6.7.1/platform10/lib/locale/org-openide-util_pt_BR.jar:/home/craig/netbeans-6.7.1/platform10/lib/locale/org-openide-util_zh_CN.jar:/home/craig/JavaJDK/jdk1.6.0_16/lib/dt.jar:/home/craig/JavaJDK/jdk1.6.0_16/lib/tools.jar" -Dnetbeans.system_http_proxy="DIRECT" -Dnetbeans.system_http_non_proxy_hosts="" -Dnetbeans.dirs="/home/craig/netbeans-6.7.1/nb6.7:/home/craig/netbeans-6.7.1/bin/../ergonomics1:/home/craig/netbeans-6.7.1/ide11:/home/craig/netbeans-6.7.1/bin/../java2:/home/craig/netbeans-6.7.1/bin/../xml2:/home/craig/netbeans-6.7.1/bin/../apisupport1:/home/craig/netbeans-6.7.1/webcommon1:/home/craig/netbeans-6.7.1/websvccommon1:/home/craig/netbeans-6.7.1/bin/../enterprise5:/home/craig/netbeans-6.7.1/bin/../mobility8:/home/craig/netbeans-6.7.1/bin/../profiler3:/home/craig/netbeans-6.7.1/bin/../ruby2:/home/craig/netbeans-6.7.1/bin/../python1:/home/craig/netbeans-6.7.1/php1:/home/craig/netbeans-6.7.1/bin/../visualweb2:/home/craig/netbeans-6.7.1/bin/../soa2:/home/craig/netbeans-6.7.1/bin/../identity2:/home/craig/netbeans-6.7.1/bin/../uml6:/home/craig/netbeans-6.7.1/bin/../harness:/home/craig/netbeans-6.7.1/bin/../cnd2:/home/craig/netbeans-6.7.1/bin/../dlight1:/home/craig/netbeans-6.7.1/bin/../groovy1:/home/craig/netbeans-6.7.1/bin/../extra:/home/craig/netbeans-6.7.1/bin/../javafx2:" -Dnetbeans.home="/home/craig/netbeans-6.7.1/platform10" '-Dnetbeans.importclass=org.netbeans.upgrade.AutoUpgrade' '-Dnetbeans.accept_license_class=org.netbeans.license.AcceptLicense' '-Xmx512m' '-client' '-Xss2m' '-Xms32m' '-XX:PermSize=32m' '-XX:MaxPermSize=200m' '-Xverify:none' '-Dapple.laf.useScreenMenuBar=true' '-Dsun.java2d.noddraw=true' -XX:+HeapDumpOnOutOfMemoryError -XX:HeapDumpPath="/home/craig/.netbeans/6.7/var/log/heapdump.hprof" org.netbeans.Main --userdir "/home/craig/.netbeans/6.7" "--branding" "nb"


Which appears to be a more verbose version of the error log I got previously.

Craig

---

### Post by craig100 on 2009-09-04
If I start NetBeans from the terminal using sudo ./netbeans then it starts.

Is this how it should be?

Any advice would be appreciated, I'm losing an awful lot of production time here.

TIA

Craig

---

