---
title: "Synaptic/Automatix install Update error"
date: 2007-05-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by j0eb0b on 2007-05-22
Recently when I try and update either with Automatix2 or Synaptic, I get tthis error.  What does it means?  

"E: clamav-base: subprocess post-installation script returned error exit status 1"

I'm not sure what the E: drive is on ubuntu.  On the Windows XP side of this machine there are numerous drives (CD, DVD and a whole lot of USB drives) .  What is he looking for?

There is frequently another error screen that i haven't been able to copy that calls this a "fatal apt-get error".  This particulare instances of the error came from trying to download the 1.4 Mozilla Java plug-in via Synaptic.

On a separate but related theme, how do you take a screen shot in Firefox/Swiftweasel?

Joe

---

### Post by RAOF on 2007-05-23
Firstly: The "E: *foo*" line is short hand for "Error: *foo*".  It's not referring to the E: drive, since linux doesn't map drives in that way.

Secondly:  From the #ubuntu IRC channel - 
[quote=ubotu]Automatix2 is a script that tries to install some software, and often fails and breaks systems. We don't provide support for it, and we strongly discourage its use. Problems caused by Automatix are often hard to track and solve, and it might sometimes be easier to !install a fresh copy of Ubuntu. See also !WorksForMe
[/quote]
Seriously.  It's entirely possible that your apt error is caused by automatix being crazy and killing dpkg.  **Don't use automatix**.

---

### Post by shad0w_walker on 2007-05-23
This looks like a package failed during install (DPKG does like having part installed programs floating around so it prevents you doing anything else til it is fixed)

If you go into synaptic and find the custom filters button then select broken from the side list, there should be that package visible, just right click and select remove. That should uninstall the broken package and sort you out.

---

### Post by j0eb0b on 2007-05-23
RAOF/Shad0w_walker,

Thanks for your coments, perhaps Automatix has comprised my system.  I will refrain from calling it in the future. Hopefuly, i will not have to reinstall my system.  When I look at the custom filters tab in Synaptic, it tells me that no packages are broken even though something obviously is.  In spite of the error messsage  I am getting, after running Synaptic, the updates i am trying to download seem to be working.  RAOF you are right that it apears that Automatix has caused a problem with my installer routine.  I am a Linux novice (in spite of 2 years of playing with various distributions)and was usng this script to help me install basic multi-media infrastruture that I am not clever enough to install manually  If I can capture a meaningfull continuing error I will post it.  In the meantime, I will  to try and muddle through  configuring my Ubuntu desktop. 

Thanks for your help.

---

### Post by PriceChild on 2007-05-23
try a ```
sudo apt-get -f install
```and see if any packages are left to be fixed.

---

### Post by arnieboy on 2007-05-24
joebob:
           The error that you got on Automatix is because of a bug in the **clamav-base** package and has **nothing to do with either dpkg or Automatix**. The bug report has been cited on the Automatix Advisories page here:
[http://www.getautomatix.com/wiki/index.php?title=Advisories#Ubuntu_7.04_.28all_versions.29](http://www.getautomatix.com/wiki/index.php?title=Advisories#Ubuntu_7.04_.28all_versions.29)
and the real bug report can be found here:
[https://bugs.launchpad.net/ubuntu/+source/clamav/+bug/39853](https://bugs.launchpad.net/ubuntu/+source/clamav/+bug/39853)
This bug sometimes prevents the clean installation of clamav and its associated dependencies because of issues with some post/pre installation scripts in the debs themselves. The only way to solve this issue till now has been to try and install the clamav packages more than once which resolves these post-installation errors. You can try doing it from Automatix (and see how it goes). Unfortunately, Ubuntu MOTU has not been able to resolve this bug in the past two months.

-Arnie
Automatix Team Lead.

---

### Post by j0eb0b on 2007-05-24
Arnieboy,

Thanks for this information.  Again, please pardon my ignorance.  When I run Automatix what package am I trying to re-install that needs clavmag?  To the best of my recollection, this problem began when I tried to install a virus scanner from the utilies menu on Automatix.  I know that viruses are not thought to be a problem in a Linux world but I am dragging my Microsoft ball and chain with me.  If this virus scanner is the problem, how can i remove it since i don't see it as a broken package in Synaptic?

---

### Post by j0eb0b on 2007-05-24
Here is better information regarding my problem:

j0eb0b@j0eb0b-desktop:~$ sudo apt-get -f install
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up clamav-base (0.90.2-0ubuntu1) ...
chown: cannot access `/var/run/clamav': No such file or directory
dpkg: error processing clamav-base (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 clamav-base
E: Sub-process /usr/bin/dpkg returned an error code (1)
j0eb0b@j0eb0b-desktop:~$ 

how can i make this go away?

Thanks,

Joe

---

### Post by arnieboy on 2007-05-24
> **j0eb0b said:**
> Here is better information regarding my problem:

j0eb0b@j0eb0b-desktop:~$ sudo apt-get -f install
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up clamav-base (0.90.2-0ubuntu1) ...
chown: cannot access `/var/run/clamav': No such file or directory
dpkg: error processing clamav-base (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 clamav-base
E: Sub-process /usr/bin/dpkg returned an error code (1)
j0eb0b@j0eb0b-desktop:~$ 

how can i make this go away?

Thanks,

Joe

Please do the following:
```
sudo rm -f /var/lib/dpkg/info/clamav-base.postinst
sudo apt-get -f install
```
and paste the results here

---

### Post by j0eb0b on 2007-05-24
many thanks for your help;  Results quoted below:

0eb0b@j0eb0b-desktop:~$ sudo rm -f /var/lib/dpkg/info/clamav-base.postinst
Password:
Sorry, try again.
Password:
j0eb0b@j0eb0b-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up clamav-base (0.90.2-0ubuntu1) ...
j0eb0b@j0eb0b-desktop:~$

---

### Post by arnieboy on 2007-05-24
> **j0eb0b said:**
> many thanks for your help;  Results quoted below:

0eb0b@j0eb0b-desktop:~$ sudo rm -f /var/lib/dpkg/info/clamav-base.postinst
Password:
Sorry, try again.
Password:
j0eb0b@j0eb0b-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up clamav-base (0.90.2-0ubuntu1) ...
j0eb0b@j0eb0b-desktop:~$

good. now you are all set. Synaptic, apt and Automatix will now work fine.

---

### Post by j0eb0b on 2007-05-25
Ok,

I'll give it a try this evening and post my results.

Thanks for the help.

Joe

---

### Post by j0eb0b on 2007-05-25
Arnieboy,

I ran updates successfully with both Synaptic and Automatix tonight with no errors.  Thanks for your support.

Joe

---

