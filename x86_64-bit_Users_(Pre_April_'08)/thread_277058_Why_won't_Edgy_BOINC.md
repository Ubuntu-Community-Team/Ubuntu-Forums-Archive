---
title: "Why won't Edgy BOINC?"
date: 2006-10-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by sheenaramone on 2006-10-13
The other night I installed an Edgy 64 bit and tried to use BOINC.  Tonight I am using a live Edgy Xubuntu cd.  This is what happens:

ubuntu@ubuntu:~$ sh boinc*
now run /home/ubuntu/BOINC/run_client to run the client and /home/ubuntu/BOINC/run_manager to run the GUI
ubuntu@ubuntu:~$ cd BOINC
ubuntu@ubuntu:~/BOINC$ ./run_client
./run_client: line 1: /home/ubuntu/BOINC/boinc: No such file or directory
./run_client: line 1: /home/ubuntu/BOINC/boinc: Success
ubuntu@ubuntu:~/BOINC$ 
ubuntu@ubuntu:~/BOINC$ 

This is what is supposed to happen:

gideon@gideon:~$ sh boinc*
now run /home/gideon/BOINC/run_client to run the client and /home/gideon/BOINC/run_manager to run the GUI
gideon@gideon:~$ cd BOINC
gideon@gideon:~/BOINC$ ./run_client
2006-10-13 21:08:25 [---] Starting BOINC client version 5.4.9 for i686-pc-linux-gnu
2006-10-13 21:08:25 [---] libcurl/7.15.3 OpenSSL/0.9.8a zlib/1.2.3
2006-10-13 21:08:25 [---] Data directory: /home/gideon/BOINC
2006-10-13 21:08:25 [---] Processor: 2 GenuineIntel               Intel(R) Pentium(R) D CPU 3.60GHz
2006-10-13 21:08:25 [---] Memory: 1.96 GB physical, 3.05 GB virtual
2006-10-13 21:08:25 [---] Disk: 70.36 GB total, 63.78 GB free
2006-10-13 21:08:25 [---] No general preferences found - using BOINC defaults
2006-10-13 21:08:25 [---] Local control only allowed
2006-10-13 21:08:25 [---] Listening on port 31416
2006-10-13 21:08:25 [---] Platform changed from  to i686-pc-linux-gnu - resetting projects
2006-10-13 21:08:25 [---] This computer is not attached to any projects
2006-10-13 21:08:25 [---] Visit [http://boinc.berkeley.edu](http://boinc.berkeley.edu) for instructions
2006-10-13 21:08:25 [---] Suspending network activity - running CPU benchmarks
2006-10-13 21:08:27 [---] Running CPU benchmarks
2006-10-13 21:09:26 [---] Benchmark results:
2006-10-13 21:09:26 [---]    Number of CPUs: 2
2006-10-13 21:09:26 [---]    811 floating point MIPS (Whetstone) per CPU
2006-10-13 21:09:26 [---]    2427 integer MIPS (Dhrystone) per CPU
2006-10-13 21:09:26 [---] Finished CPU benchmarks
2006-10-13 21:09:27 [---] Resuming computation
2006-10-13 21:09:27 [---] Rescheduling CPU: Resuming computation
2006-10-13 21:09:27 [---] Resuming network activity 

I have had success using BOINC with Breezy and Dapper, but for some reason the exact same thing is not working in Edgy.  This is especially sad because I was able to boot a live Edgy Xubuntu cd tonight on my Asus P5B but the one thing I built this computer for won't work- unless I use Windows.

It looks to me like all the permissions are ok in the BOINC folder- what am I doing wrong in Edgy that doesn't matter in Breezy or Dapper?

---

### Post by RktMan on 2006-10-14
run_client is a simple shell script.

did you verify that the shell script is doing sensible stuff ?

using the right directory and command for your system ?

secondly, is the 'boinc' executable in the directory where the script says it should be, and is it executable.

can you run it directly ? './boinc' ?

Tony

---

### Post by sheenaramone on 2006-10-15
Could this have something to do with the shell scripts not working?

[https://launchpad.net/distros/ubuntu/+ticket/1932](https://launchpad.net/distros/ubuntu/+ticket/1932)

It says Edgy uses dash instead of bash and that breaks some scripts.  I'll have to ask my coding buddies at BOINC about this and see if they can write some Edgy friendly code.

---

### Post by martalli on 2006-10-22
I read that bug report, but then I went to my terminal.  This is my son's computer, running edubuntu 6.10.  Honestly, I started this out as a dapper machine but have dist-upgraded to edgy through the graphical technique shown at [https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

Here is a clip from the standard gnome-terminal on my son's edgy edubuntu computer:

```
charley@charley-desktop:~$ ps aux | grep dash
charley   5928  0.0  0.2   2796   744 pts/0    R+   08:43   0:00 grep dash
charley@charley-desktop:~$ ps aux | grep bash
charley   5908  4.4  1.2   5656  3284 pts/0    Ss   08:42   0:00 bash
charley   5932  0.0  0.2   2800   744 pts/0    R+   08:43   0:00 grep bash
charley@charley-desktop:~$ 
```

It implies to me that my terminal is running bash, not dash.

Another suggestion  I have would be to edit the script to call bash explicitly.  Disclaimer:  I am not a shell scripting maven...

---

### Post by RAOF on 2006-10-23
> **martalli said:**
> I read that bug report, but then I went to my terminal.  This is my son's computer, running edubuntu 6.10.  Honestly, I started this out as a dapper machine but have dist-upgraded to edgy through the graphical technique shown at [https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

Here is a clip from the standard gnome-terminal on my son's edgy edubuntu computer:

```
charley@charley-desktop:~$ ps aux | grep dash
charley   5928  0.0  0.2   2796   744 pts/0    R+   08:43   0:00 grep dash
charley@charley-desktop:~$ ps aux | grep bash
charley   5908  4.4  1.2   5656  3284 pts/0    Ss   08:42   0:00 bash
charley   5932  0.0  0.2   2800   744 pts/0    R+   08:43   0:00 grep bash
charley@charley-desktop:~$ 
```

It implies to me that my terminal is running bash, not dash.

Another suggestion  I have would be to edit the script to call bash explicitly.  Disclaimer:  I am not a shell scripting maven...

Bash is still used as the interactive-terminal shell, just not to run scripts.  The way to fix a shell-script which breaks with dash is to change the first line of the script, which will be
```

#!/bin/sh

```
To
```

#!/bin/bash

```

---

### Post by ttread on 2007-01-06
I get the same error as the original poster.  I'm using Kubuntu Edgy AMD64 and trying to run the downloaded BOINC, simlar to OP.

I don't think the problem is caused by dash, because the same error occurs when simply typing the command at the shell:

root@ted:/home/ted/Download/Boinc/BOINC# ls -l boinc
-rwxr-xr-x 1 ted ted 1802664 2006-12-04 11:18 boinc
root@ted:/home/ted/Download/Boinc/BOINC# ./boinc
bash: ./boinc: No such file or directory

I thought this might be because boinc is 32-bit, not recognized as an executable in a 64-bit environment.  But then why:

root@ted:/home/ted/Download/Boinc/BOINC# linux32 ./boinc
Cannot execute ./boinc: No such file or directory

What am I missing here?

---

### Post by sheenaramone on 2007-01-13
I got it to work by typing this in terminal

sudo apt-get install ia32-libs

after it finished downloading the libraries, BOINC worked with 64 bit Edgy!

---

