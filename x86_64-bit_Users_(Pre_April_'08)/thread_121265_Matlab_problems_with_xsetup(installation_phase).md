---
title: "Matlab problems with xsetup(installation phase)"
date: 2006-01-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by Tinuz on 2006-01-24
I have a problem with matlab 7.04 r14 sp2 on Hoary 5.10 AMD64.

I have tried numerous solutions and searched everywhere, but cannot find anything.
I create the directories as asked, copy the license file and start the setup using sudo /home/tinuz/Mlab/install (I also tried from the CD-ROM but this does not make any difference).
I get setup it asks me about the agreement, where my folder is and shows me my license file. When the license file show i click on the 'OK' button and then Matlab setup exits with the following error: 


/media/cdrom1/install: line 713: /lib64/libc.so.6: Permission denied
/tmp/6797tmwinstall/install: line 713: /lib64/libc.so.6: Permission denied
/tmp/6797tmwinstall/update/install/main.sh: line 244:  8725 Segmentation fault     "$xsetup" $arglist 2>$tmp_file
-------------------------------------------------------------------

    An error status was returned by the program 'xsetup',
    the X Window System version of 'install'. The following
    messages were written to standard error:


    Attempt to fix the problem and try again. If X is not available
    or 'xsetup' cannot be made to work then try the terminal
    version of 'install' using the command:

            install* -t    or    INSTALL* -t

-------------------------------------------------------------------
/tmp/6797tmwinstall/update/install/abort.sh: line 15: /tmp/6797tmwinstall/update/install/cleanup.sh: No such file or directory

I can remove the permission denieds through editing the install.sh file, but this does not seem to make any difference. The errors beneath the main body seem to originate from some exit script and seem not relevant. 
Debugging also shows me nothing, namely, the following:

CONVERT : update/data/settings.ini -to-
                update/data/settings.ini
Reading /media/cdrom1/update/data/settings.ini.
        settings line = cdnum=1
CD_ROOT        :/media/cdrom1
TMW_CD_FORMAT  :sgi
CDNUM is       :1
Student is     :0
FTP_INSTALL is :0
RunMode is     :xsetup
CONVERT : update/data/mathelp.enc -to-
                update/data/mathelp.enc
CONVERT : update/data/Xsetup -to-
                update/data/xsetup
MOVE    : /media/cdrom1/update/data/xsetup to /tmp/Xsetup
CONVERT : update/data/mat.xbm -to-
                update/data/mat.xbm
CONVERT : update/data/in.xbm -to-
                update/data/in.xbm
CONVERT : license.txt -to-
                license.txt
Got Pathname /home/tinuz/MatLab704
DirPerms: /home/tinuz/MatLab704  1
CONVERT : update/data/matinfo.enc -to-
                update/data/matinfo.enc
DIRCREAT: /home/tinuz/MatLab704/etc
DirPerms: /home/tinuz/MatLab704/etc  1
Found MathWorks DAEMON
Found SERVER line

(This is done from the CD)

I read through the bash scripts, but i can't really find what goes wrong(i can find where the error originates, around line 158 it seems). 
Anybody got any clue as to where it went wrong?

PS. I have used matlab on a previous install of ubuntu(5.04) AMD64, so it seems to be some version related problem, but i cannot be sure about this.

---

### Post by socsuj on 2006-01-25
Are the permissions for /lib64/libc.so.6 set up correctly?  Following the first post in [this]("http://ubuntuforums.org/showthread.php?t=90895") thread you may need to run

```
sudo chmod 755 /lib64/libc.so.6
```

---

### Post by supsup on 2006-01-26
I installed Matlab 7.04 r14 sp2  without any problem.

But it does not work. (see [http://ubuntuforums.org/showthread.php?t=53222&highlight=matlab)](http://ubuntuforums.org/showthread.php?t=53222&highlight=matlab)). I have the same problems. 

To solve it i run matlab in chroot of debian amd64 sarge. (I suppose Hoary amd64 chroot will be good as well).
Back to your problems:

1. I installed in root shell : sudo -s and then install
2. try text installer.
2. check your env. variables.

---

