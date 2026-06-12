---
title: "Ubuntu 64 and Lotus Notes 8 Gold"
date: 2007-09-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by tbullard on 2007-09-14
Have Lotus 8 Gold Client - trying to install on Ubuntu 64 bit - Install wizard starts then I get an error during the "provisioning process" - the error (in part is) below - Any ideas would be appreciated - tia - tbullard

--start clip
(Sep 12, 2007 9:05:07 PM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, dbg.install, JVM memory before installing Provisioning Action (provisioning): free=9710872 total=57648640
(Sep 12, 2007 9:05:07 PM), RCPCore-Install, com.installshield.product.service.product.PureJavaProductServiceImpl, msg1, installing Provisioning Action (provisioning)
(Sep 12, 2007 9:05:07 PM), RCPCore-Install, com.ibm.pvc.install.product.ProvisioningAction, msg1, Getting rcp.data from /opt/ibm/lotus/notes/framework/rcp/rcplauncher.properties
(Sep 12, 2007 9:05:08 PM), RCPCore-Install, com.ibm.pvc.install.product.ProvisioningAction, err, CWPIM0013E: No .provisioning_rc file found after provisioning process returned.
(Sep 12, 2007 9:05:08 PM), RCPCore-Install, com.ibm.pvc.install.product.ProvisioningAction, msg1, Set RCP_PROVISIONING_RETURN_CODE = -99
(Sep 12, 2007 9:05:08 PM), RCPCore-Install, com.ibm.pvc.install.product.ProvisioningAction, msg1, Set RCP_PROVISIONING_STATUS = Provisioning process failed.  Process failed to launch or was terminated before status could be determined.
(Sep 12, 2007 9:05:08 PM), RCPCore-Install, com.ibm.pvc.install.product.ProvisioningAction, err, An error occurred and product installation failed.  Look at the log file /opt/ibm/lotus/notes/framework/rcp_install.log for details.
(Sep 12, 2007 9:05:08 PM), RCPCore-Install, com.ibm.pvc.install.product.ProvisioningAction, err, ProductException: (error code = 601; message="err"; additional data = [Provisioning process failed.  Process failed to launch or was terminated before status could be determined.])
STACK_TRACE: 25
ProductException: (error code = 601; message="err"; additional data = [Provisioning process failed.  Process failed to launch or was 
-- end clip

---

### Post by praxis22 on 2007-09-15
Looks like a Java Memory error to me, how much do you have in total, and how much are you using?

check this file: **/opt/ibm/lotus/notes/framework/rcp_install.log **on your local machine.

However in an entirely selfless gesture, and having spent many years dealing with Notes, both as a user, and doing application support, I'd advise you to trash it, and your mail file and go find something more friendly instead. Seriously, Notes is just bad.

There are any number of mail clients out there that are infinitely better, such as Evolution or Thunderbird, etc.

---

### Post by tbullard on 2007-09-15
Thanks - I'm running with 4 gig of memory on an am64 dualcore - We use Lotus notes at work so I'm trying to run at home with it :-)  It seems to be an issue that a file - is not found - below is the snippet - I had installed this Note 8 Gold version on an earlier install of the 32 bit Ununtu - same machine - and it installed fine - but when I went to 64 bit - no dice - thanks again..

Sep 12, 2007 9:37:37 PM), RCPCore-Install, com.ibm.pvc.install.product.ProvisioningAction, msg1, Getting rcp.data from /opt/ibm/lotus/notes/framework/rcp/rcplauncher.properties
(Sep 12, 2007 9:37:39 PM), RCPCore-Install, com.ibm.pvc.install.product.ProvisioningAction, err, CWPIM0013E: No .provisioning_rc file found after provisioning process returned.
(Sep 12, 2007 9:37:39 PM), RCPCore-Install, com.ibm.pvc.install.product.ProvisioningAction, msg1, Set RCP_PROVISIONING_RETURN_CODE = -99

---

### Post by praxis22 on 2007-09-15
Hi,

Try this see if it works:

./setup.bin -V useNotesDataForWorkspace="true"

---

### Post by tbullard on 2007-09-15
Thanks for the suggestion - but still no go - same error as before :-(

---

### Post by limaunion on 2007-09-16
I don't have an idea about your problem but you may want to check for similar errors at [http://support.lotus.com](http://support.lotus.com) or [http://www.notes.net](http://www.notes.net) (in the forum section).
HTH

---

### Post by jdos2 on 2007-11-25
I'm having the same trouble installing it on my Laptop- a Toshiba with a dual core AMD 64 bit processor.
What's worse is that it leaves the not-installed Notes associated with StarOffice (oops! OpenOffice!) documents, and I now have to figure out how to get gnome to forget about 'em.

---

### Post by the.j on 2007-11-26
I get the same message when trying to install Symphony on 7.10...

I have a dual amd64 too...

Hmmmm  !

---

### Post by Xantane on 2007-12-12
Same issue with Intel core2 duo on ubuntu 64 7.10 ](*,)

---

### Post by MrKnoedelmann on 2008-04-06
Hi,

I tried to setup LN 801 on GNU/Linux (Ubuntu 7.10 AMD64) as well - without success.
I guess it has todo with 64bit kernel/libs as I get the following error in "/root/Lotus/XPD/logs/error-log-0.xml"

<extendedDataElements name="CommonBaseEventLogRecord:Exception" type="string"><values>java.lang.UnsatisfiedLinkError: /opt/IBM/Lotus/Notes/framework/rcp/eclipse/plugins/com.ibm.rcp.os.linux_6.1.1.200802211037/os
.linux_6.1.1.200802211037/os/linux/x86/libos.so (libxkbfile.so.1: cannot open shared object file: No such file or directory)&#xA;&#x9;at java.lang.ClassLoader.loadLibraryW

this is because there is no /usr/lib32/libxkbfile.so.1 - there is only the 64bit library in /usr/lib
so my assumption is that LN801 runs with Java (Eclipse RCP) but is not platform indepented as it depends on a 32bit linux librarys

btw. to get the setup.sh working, I had to manually mkdir /etc/lots/notes ; ln -s /home/knoedel/download/deploy/install.xml ./install.xml ; and set the DISPLAY var to get a GTK errormessage window (although I started ./setup.sh -console !)
who knows why they supply their own Java JRE if it still depends on os libs ... ??
hopefully the guys at IBM also try 64bit GNU/Linux in the future! (Eclipse 3.2 runs fine)

root@section60:~# uname -a
Linux section60 2.6.22-14-generic #1 SMP Tue Feb 12 02:46:46 UTC 2008 x86_64 GNU/Linux
root@section60:~# grep "model name" /proc/cpuinfo 
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 6000+
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 6000+
root@section60:~# date
Mon Apr  7 02:29:07 CEST 2008

hth ... 
greetings
:)

---

