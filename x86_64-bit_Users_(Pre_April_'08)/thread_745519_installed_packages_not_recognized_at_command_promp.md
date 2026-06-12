---
title: "installed packages not recognized at command prompt"
date: 2008-04-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by griztown on 2008-04-04
I downloaded java  j2sdk1.4.2_05.linuxAMD64.tgz .  After running tar -xzvf  j2sdk1.4.2_05.linuxAMD64.tgz it created a directory bin under j2sdk1.4.2_05.  In that directory are listed all the executables.  When I try and execute them I get 'No such file or directory'.  It makes no sense.  I've tried playing around with different permissions, owners, groups, sudo, su, whatever.  When I ls it shows it but when I try and execute it says it isn't there.  Very bizarre!  Anybody have any ideas?

I downloaded this from the OpenFOAM sourceforge project website.

Thanks!
Ted

---

### Post by mikewhatever on 2008-04-04
Have you cd'ed to that directory? Your terminal prompt should look like this: j2sdk1.4.2_05~$. If not try <cd j2sdk1.4.2_05>.

---

### Post by griztown on 2008-04-04
Yes, it is in my path so I've tried it outside the directory which didn't work.  I then cd'd into the directory and tried it there './java' and same result.  I've add this problem with other packages so I feel like it might be a larger system problem though it works fine with other programs.

Ted

---

### Post by EnkiduinNZ on 2008-04-05
> **griztown said:**
> Yes, it is in my path so I've tried it outside the directory which didn't work.  I then cd'd into the directory and tried it there './java' and same result.  I've add this problem with other packages so I feel like it might be a larger system problem though it works fine with other programs.

1) Change to the directory and run the ls -l command and post it here.

2) Type 'which java' and see if you get anything.

Cheers,

Cliff

---

### Post by linuxbeatswin on 2008-04-05
I have the same problem, so I 'm following this thread closely.

---

### Post by EnkiduinNZ on 2008-04-05
> **griztown said:**
> I downloaded java  j2sdk1.4.2_05.linuxAMD64.tgz .  After running tar -xzvf  j2sdk1.4.2_05.linuxAMD64.tgz it created a directory bin under j2sdk1.4.2_05.  In that directory are listed all the executables.  When I try and execute them I get 'No such file or directory'.  It makes no sense.  I've tried playing around with different permissions, owners, groups, sudo, su, whatever.  When I ls it shows it but when I try and execute it says it isn't there.  Very bizarre!  Anybody have any ideas? I downloaded this from the OpenFOAM sourceforge project website.


The install instructions say to firstly untar it, which should create a single bin file. Then you change the permissions on the bin file so that you can execute it, and then you run it. Did you do these three steps?

Cheers,

Cliff

---

### Post by griztown on 2008-04-07
All,

Sorry for the delay, the computer I'm having the problems with is at work so it had to wait to Monday.  Here is the results for 'ls -l' and 'which java'.

