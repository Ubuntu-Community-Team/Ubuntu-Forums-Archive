---
title: "Problems installing MatLab 7 R14 on Ubuntu 7.04 64 bit"
date: 2007-05-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by Dan23 on 2007-05-11
After reading a little bit on MathWorks, I used the following to install from the terminal:
code: sudo sh install -glnx86 -nocp -t

This got me the following screen:
                         Welcome to the MATLAB Installer

   ---------------------------------------------------------------------------
   | Please review the license agreement on the next set of screens.  On any |
   | screen the options to proceed are at the bottom.  Type your response    |
   | at the prompt.                                                          |
   ---------------------------------------------------------------------------

                                 [screen 1 of 90]
                                                 
The MathWorks, Inc.
Software License Booklet

IMPORTANT NOTICE

Read the terms and conditions of your License Agreement carefully.

----------------------------------------------------------------------------
                >>>>>>>> For this License Agreement <<<<<<<<
Enter either:  <return>       a        r        p      ^C
To:          [next screen] [accept] [reject] [print] [abort]
----------------------------------------------------------------------

After choosing the option "a" I got the error:
/media/cdrom0/update/install/main.sh: 603: /media/cdrom0/update/bin/glnx86/xsetup: Permission denied

I`ve tried to read here in the forums about MatLab on 64 bit but nothing from what I found helped me.

This stuff are really frustrating. I`m new to Linux and really trying to make the transition from XP to work but because of things like this, this is not a walk in the park.

---

### Post by seatopia on 2007-05-11
I had a similar problem installing Matlab R2007a on my 32-bit system.  The problem was that the cdrom drive is not mounted with executable permissions (I guess this is the default in Ubuntu).  I solved it by editing the /etc/fstab file and adding "exec" to the option line for the cdrom, e.g:

/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0

After that the installation went normally.

---

### Post by schrodingerscat on 2007-06-22
ive had exactly the same problem with the xsetup file. to see if it was the drive executable error, i copied the contents of the cd to a directory in my home folder and ran the install script from there. Unfortunately, it was the same error. Has anyone found a solution to this problem by any chance?:(

---

### Post by Cappy on 2007-06-22
try a 
```
sudo chown -R $USER:$USER directory_name_you_copied_to
chmod 777 -R directory_name_you_copied_to
```
777 lets anyone write/read from that directory so you should delete the folder after installation

---

