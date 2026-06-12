---
title: "VMware-server package install not working /AMD64."
date: 2007-06-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by TWFJR on 2007-06-14
VMware/Server

Contents

   1. Installation and Quick Start
   2. Installing VMware Tools on an Ubuntu VMware guest system
   3. Other Topics
         1. Installing from Source
         2. Uninstalling Source Installs
         3. Transitioning from a Source Install
         4. VMware Server MUI Component Installation (Optional, Source Install Only)
         5. VMware Server Console Installation (Optional, Source Install Only)
   4. Additional Resources

VMware Server is a proprietary virtualization software package made available for no cost from the [WWW] VMware website. VMware Server allows you to run entire operating systems in a virtual machine, which runs on top of Edubuntu, Ubuntu or Xubuntu. This guide provides instructions on installing, configuring and running VMware Server and VMware Server Console on (Ed/K/X)Ubuntu.
Installation and Quick Start

    *

      Ubuntu 7.04 (Feisty Fawn)

From Ubuntu packages

   1.

      Get a serial number by registering (for free) at [WWW] [http://register.vmware.com/content/registration.html](http://register.vmware.com/content/registration.html)
   2.

      Add the universe, multiverse, and commercial repositories to your Ubuntu 7.04 install [WWW] Directions.
   3.

      Uninstall vmware-server if it is already installed according to the section in this document titled "Transitioning from a Source Install."
   4.

      Install the vmware-server package
   5.

      Until [WWW] bug #115295 is fixed, edit /etc/pam.d/vmware-authd to read as follows:
          *

            #%PAM-1.0
            auth required pam_unix_auth.so shadow nullok
            account required pam_unix_acct.so
                 

   6.

      Start the remote access console by going to Applications > System Tools > VMWare Server Console in the menus (or run vmware from the command line). From there you will be able to access vmware servers locally or remotely, and create/open VMware virtual machines. Login with your regular username and password.

Ok, the above instructions are not necessarily for AMD64.  But no other instructions that I could find were available to install VMware-server on 7.04.  Here is what I did:  Installed through Synaptic, vmware-server-kernel-modules 2.6.20.16.28.1 (dependency package,) and vmware-server-kernel-modules 2.6.20.16.28 (for linux kernel 2.6.20.) Then in step 5, sudo gedit /etc/pam.d/vmware-authd but no vmware-authd exists.  Nor does step 6's VMWare Server Console exist.  So, I figure I need to uninstall the two packages of vmware and find the correct one's to install.  What are the correct installable VMware-server packages for 7.04 AMD64?  VMware-mui-1.0.3-44356.tar.gz seems to be giving others problems as well.  I have this downloaded.  If this download is the solution, what are the instructions?

---

