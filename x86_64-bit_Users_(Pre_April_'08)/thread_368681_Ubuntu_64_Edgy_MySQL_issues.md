---
title: "Ubuntu 64 Edgy MySQL issues"
date: 2007-02-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by Howler9443 on 2007-02-23
Hello everyone,

Recently, I did a fresh install of Ubuntu 64 Edgy on my machine in order to do some development work. I installed JDK 6.0, Eclipse, MyEclipse and MySQL.

However, after updating my system, I can no longer connect to the MySQL server. I get the following message

ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' 

The mysqld.sock file does not exist, I can't start mysql via /etc/init.d/mysql start as I get the above error.

It should be noted that upon bootup (after update which included a newer kernel) I occasionally get a "Failure to initialize HAL".  I'm assuming that this could be the problem.

I dual boot this machine with XP and have the Creative Labs X-fi card. I understand that there are no drivers available for it and thats ok, as I really just want to work on some code. However, I think that since its just sitting there its causing an issue with the startup of HAL and also causing my MySQL error.

I don't seem to have this issue on my laptop that is also running Ubuntu 64 Edgy.

Here is my current hardware list.

Asus P5LD-VM motherboard
Intel Pentium 805 D
2GB DDR2 RAM
WD250GB SATA
WD120GB SATA
nVidia 7900GT PCIe w/256MB
Creative Labs X-Fi Music Extreme
DVD Burner

Has anyone else had a similar issue or know of a fix or workaround for this?

Thanks

---

### Post by kane77 on 2007-02-25
the same happened for me, however the mysql worked fine before and I didn't do anything to it...

however I solved it by running mysqld_safe (I ran it as root...) now it works...

---

### Post by Howler9443 on 2007-02-25
Thanks, I'll give that a shot. :-)

---

### Post by ffxr on 2007-02-27
I am getting the same issue.

the mysql_safe command does not work..

I installed mysql server, and the service starts normally immediately post the install.. but then after a reboot the mysql services wont start..

```
sudo /etc/init.d/mysql start
 * Starting MySQL database server mysqld        [fail]  
```

from my syslog i notice the following..

```
Feb 27 17:39:18 ffxr-desktop mysqld_safe[4921]: started
Feb 27 17:39:18 ffxr-desktop mysqld[4924]: mysqld got signal 4;
Feb 27 17:39:18 ffxr-desktop mysqld[4924]: This could be because you hit a bug. It is also possible that this binary
Feb 27 17:39:18 ffxr-desktop mysqld[4924]: or one of the libraries it was linked against is corrupt, improperly built,
Feb 27 17:39:18 ffxr-desktop mysqld[4924]: or misconfigured. This error can also be caused by malfunctioning hardware.
Feb 27 17:39:18 ffxr-desktop mysqld[4924]: We will try our best to scrape up some info that will hopefully help diagnose
Feb 27 17:39:18 ffxr-desktop mysqld[4924]: the problem, but since we have already crashed, something is definitely wrong
Feb 27 17:39:18 ffxr-desktop mysqld[4924]: and this may fail.
Feb 27 17:39:18 ffxr-desktop mysqld[4924]: 
Feb 27 17:39:18 ffxr-desktop mysqld[4924]: key_buffer_size=0
Feb 27 17:39:18 ffxr-desktop mysqld[4924]: read_buffer_size=131072
Feb 27 17:39:18 ffxr-desktop mysqld[4924]: max_used_connections=0
Feb 27 17:39:18 ffxr-desktop mysqld[4924]: max_connections=100
Feb 27 17:39:18 ffxr-desktop mysqld[4924]: threads_connected=0
Feb 27 17:39:18 ffxr-desktop mysqld[4924]: It is possible that mysqld could use up to 
Feb 27 17:39:18 ffxr-desktop mysqld[4924]: key_buffer_size + (read_buffer_size + sort_buffer_size)*max_connections = 217599 K
Feb 27 17:39:18 ffxr-desktop mysqld[4924]: bytes of memory
Feb 27 17:39:18 ffxr-desktop mysqld[4924]: Hope that's ok; if not, decrease some variables in the equation.
Feb 27 17:39:18 ffxr-desktop mysqld[4924]: 
```


has ANYONE any clue as to whats going on..?

---

### Post by ffxr on 2007-02-27
my signature is from my old rig.. obviously ; )

m setting up a xubuntu amd64 system now [with pentium d 820s), & the 2.6.20 kernel.. and i didnt see this problem in 32bit xubuntu.. 

ta. : )

---

### Post by ffxr on 2007-02-27
i have reasearched a little and did this: 

I delete all the files in /var/lib/mysql, but not the /var/lib/mysql/mysql directory, and then run /etc/init.d/mysql start, it creates the databases again, and mysqld works

but then i reboot and mysqld doesnt start again.. i have'nt really a clue what im essentially doing.. by deleteing them files.. what process is responsible for recreating them? does this look like a permissions problem..? can anyone offer any background at all? 

i dont know if this is an AMD64 issue or a mysql problem.. i just wanna import my amarok collection db..


ve been lookin at this forum.. [http://forums.mysql.com/read.php?11,9689,133714](http://forums.mysql.com/read.php?11,9689,133714)

but m not really any closer to working out what is going on...

---

### Post by Howler9443 on 2007-02-27
Yeah, I just got around to trying mysqld_safe and I can't make it run either. 

This seems like a pretty big bug and I would expect this type of issue to have been found prior to now. It's probably some weird hardware combo issue causing this.

Still no joy.  I'd rather not go to Ubuntu 32 unless I have to.

Anyone have any suggestions? How do we get this kicked up to the gurus at Ubuntu so that they are aware of it?

I would be willing to provide them with just about any type of information they would need. 

Any devs listening? :-)

