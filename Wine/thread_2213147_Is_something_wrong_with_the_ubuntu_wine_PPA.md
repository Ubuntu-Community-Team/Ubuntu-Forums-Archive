---
title: "Is something wrong with the ubuntu wine PPA?"
date: 2014-03-25
forum: Wine
---

### Post by asmith5416 on 2014-03-25
I've been using wine 1.7 on kubuntu 13.10 for months without any issues. I did an apt-get upgrade today and suddenly wine stopped working. I had not run an update/upgrade in the last week or more.

I attempted to remove and and reinstall it, and I'm getting the following error:

apt-get install wine produces this:
> Some packages could not be installed. This may mean that you haverequested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.


The following information may help to resolve the situation:


The following packages have unmet dependencies:
wine : Depends: 
     wine1.6 but it is not going to be installed or
     wine1.7 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

apt-get install wine1.7 produces this:
> Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 wine1.7 : Depends: wine1.7-i386 (= 1:1.7.14-0ubuntu1~saucy1)
E: Unable to correct problems, you have held broken packages.


Someone else seems to be describing the same issue here:
[http://ubuntuforums.org/showthread.php?t=2212936](http://ubuntuforums.org/showthread.php?t=2212936)

A related discussion is here, also pertaining to the same issue:
[http://forum.winehq.org/viewtopic.php?t=22119&p=92790](http://forum.winehq.org/viewtopic.php?t=22119&p=92790)

Another here:
[http://forum.winehq.org/viewtopic.php?f=8&t=22117](http://forum.winehq.org/viewtopic.php?f=8&t=22117)

All in the last few days...

---