> theodore@theodore-desktop:~/OpenFOAM/linux64/j2sdk1.4.2_05/bin$ pwd
/home/theodore/OpenFOAM/linux64/j2sdk1.4.2_05/bin
theodore@theodore-desktop:~/OpenFOAM/linux64/j2sdk1.4.2_05/bin$ ls -l
total 1732
-rwxr-xr-x 1 theodore theodore 66420 2004-06-03 21:48 appletviewer
-rwxr-xr-x 1 theodore theodore 66156 2004-06-03 21:51 extcheck
-rwxr-xr-x 1 theodore theodore  1080 2004-06-03 22:02 HtmlConverter
-rwxr-xr-x 1 theodore theodore 66188 2004-06-03 21:37 idlj
-rwxr-xr-x 1 theodore theodore 66156 2004-06-03 21:40 jar
-rwxr-xr-x 1 theodore theodore 66156 2004-06-03 21:39 jarsigner
-rwxr-xr-x 1 theodore theodore 64940 2004-06-03 21:32 java
-rwxr-xr-x 1 theodore theodore 66156 2004-06-03 21:32 javac
-rwxr-xr-x 1 theodore theodore 66156 2004-06-03 21:33 javadoc
-rwxr-xr-x 1 theodore theodore 66156 2004-06-03 21:33 javah
-rwxr-xr-x 1 theodore theodore 66156 2004-06-03 21:49 javap
-r-xr-xr-x 1 theodore theodore  1789 2004-06-03 21:48 java-rmi.cgi
-rwxr-xr-x 1 theodore theodore 66156 2004-06-03 21:52 jdb
-rwxr-xr-x 1 theodore theodore 66156 2004-06-03 21:39 keytool
-rwxr-xr-x 1 theodore theodore 66188 2004-06-03 21:39 kinit
-rwxr-xr-x 1 theodore theodore 66188 2004-06-03 21:39 klist
-rwxr-xr-x 1 theodore theodore 66188 2004-06-03 21:39 ktab
-rwxr-xr-x 1 theodore theodore 66156 2004-06-03 21:49 native2ascii
-rwxr-xr-x 1 theodore theodore 66380 2004-06-03 21:51 orbd
-rwxr-xr-x 1 theodore theodore 66420 2004-06-03 21:39 policytool
-rwxr-xr-x 1 theodore theodore 66156 2004-06-03 21:48 rmic
-rwxr-xr-x 1 theodore theodore 66156 2004-06-03 21:49 rmid
-rwxr-xr-x 1 theodore theodore 66156 2004-06-03 21:48 rmiregistry
-rwxr-xr-x 1 theodore theodore 66156 2004-06-03 21:49 serialver
-rwxr-xr-x 1 theodore theodore 66188 2004-06-03 21:51 servertool
-rwxr-xr-x 1 theodore theodore 66188 2004-06-03 21:51 tnameserv
theodore@theodore-desktop:~/OpenFOAM/linux64/j2sdk1.4.2_05/bin$ which java
/home/theodore/OpenFOAM/linux64/j2sdk1.4.2_05/bin/java
theodore@theodore-desktop:~/OpenFOAM/linux64/j2sdk1.4.2_05/bin$ java
bash: /home/theodore/OpenFOAM/linux64/j2sdk1.4.2_05/bin/java: No such file or directory
theodore@theodore-desktop:~/OpenFOAM/linux64/j2sdk1.4.2_05/bin$ ./java
bash: ./java: No such file or directory


As you can see, the permissions look okay.  The path is okay.  When I type 'java' I get 'No such file or directory'.  

Thanks for all the help.

---

### Post by griztown on 2008-04-07
As a follow up, I've been trying different things with the executable.  I can move it, rename it, copy it.  Open it with gvim and it shows funky binary characters.  I can change permissions and try and execute it and it tells me 'Permission denied'.  I can do all sorts of things but the moment I try and execute it (with the right permissions), I get "No such file or directory".  

Crazy.

---

### Post by griztown on 2008-04-09
> **EnkiduinNZ said:**
> The install instructions say to firstly untar it, which should create a single bin file. Then you change the permissions on the bin file so that you can execute it, and then you run it. Did you do these three steps?


I did not do that initially since it had the correct permissions but I have tried changing the permissions and executing it and it hasn't worked.  So yes, I've tried them, but in a more round about way.

By the way, when I untar the file it does not create a single bin file.  I creates numerous directories and files.  Most of which are accessible but none of which are executable, which is the problem.

---

### Post by capeto on 2008-04-13
Hi,

   I had the same problem trying to execute some cgi scripts on a 64bits Dapper server.

   I solved it installing the package lsb-core. Read this post:

   [http://ubuntuforums.org/showthread.php?t=422767](http://ubuntuforums.org/showthread.php?t=422767)

   Hope this helps.

Regards,
Capeto

---

