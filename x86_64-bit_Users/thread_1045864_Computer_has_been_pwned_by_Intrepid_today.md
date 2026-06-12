---
title: "Computer has been pwned by Intrepid today"
date: 2009-01-20
forum: x86 64-bit Users
---

### Post by Mitch on 2009-01-20
Came home, booted up and started Firefox - got a nice Kernel Panic dump to the terminal.  Rhythmbox crashes, Firefox crashes, Konquer crashes, Netbeans Crashes.  My computer is unusable.  What is going on?

Here are some errors:

Firefox in terminal:

Segmentation fault

Netbeans (another seg fault)

#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00007fcc59a88ead, pid=7718, tid=1082542416
#
# Java VM: Java HotSpot(TM) 64-Bit Server VM (11.0-b15 mixed mode linux-amd64)
# Problematic frame:
# V  [libjvm.so+0x2faead]
#
# An error report file with more information is saved as:
# /home/mitch/hs_err_pid7718.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
/opt/netbeans-6.5/bin/../platform9/lib/nbexec: line 493:  7718 Aborted                 "/usr/lib/jvm/java-6-sun/bin/java" -Djdk.home="/usr/lib/jvm/java-6-sun" -classpath "/opt/netbeans-6.5/platform9/lib/boot.jar:/opt/netbeans-6.5/platform9/lib/org-openide-modules.jar:/opt/netbeans-6.5/platform9/lib/org-openide-util.jar:/opt/netbeans-6.5/platform9/lib/locale/boot_ja.jar:/opt/netbeans-6.5/platform9/lib/locale/boot_pt_BR.jar:/opt/netbeans-6.5/platform9/lib/locale/boot_zh_CN.jar:/opt/netbeans-6.5/platform9/lib/locale/org-openide-modules_ja.jar:/opt/netbeans-6.5/platform9/lib/locale/org-openide-modules_pt_BR.jar:/opt/netbeans-6.5/platform9/lib/locale/org-openide-modules_zh_CN.jar:/opt/netbeans-6.5/platform9/lib/locale/org-openide-util_ja.jar:/opt/netbeans-6.5/platform9/lib/locale/org-openide-util_pt_BR.jar:/opt/netbeans-6.5/platform9/lib/locale/org-openide-util_zh_CN.jar:/usr/lib/jvm/java-6-sun/lib/dt.jar:/usr/lib/jvm/java-6-sun/lib/tools.jar" -Dnetbeans.system_http_proxy="DIRECT" -Dnetbeans.system_http_non_proxy_hosts="" -Dnetbeans.dirs="/opt/netbeans-6.5/nb6.5:/opt/netbeans-6.5/ide10:/opt/netbeans-6.5/webcommon1:/opt/netbeans-6.5/websvccommon1:/opt/netbeans-6.5/gsf1:/opt/netbeans-6.5/ruby2:" -Dnetbeans.home="/opt/netbeans-6.5/platform9" '-Dnetbeans.importclass=org.netbeans.upgrade.AutoUpgrade' '-Dnetbeans.accept_license_class=org.netbeans.license.AcceptLicense' '-Xmx512m' '-client' '-Xverify:none' '-Xss2m' '-Xms32m' '-XX:PermSize=32m' '-XX:MaxPermSize=200m' '-Dapple.laf.useScreenMenuBar=true' '-Dsun.java2d.noddraw=true' org.netbeans.Main --userdir "/home/mitch/.netbeans/6.5" "--branding" "nb"

Can anyone tell me what might be going on or what I should do?

---

### Post by TaTaE on 2009-01-21
Did u overclocked something,    mitch ?
Or maybe could you check your RAM and inside coolers for blocking and such...

---

### Post by timcredible on 2009-01-21
looks like hardware problem.  you could boot with your ubuntu livecd and see if it works ok, if it does, then i would suspect the hard drive.

---

### Post by Mitch on 2009-01-21
I should have figured it was a hardware problem, but the new upgrade to Intrepid threw me off the scent.  

I ran memtest84 and found that one of my RAM sticks had become a total mess.  Trying to RMA.  Thanks for the responses.

---

