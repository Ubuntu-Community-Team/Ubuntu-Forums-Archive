---
title: "Install Hangs as VMWare guest"
date: 2007-01-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by gmaltby on 2007-01-08
Hello,

I'm having problems with the installation of Ubuntu Server as a Guest within a VMWare server.

I'm running a Dell 1950 (dual Xeon) with VMWare Server 1.0.1. The host is running Ubuntu 6.06.1 AMD64. Aside from the known Raid/NIC issues, the host installation goes without error and VMWare Server installs and runs without error.


The problem occurs during the installation of a Guest server. The installation hangs at 5% during the 'Select and install software' stage. Using Alt+F2 and going to a console, I can see a zombie instance of 'aptitude'. 'ps faxw' shows:

...

360 S+ 0:00 \_ /usr/bin/perl -w /usr/bin/debconf-apt-progress --from 50 --to 860
361 Z+ 0:00 \_ [aptitude]
...

The last entry in syslog is:
---
in-target: Setting up ubuntu-standard (0.120)
---

If I kill the parent (PID 360), the installation continues and complete without further problem. After the reboot, the installation boots correctly and appears complete.

The guest being installed is Ubuntu 6.06.1 (either 386 or AMD64 versions) -- the hang occurs on both versions at the same point. The installation is being done from ISO images, MD5 verified and also used many times previously so I assume them to be complete and accurate.

This same setup is in use on several Dell 860 and 750 servers (in total - 3 hosts and ~15 guests) and I've not had a problem to date. The only difference is the host hardware and host OS running the AMD64 version.

I would stress, the VM is still running without any obvious problem - switching to the console show the machine to be active so I don't think it is a VMWare issue specifically.

I've not had reason to look at the Ubuntu install process before now so any guidance on further debug would be appreciated. Any ideas on preventing the hang would be really appreciated. :)

Cheers,
Graham

---

### Post by aidtwo on 2007-01-11
Thank you for posting this information.  It helped me to successfully install Ubuntu Server 6.06.1 LTS on a Microsoft Virtual Server 2005 R2 (1.1.465.292 EE R2).

It would be helpful to learn what causes this hang and why killing the one process seems to allow the installation to complete successfully.

-Adrian

---

