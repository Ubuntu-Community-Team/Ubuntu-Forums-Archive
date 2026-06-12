---
title: "mldonkey install error"
date: 2006-04-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by cosmoshell on 2006-04-20
root@ubuntu:~# apt-get install mldonkey-server
Reading package lists... Done
Building dependency tree... Done
mldonkey-server is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up mldonkey-server (2.7.1-2ubuntu1) ...
Fatal error: exception Failure("lexing: empty token")
dpkg: error processing mldonkey-server (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 mldonkey-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ubuntu:~#

---

### Post by ivangotoy on 2006-04-23
my humble advice is simple : compile wxGTK 2.6.3 then compile aMule CVS and 

just make sure you DO NOT have older wxGTK and if you have just uninstall it then compile wxGTK from : 

[http://prdownloads.sourceforge.net/wxwindows/wxGTK-2.6.3.tar.gz](http://prdownloads.sourceforge.net/wxwindows/wxGTK-2.6.3.tar.gz)

to get wxGTK properly compiled for aMule in configuration option just type 

./configure --enable-unicode

to have wxGTK u need some gcc and other stuff but it is not big deal to get it

for aMule CVS : [http://www.hirnriss.net/?area=cvs](http://www.hirnriss.net/?area=cvs)  - get the latest on your

own risk and i hope you will have no problems

---

### Post by skylark on 2006-04-24
I remember playing with mldonkey back with Hoary and it worked fine. I just tried to install it and it went ahead with no problem:

```
$ sudo aptitude install mldonkey-server
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
The following NEW packages will be installed:
  mldonkey-server
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 2543kB of archives. After unpacking 7377kB will be used.
Writing extended state information... Done
Get:1 http://au.archive.ubuntu.com breezy/universe mldonkey-server 2.5.28.1-1 [2 543kB]
Fetched 702kB in 22s (31.3kB/s)

Preconfiguring packages ...
Selecting previously deselected package mldonkey-server.
(Reading database ... 109565 files and directories currently installed.)
Unpacking mldonkey-server (from .../mldonkey-server_2.5.28.1-1_amd64.deb) ...
Setting up mldonkey-server (2.5.28.1-1) ...

Creating config file /etc/default/mldonkey-server with new version
Starting MLDonkey: mlnet configuration file prevent mlnet to be started (use for ce-start).

Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
```

Maybe try again after an apt-get (or aptitude) update?

Ahh.. I just noticed your machine is trying to install mldonkey-server (2.7.1-2ubuntu1)... are you running Dapper? 

As ivangotoy suggested there are alternatives... although mldonkey is great because it supports a wide variety of networks (and you can use it's telnet interface to cue stuff remotely!).

---

