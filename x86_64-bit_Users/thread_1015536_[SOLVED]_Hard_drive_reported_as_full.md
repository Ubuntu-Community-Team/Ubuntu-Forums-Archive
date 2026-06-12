---
title: "[SOLVED] Hard drive reported as full"
date: 2008-12-18
forum: x86 64-bit Users
---

### Post by piemaster89 on 2008-12-18
I have a 100GB hard drive that I just performed a clean install of 8.10 on last night. I installed a couple of programs and downloaded a couple of videos in that time but suddenly it's telling me the hard drive has 0 free bytes left. I didn't download 100GB worth of data so something went terribly wrong. (At most it was 20GB of data.) I ran 
```

sudo apt-get clean
sudo apt-get autoclean

```

This got me back 499MB of free space. I've searched for this problem in the Ubuntu forums already and have found similar cases where the hard drive was close to full. However, I could not find a solution.

This is the output of "df -BM"
```

$ df -BM
Filesystem           1M-blocks      Used Available Use% Mounted on
/dev/sda1               90036M    84964M      499M 100% /
tmpfs                     984M        0M      984M   0% /lib/init/rw
varrun                    984M        1M      984M   1% /var/run
varlock                   984M        0M      984M   0% /var/lock
udev                      984M        3M      982M   1% /dev
tmpfs                     984M        1M      984M   1% /dev/shm
lrm                       984M        3M      982M   1% /lib/modules/2.6.27-9-generic/volatile
overflow                    1M        1M        1M   4% /tmp

```

Thanks in advance for any replies!

EDIT:
I realized after posting this that the USED and AVAILABLE numbers don't add up to the SIZE for /dev/sda1.

I ran Disk Usage Analyzer and it turns out that all the space is being used in /var/log. Specifically syslog, syslog.0, kern.log, kern.log.0, messages, and messages.0 are all taking up roughly about 10GB each. I'm pretty sure this isn't normal. Any ideas?

---

### Post by paxmark1 on 2008-12-18
man du


after reading that start du in various folders.  ~/tmp  /etc etc.

In Kubuntu 8.04, the nepomuk crap had a glitch that almost filled up my 40 gb hdd on a sff (and others on the forum) with no real bug fix ever given other than to aptitude purge the swine rogue program.  But you shoud not have that in Ubuntu.

---

### Post by hambone79 on 2008-12-18
> I realized after posting this that the USED and AVAILABLE numbers don't add up to the SIZE for /dev/sda1.

FYI...the numbers don't add up to 100% because the the partition has a certain amount of space reserved for the root user. This reserved space is part of what allows the system to continue running even after the hard drive space is filled up.

You can tweak this number by using the tunefs program:

```

sudo tunefs -m 2 /dev/sda1 

```

In that example, "2" is the percentage of free space to reserve on the drive.

---

### Post by piemaster89 on 2008-12-18
Thanks hambone, that answers one of my questions.

So I went ahead and removed those files I stated earlier. I haven't rebooted yet but I hope this doesn't cause any errors of any sort.

---

### Post by piemaster89 on 2008-12-30
Turns out this was a bug in the 2.6.27-8 and 2.6.27-9 kernels where 'messages' 'syslog' and 'kern.log' in /var/log/ would keep growing. This should be fixed in 2.6.27-10.

---

### Post by KrazyPenguin on 2009-01-11
same problem here:  many things stopped working, i was wondering what was going on.

So i got pissed and started to reinstall hardy, then came across this tool: xdiskusage 
I installed by synaptic and it gave me an output of my other partition, which was basically showing me half my disk space was being used by var/log.  It is 4.6GB big!!!!!

I will delete and retry.

Wish me luck!!

;-)

---

