---
title: "Intel Fortran 9 compiler on 64-bit Edgy"
date: 2006-12-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by Extr3me on 2006-12-05
OK, I have spent the last week getting a working install of the Intel Fortran compilers (the non-commercial, free version) on my 64-bit Edgy install.  Really, once I had it all going I was kicking myself in the pants due to the obviousness of the problems.

To start, register for the non-commercial (unlimited license) or the evaluation license (1-month) of the Intel compilers from their web site.  I got the link originally from the following Fortran page (very helpful :)):

[http://www.thefreecountry.com/compilers/fortran.shtml](http://www.thefreecountry.com/compilers/fortran.shtml)

Obtain the license key and make sure you download the correct version for the license you have been issued!  I can't stress that enough, each license is for one version only!!

You can check your registration details, including what version you have been licensed; getting another license key posted out to you or even just the link to the correct download page from:

[https://registrationcenter.intel.com/regcenter/register.aspx](https://registrationcenter.intel.com/regcenter/register.aspx)

Once you have the tar.gz downloaded, unzip the file to a folder in your home folder or wherever.

Before going any further, you will need to install some packages to get this all working.  You need to install:  rpm; build-essential; ia32-libs.

I reckon these are the minimum you need, but I have installed some others during my process of getting this to work which you may not need, these include: libc6-i386; libstdc++5.  Check out this Intel page for their info on the matter:

[http://www.intel.com/support/performancetools/c/linux/sb/CS-023486.htm](http://www.intel.com/support/performancetools/c/linux/sb/CS-023486.htm)

OK, from here you can try to install the compilers and debugger from their install.sh script in the root of the directory tree you just uncompressed.  

To get any of the scripts to run in Ubuntu, you have to change the first line of the script to call the bash shell rather than the sh shell.

eg:  from -> #!/bin/sh -> to -> #!/bin/bash

The unzipped files have two scripts that need to be modified, one called install.sh in the root dir, and one called install_fc.sh in the data sub-folder.  This is the case for the Fortran compilers at least.

Don't forget to either use a root shell to do the install or use sudo for calling each of the scripts.

As the intel installer uses rpm's which are designed for RedHat systems, you might have more luck using the --nonrpm flag when you call install.sh.  This will force the install script to use either rpm2cpio which should be installed already.

I never got the install to work, so I was forced to use a non-default installation method.  Intel give some very good instructions at:

[http://www.intel.com/support/performancetools/fortran/linux/sb/cs-017157.htm](http://www.intel.com/support/performancetools/fortran/linux/sb/cs-017157.htm)

Be wary of the following line:

rpm2cpio l_fc_pc_8.1.022/intel-ifort8-8.1-022.i386.rpm |cpio -i

I discovered that the rpm's have a pre-set directory structure so it will create a folder structure from the dir you run rpm2cpio.  If you are doing a root install like myself, run this command from the root directory of your filesystem and it will uncompress to the /opt/intel/fce structure.  I also needed to add a -d flag to cpio.  Therefore:

cd /
rpm2cpio /home/extr3me/l_fc_pc_9.1.040/data/intel-iforte91040-9.1.040-1.em64t.rpm |cpio -id

Now you have the compiler uncompressed and in the /opt/intel folder.  The license key that should have been emailed to you as an attachment should be saved to the folder /opt/intel/licenses that you may have to create yourself.

Following the intel guide, change the scripts to point to the correct installation directory, not forgetting to change the calls from the sh shell to the bash shell and all should be rosy.

If you want this compiler to be permantently enable, then you could add the source /opt/intel/fc...../ifortvars.sh command to your .bashrc or summit.

That was all I needed to do to get it all working!!  Good luck to everyone, and if you get really stuck the intel support team are actually particularly helpful if you get stuck.

If you find my english or grammar in this post bad, then just ask some questions.  This post is too long already, and I need to do some work!!

---