---

### Post by Howler9443 on 2007-02-27
ffxr, I noticed that we are both running Intel Pentium Ds what is your hardware config? I wonder if we have a few things in common that we look at an perhaps provide feedback to the devs.

---

### Post by ffxr on 2007-02-27
i have  a pentium 820 D with 2gig of RAM on an Abit SG-95 mobo. (& im using the 2.6.20 kernel)
i find it hard to imagine that it would be a hardware problem tho.

The problem is easily re-creatable if someone else wants to help out/check/confirm..

install mysqlserver:

```
 sudo apt-get install mysql-server. 
```

check service is running:

```
 sudo /etc/init.d/mysql status 
```

reboot pc & check service is running:

```
 sudo /etc/init.d/mysql status 
```

the service wont start after the reboot.. does ANYONE have mysql working ? 

I will have another hunt in google tomorrow.

---

### Post by Howler9443 on 2007-02-28
ffxr, one of the reasons that I suspected it was potentially a hardware issue is because this particular box is a dual boot machine that has a Creative Labs X-Fi card, which I know does not have any drivers for it at this time.  I occasionally receive "Failed to initialize HAL" and thought that the X-Fi card was causing this and the MySQL issue. 

It now appears that they are two unrelated issues.

I've downloaded the "Fiesty" DVD image and will try to install from that to see if there is something in there that resolves the issue.

ffxr, are you able to find anything in the logs pertaining to this? Is so which logs? I found nothing in the MySQL logs. In fact they were 0 byte files.

I'm currently running

Intel Pentium D 805
2GB Ram
nVidia 7900GT
2 SATA drives
DVD Burner 
Creative X-Fi Music Extreme
Asus P5LD2-VM

I was wondering if there could have been something in the chipset, but I am using the Intel 945G chipset and yours is the SiS. hmmm.


Looks like the we both have the Pentium D series, 2GB Ram, and Micro-ATX mobos.

Very strange.

---

### Post by ffxr on 2007-02-28
it IS very strange, maybe it is something to do with our entry level CPU's.. i dunno..

there is some mysql related entires but thery are pretty meaningless in \var\log\syslog.


i will try compiling mysql from source later on.. & see if that changes anything..
ll post back.

which distro are you using btw?

---

### Post by Howler9443 on 2007-02-28
Thanks ffxr, I'll keep digging as well and will post back if I find anything.

---

### Post by ffxr on 2007-02-28
i compiled from source... guess what? ............. issue remains... 

I have posted to the mysql forum: [http://forums.mysql.com/read.php?11,142050,142050#msg-142050](http://forums.mysql.com/read.php?11,142050,142050#msg-142050)

lets see if we can get a few ideas from there.. i dont know how to proceed.. ..

---

### Post by Howler9443 on 2007-02-28
Well, at least its consistat. Hopefully you'll hear something back soon. I'll watch the thread as well. 

Thanks!

---

### Post by ffxr on 2007-03-01
can someone pls advise if i should file a bug report about this issue @ Launchpad ubuntu?

---

### Post by ffxr on 2007-03-01
Ok Howler9443, it IS a bug & its been reported to launcpad a couple of times & it is related to our Pentium chips.. there is  a workaround & i will try this later.. hopefully this is the solution to my final problem in migrating to AMD64.

the bug report is here:
[https://launchpad.net/ubuntu/+source/gcc-4.1/+bug/66702](https://launchpad.net/ubuntu/+source/gcc-4.1/+bug/66702)

---

### Post by ffxr on 2007-03-01
ok i have got it working... 

enable the edgy-proposed repo in your software sources.

remove all of the mysql you have installed now including any my.conf files & any other mysql residue you can find ( i had to remove mysql-common & amarok as well because i was getting a new error after installing ..)

sudo apt-get install mysql-server

your probably better disabling the proposed repo afterwards..

if you need any clarification or have problems, shout back..

---

### Post by Howler9443 on 2007-03-01
ffxr,

Thanks for the info. Its good to know that this is a known bug and is being addressed.  I stumbled across the resolution as well, though it was more like taking a sledgehammer to a finishing tac. I pulled "Fiesty Fawn" HERD 5 and installed it.

I then installed JDK 6.0 and MySQL, I was able to get to MySQL via the command line. I rebooted to verify that the issue was taken care of. It was. It seems to work fine at this point under FF HERD 5.  

Is it possible that whatever glitch caused our MySQL issues was addressed in the kernel update or was this strictly a MySQL issue?

Thanks for the heads up on this issue. Keep me posted and I'll do the same!

---

### Post by envis on 2007-04-01
can anyone help me find where to change the max_connections parameter for mysql on ubuntu 6.10 for AMD64

it seems to be set at a hundred by default and i really need to boost that number but cant find where i been trying to find it for a while...

anyone would happen to know?

---

### Post by envis on 2007-04-01
hmm.. nevermind... i seem to have been able to google the answer finally...



[http://unix.derkeiler.com/Mailing-Lists/FreeBSD/newbies/2004-05/0075.html](http://unix.derkeiler.com/Mailing-Lists/FreeBSD/newbies/2004-05/0075.html)

If the option isn't in my.cnf already then just add under the [mysqld]
section:

set-variable = max_connections=250

or however many you want.

---

