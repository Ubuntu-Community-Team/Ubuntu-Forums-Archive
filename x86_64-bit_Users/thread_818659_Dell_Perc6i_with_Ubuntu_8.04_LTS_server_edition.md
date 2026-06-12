---
title: "Dell Perc6/i with Ubuntu 8.04 LTS server edition"
date: 2008-06-04
forum: x86 64-bit Users
---

### Post by ha2432003 on 2008-06-04
I'm having trouble getting Ubuntu to properly communicate with my Raid controller.  Using Dell's OMSA system, the output from 'omreport storage controller' is posted below.  The problematic line is where the 'State' is reported as 'Degraded'.  The report indicates that the megaraid_sas driver version is out of date, but I've had no success trying to compile the new driver release on the Dell website for my system (the compile completes correctly, but my system then doesn't bring up the disks properly on reboot).  I'd really appreciate any help with this issue as its all thats standing between me and getting the servers we just had shipped up and running.  Thanks!


Controllers
ID                                : 0
Status                            : Non-Critical
Name                              : PERC 6/i Integrated
Slot ID                           : Embedded
State                             : Degraded
Firmware Version                  : 6.0.2-0002
Minimum Required Firmware Version : Not Applicable
Driver Version                    : 00.00.03.10-rc5 
Minimum Required Driver Version   : 00.00.03.13
Number of Connectors              : 2
Rebuild Rate                      : 30%
BGI Rate                          : 30%
Check Consistency Rate            : 30%
Reconstruct Rate                  : 30%
Alarm State                       : Not Applicable
Cluster Mode                      : Not Applicable
SCSI Initiator ID                 : Not Applicable
Cache Memory Size                 : 256 MB
Patrol Read Mode                  : Auto
Patrol Read State                 : Stopped
Patrol Read Rate                  : 30%
Patrol Read Iterations            : 2

---

### Post by msghaleb on 2008-06-19
same problem here!

---

### Post by oneloveamaru on 2008-06-23
I can't get dell omsa 5.4 installed correctly on 8.04. Did you guys follow some guide? I get a couple errors. 

Starting dsm_sa_datamgr32d: /opt/dell/srvadmin/dataeng/bin/dsm_sa_datamgr32d: error while loading shared libraries: libdcsmil32.so.5: cannot open shared object file: No such file or directory
 *
Starting dsm_sa_eventmgr32d: /opt/dell/srvadmin/dataeng/bin/dsm_sa_eventmgr32d: error while loading shared libraries: libdcsupt32.so.5: cannot open shared object file: No such file or directory
 *

Well, I guess they are the same errors but pretty much, it's not completely installed and won't start. Do you guys have any suggestions or a guide I can dive into. I got OMSA 5.4 working perfectly on my Debian etch boxes.

I appreciate any help, thanks!

---

### Post by mrmagos on 2008-07-28
> **oneloveamaru said:**
> I can't get dell omsa 5.4 installed correctly on 8.04. Did you guys follow some guide? I get a couple errors. 

Starting dsm_sa_datamgr32d: /opt/dell/srvadmin/dataeng/bin/dsm_sa_datamgr32d: error while loading shared libraries: libdcsmil32.so.5: cannot open shared object file: No such file or directory
 *
Starting dsm_sa_eventmgr32d: /opt/dell/srvadmin/dataeng/bin/dsm_sa_eventmgr32d: error while loading shared libraries: libdcsupt32.so.5: cannot open shared object file: No such file or directory
 *

Well, I guess they are the same errors but pretty much, it's not completely installed and won't start. Do you guys have any suggestions or a guide I can dive into. I got OMSA 5.4 working perfectly on my Debian etch boxes.

I appreciate any help, thanks!

I got those errors, too. Doing a
```
sudo ldconfig
sudo /etc/init.d/dataeng restart
```
resolved the errors in my case. Though, I can't help on the megaraid module issue; my servers are too old for that.

---

### Post by oneloveamaru on 2008-10-03
mrmagos, that solved it for me, thanks.

ha2432003, sorry for replying months later, the reason it says degraded is just because your driver is out of date. Were you trying to run 32bit or 64bit? People have gotten the new driver to compile correctly on 32bit but 64bit is a no go. I just installed Debian Lenny and that solved all my problems. Driver version 3.20 on that. This is probably too late to help you but maybe it'll help someone else. :)

---

### Post by el_baby on 2009-05-02
Thanx, mrmagos... had the same problem as onelovemaru (using ubuntu 8.10 after upgrading to omsa 5.5) and your recipe worked for me too.

Regards.

---

### Post by mr_scary on 2009-10-29
I have a 8.04 Ubuntu package containing the megaraid_sas driver found in the Jaunty release if anyone is interested.

---

### Post by rockyzhangxq on 2009-11-03
[SIZE=2]Hello Mr_scary,

I am interested in the driver. Does it fix driver version (00.00.03.10-rc5 so far, should be 00.00.03.20) bug? I need to install Nagios openmanage plugin for our servers; But it kept complaining that the driver version mismatch/out of date, which is quite annoying for me.

[/SIZE][FONT=monospace][SIZE=2]BTW, I am running Ubuntu hardy LTS server 64-bit on Dell PowerEdge T300 server.

Thanks,
Rocky
[/SIZE]
[/FONT]> **mr_scary said:**
> I have a 8.04 Ubuntu package containing the megaraid_sas driver found in the Jaunty release if anyone is interested.

---

