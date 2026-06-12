---
title: "Yum failure"
date: 2008-07-23
forum: x86 64-bit Users
---

### Post by Imap on 2008-07-23
Hello,

Following the instructions at:
[http://www.virtuatopia.com/index.php/Building_a_Xen_Guest_Root_Filesystem_using_yum_and_rpm](http://www.virtuatopia.com/index.php/Building_a_Xen_Guest_Root_Filesystem_using_yum_and_rpm)
I am trying to setup centOS as domainU on my Ubuntu hardy desktop
(which is domain0). When I try the yum command I get error:

$yum --installroot=/xen/vm2/root -y groupinstall Base
Setting up Group Process
Setting up repositories
base                      100% |=========================| 1.1 kB    00:00     
updates                   100% |=========================|  951 B    00:00     
addons                    100% |=========================|  951 B    00:00     
extras                    100% |=========================| 1.1 kB    00:00     
comps.xml                 100% |=========================| 914 kB    00:04     
Traceback (most recent call last):
  File "/usr/bin/yum", line 27, in <module>
    yummain.main(sys.argv[1:])
  File "/usr/share/yum-cli/yummain.py", line 92, in main
    result, resultmsgs = do()
  File "/usr/share/yum-cli/cli.py", line 555, in doCommands
    self.doGroupSetup()
  File "/var/lib/python-support/python2.5/yum/__init__.py", line 325, in doGroupSetup
    self.groupInfo.add(groupfile)
  File "/var/lib/python-support/python2.5/yum/Errors.py", line 55, in __init__
    YumBaseError.__init__(self)
  File "/var/lib/python-support/python2.5/yum/Errors.py", line 25, in __init__
    self.args = args
TypeError: 'NoneType' object is not iterable

I am not familiar with python and wondering if you have any suggestions
on what could be the reason for above error.

Thanks

---

### Post by Thelasko on 2008-07-23
I must admit, I am confused about what you are trying to do.  I think this would be a more appropriate question for the people at CentOS.  The most obvious reason for Yum not working is because Ubuntu doesn't use RPM.  It uses APT and DEB.

Perhaps someone with more insight than myself can steer you in the right direction.

---

### Post by John.Michael.Kane on 2008-07-23
According to the site linked to, it is for Linux distributions which uses yum and rpm for package management. which Ubuntu being deb base does not use.

As for building a xen type of system Ubuntu seems to be able to do this. 
[https://help.ubuntu.com/community/Xen](https://help.ubuntu.com/community/Xen)
[http://www.howtoforge.com/ubuntu-8.04-server-install-xen-from-ubuntu-repositories](http://www.howtoforge.com/ubuntu-8.04-server-install-xen-from-ubuntu-repositories)

Also building xen using the guide you linked to will most likely require you either directly install centos or some other rpm based distro to it's own partition, or try test building it by installing centos via vmware, and building it in that environment.

---

### Post by Imap on 2008-07-23
Thank you Thelasko and John.Michael.Kane for your resonses.

I am using Ubuntu hardy desktop as the domain0 (the host OS) and hence these utilities
need to come from the host. I have the xen system already configured and working with
Ubuntu desktop as the host. I am trying to have a centOS as a guest OS. Until I have
the initial images and other packages configured, I need to work with the utilities
available in Ubuntu, but work with rpm based packages and hence my attempt to use
the listed URL and yum.

I have already gone over the links that you have attached and they are not helpful
for centOS install on Ubuntu. I have tried the instructions there and tried to use
xen-tools and 'rinse' to install centOS, but no go. I got the following error:
----------
There was a problem importing one of the Python modules
required to run yum. The error leading to this problem was:

   No module named sqlitecachec

Please install a package which provides this module, or
verify that the module is installed correctly.

It's possible that the above module doesn't match the
current version of Python, which is:
2.4.3 (#1, May 24 2008, 13:57:05)
[GCC 4.1.2 20070626 (Red Hat 4.1.2-14)]
---------

I am thinking that if I can get the yum work properly and install the base system
I should be able to bring up the centOS and then could do further configuration 
from with in the centOS.

Thanks

---

### Post by John.Michael.Kane on 2008-07-23
I am not currently logged in on my test of centos, but I am guessing the error to be saying that is a version mismatch. Which seems odd, as the version of sqlitecachec included with ubuntu calls for python (>= 2.4), and python (>= 2.5).

Also the version for centos 5.2 calls on python(abi) = 2.4, as well.

Below are two links the the sqlitecachec package.
[http://rpm.pbone.net/index.php3/stat/4/idpl/8081803/com/yum-metadata-parser-1.1.2-2.el5.x86_64.rpm.html]("http://rpm.pbone.net/index.php3/stat/4/idpl/8081803/com/yum-metadata-parser-1.1.2-2.el5.x86_64.rpm.html")

[http://packages.ubuntu.com/hardy/python/python-sqlitecachec]("http://packages.ubuntu.com/hardy/python/python-sqlitecachec")

By the way what version of centos are you running?

---

### Post by Imap on 2008-07-23
Thank you for your response.

Installation of python-sqlitecache did not resolve the issue. I am still getting
the same error. There is another statement that I am not sure if it is a related
error. Here is the complete log output:

-----------------------------------
Installation method: rinse
                                                                               
                                                                                
Running post-install script post-install.sh:
  Creating resolv.conf
[: 32: ==: unexpected operator         <-- I don't know if this is an error
BUGFIX                                 <--         ''
  Mounting /proc
  Bootstrapping yum
  Authfix
There was a problem importing one of the Python modules
required to run yum. The error leading to this problem was:

   No module named sqlitecachec

Please install a package which provides this module, or
verify that the module is installed correctly.

It's possible that the above module doesn't match the
current version of Python, which is:
2.4.3 (#1, May 24 2008, 13:57:05) 
[GCC 4.1.2 20070626 (Red Hat 4.1.2-14)]

If you cannot solve this problem yourself, please go to 
the yum faq at:
  [http://wiki.linux.duke.edu/YumFaq](http://wiki.linux.duke.edu/YumFaq)
  

chroot: cannot run command `/usr/bin/authconfig': No such file or directory
  Cleaing up
There was a problem importing one of the Python modules
required to run yum. The error leading to this problem was:

   No module named sqlitecachec

Please install a package which provides this module, or
verify that the module is installed correctly.

It's possible that the above module doesn't match the
current version of Python, which is:
2.4.3 (#1, May 24 2008, 13:57:05) 
[GCC 4.1.2 20070626 (Red Hat 4.1.2-14)]
-----------------------------------

I am surprised that the installation of python-sqlitecachec did not really have 
an effect on the error message!

Thanks

---

