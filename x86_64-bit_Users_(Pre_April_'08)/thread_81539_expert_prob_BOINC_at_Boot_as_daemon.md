---
title: "expert prob: BOINC at Boot as daemon"
date: 2005-10-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by bonzodog on 2005-10-24
Hi, I have a relatively complicated problem;
I need someone to explain to me how Ubuntu's unique init script processes work. I need to do this as I have to add a script to start an extra process at boot time, namely BOINC. I want the BOINC manager to start as a daemon process, and there is a script for unices that is known to work on slackware, redhat and mandrake. But looking at the /etc/init.d directory confused me as I was trying to follow it's init path for boot-up and shut-down. 
So, is there anyone here who REALLY knows ubuntu's nut-and-bolts, or am I gonna have to dismantle it myself and attempt to work out the init process for the respective runlevels?
I know that for some strange reason, the init/runlevels on Ubuntu are mixed up, so that you don't get the conventional;
1= single user
3= multi-user, console mode
4/5 =multi user X
anyone installed BOINC on Ubuntu yet, as a daemon?

---

### Post by RAOF on 2005-10-24
Yup, I've got BOINC running as a daemon.

Basically, the /etc/init.d directory contains a whole bunch of init scripts - I think it actually contains all of them.  There is no startup - shutdown path there :).  A system of symlinks is set up to them under the appropriate rc.whatever directories.  **That** can be accomplished automatically by using rcconf (apt-get install rcconf).

So, basically, what you need to do is put the boincd script in /etc/init.d, run rcconf, and select the boincd script for startup.

Oh, and I can post you my script if you can't get one of your own.  I've done some uninformed hacking on it though, it may not work for you :)

---

### Post by bonzodog on 2005-10-25
It's ok, I have it solved :)
I downloaded and installed BOINC off the debian site for it, and it runs automatically as a daemon. Just sorted out the glitch with the 64 bit seti thing as well...

---

### Post by HankB on 2005-11-01
Where did you find your boinc client? I've got 4.32 from [http://www.lb.shuttle.de/apastron/boincDown.shtml#gnua64](http://www.lb.shuttle.de/apastron/boincDown.shtml#gnua64) and cannot figure out how to specify the key. According to the usage message, it should prompt me for the URL and key, but it doesn't. I can supply the URL on the command line but never asks for the key. Instead it just tries to log in without it.

thanks,
hank

---

### Post by veehell on 2005-12-03
Hi 
i used [http://boinc.berkeley.edu/download.php](http://boinc.berkeley.edu/download.php) and download official clien/manager.
It is not acting as a daemon, it runs normally under my profile.

Coz i had problems with synaptic to instal boinc/seti packages. (Also the init.d script provided by the 3rd parties from the [3rd party executalbes ]("http://boinc.berkeley.edu/download_other.php")need to be edited for sure)

The official manager connect via GTK gui to any runned "boinc" procces. Really nice, it looks like the window's client, also graphics run pretty good (only for einstein@home, seti is not working at all).

So maybe the links help you, as they help to me to run boinc correctly ;)

---

### Post by eldiabolosk on 2006-11-12
Hi,

How did you get it working? I am currently running boinc 5.4.9 before there was boinc I used the seti at home client to run from the cron table and ever since cant get it working and especialy on UBUNTU, anybody knows how? please send me detailed instructions, please

Thank you ed.

---

