---
title: "Instaling vmware server problem"
date: 2006-08-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by killkoy on 2006-08-21
I am having trouble installing vmware sever.

I download the tar binary from the vmware site and extract it then run ```
./vmware-install.pl
```
and the following happens. 
```
 ./vmware-install.pl
Creating a new installer database using the tar3 format.

Installing the content of the package.

In which directory do you want to install the binary files?
[/usr/bin]

The file /usr/bin/vmware-uninstall.pl that this program was about to install
already exists. Overwrite? [yes]

The file /usr/bin/vmnet-bridge that this program was about to install already
exists. Overwrite? [yes]

The file /usr/bin/vmnet-sniffer that this program was about to install already
exists. Overwrite? [yes]

The file /usr/bin/vmnet-netifup that this program was about to install already
exists. Overwrite? [yes]

The file /usr/bin/vmnet-dhcpd that this program was about to install already
exists. Overwrite? [yes]

The file /usr/bin/vmware-loop that this program was about to install already
exists. Overwrite? [yes]

The file /usr/bin/vmware that this program was about to install already exists.
Overwrite? [yes]

The file /usr/bin/vmrun that this program was about to install already exists.
Overwrite? [yes]

The file /usr/bin/vmware-mount.pl that this program was about to install
already exists. Overwrite? [yes]

The file /usr/bin/vmware-config.pl that this program was about to install
already exists. Overwrite? [yes]

The file /usr/bin/vmware-vdiskmanager that this program was about to install
already exists. Overwrite? [yes]

The file /usr/bin/vmware-ping that this program was about to install already
exists. Overwrite? [yes]

The file /usr/bin/vmnet-natd that this program was about to install already
exists. Overwrite? [yes]

The file /usr/bin/vmware-cmd that this program was about to install already
exists. Overwrite? [yes]

The file /usr/bin/vmware-authtrusted that this program was about to install
already exists. Overwrite? [yes]

The file /usr/bin/vm-support that this program was about to install already
exists. Overwrite? [yes]

What is the directory that contains the init directories (rc0.d/ to rc6.d/)?
[/etc]

What is the directory that contains the init scripts?
[/etc/init.d]

The file /etc/init.d/vmware that this program was about to install already
exists. Overwrite? [yes]

Unable to copy the source file ./installer/services.sh to the destination file
/etc/init.d/vmware.

Execution aborted.


```
This is a reistall of vmware and i have been using [this]("http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware+installation+failed") guide

Any help would be much apreciated

Thanks, killkoy

---

### Post by killkoy on 2006-08-21
ok iv solved this problem by deleting the vmware folder from /etc/init.d/

---

