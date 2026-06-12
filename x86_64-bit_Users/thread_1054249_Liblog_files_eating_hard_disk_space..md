---
title: "Lib/log files eating hard disk space."
date: 2009-01-29
forum: x86 64-bit Users
---

### Post by tona_107 on 2009-01-29
Hi,
 I'm running ubuntu 8.10 amd64 on my HP intel 2.26ghz dual core processor, 320gb hdd and 4gb ram. 

My main problem is that when I dual booted ubuntu onto my laptop, I had vista already installed, so I only set aside 20GB of hard disk space for ubuntu, which seems like more than enough to me. What's going on is that it says I have used all my space and only have one GB left, when the only thing I have on my computer are word files and necessary installs like flash player, compiz, avant, etc.

When trying to hunt down what was using all my space, first I checked out the disk usage analyzer (some pics from here in):

theres my hdd with 1/19 gb remaining
[IMG]http://i282.photobucket.com/albums/kk272/tona_107/Screenshot-DiskUsageAnalyzer.png[/IMG]

here's a breakdown of my home folder, showing that it's not using very much at all

[IMG]http://i282.photobucket.com/albums/kk272/tona_107/Screenshot-DiskUsageAnalyzer-1.png[/IMG]

here's my filesystem, now we can see that all the space is being used in the folder: /var

[IMG]http://i282.photobucket.com/albums/kk272/tona_107/Screenshot-DiskUsageAnalyzer-2.png[/IMG]

looking closer now we see that it's all in /var/log

[IMG]http://i282.photobucket.com/albums/kk272/tona_107/Screenshot-DiskUsageAnalyzer-3.png[/IMG]

and now we see that it's all being used by files inside the log folder

[IMG]http://i282.photobucket.com/albums/kk272/tona_107/Screenshot-DiskUsageAnalyzer-4.png[/IMG]

So I browsed my computer looking for this infamous log folder and it indeed was the one eating up all the space:

[IMG]http://i282.photobucket.com/albums/kk272/tona_107/Screenshot-logProperties.png[/IMG]

keep in mind that I am good with computers, but I'm no hacking specialist or anything like that, so I'm not very familiar with the intense inner runnings of computers, like, advanced dosprompt/terminal functions or the system folders. I don't know what the log files are, I'd just assume they are a log of the system activity for something or other, but I don't see why they take up 14 GB, anyone have any ideas what's going on and what I can do? I'll leave you finally with a picture of all the files inside the "/var/log".

[IMG]http://i282.photobucket.com/albums/kk272/tona_107/Screenshot-log-FileBrowser.png[/IMG]

thanks in advance.

---

### Post by dagriff on 2009-01-29
The contents of /var/log are indeed log files. 

14.8Gb is a lot of logs though.

To compare, my system has 53Mb of logs, of which 40Mb are from the VMware server I run for testing installers.

The program logrotate compresses old logs, and deletes even older logs, which you can see is working from the fact you have 

messages
messages.0
messages.1.gz etc

Can you see which of your logs are largest, and have a look at them. Vast log files can be indicative of a deeper problem.

Once you've found what is logging excessively, you will either need to

 a) Sort out the problem it is complaining about
 b) Tell the program responsible to log less
 c) Tell logrotate to keep less archived logs.
 d) Increase the disk space for /var/log

---

### Post by tona_107 on 2009-01-29
> **dagriff said:**
> The contents of /var/log are indeed log files. 

14.8Gb is a lot of logs though.

To compare, my system has 53Mb of logs, of which 40Mb are from the VMware server I run for testing installers.

The program logrotate compresses old logs, and deletes even older logs, which you can see is working from the fact you have 

messages
messages.0
messages.1.gz etc

Can you see which of your logs are largest, and have a look at them. Vast log files can be indicative of a deeper problem.

Once you've found what is logging excessively, you will either need to

 a) Sort out the problem it is complaining about
 b) Tell the program responsible to log less
 c) Tell logrotate to keep less archived logs.
 d) Increase the disk space for /var/log

Thanks a bunch for the help.
The largest files are:
kern.log.0 (4.7GB)
syslog.0 (4.6GB)
messages.0 (4.3GB)

there are also gz files for those ones that are a couple hundred mb as well.

I don't know what to do from here.

Thanks again.

---

### Post by dagriff on 2009-01-29
> **tona_107 said:**
> Thanks a bunch for the help.
The largest files are:
kern.log.0 (4.7GB)
syslog.0 (4.6GB)
messages.0 (4.3GB)

there are also gz files for those ones that are a couple hundred mb as well.

I don't know what to do from here.

Thanks again.

That's interesting that the first set of rotated logs are huge, but you don't mention the live ones being too big. The live ones have no extension, the rotated ones get .0 then .1 etc appended.

Can you actually take a look inside one of those files?

If you open a terminal, and first of all type

```

less /var/log/kern.log

```

Ideally you will something logging vast quantities of information, and finding out what that something is (or was) is the first step towards fixing it.

---

### Post by tona_107 on 2009-01-29
> **dagriff said:**
> That's interesting that the first set of rotated logs are huge, but you don't mention the live ones being too big. The live ones have no extension, the rotated ones get .0 then .1 etc appended.

Can you actually take a look inside one of those files?

If you open a terminal, and first of all type

```

less /var/log/kern.log

```

Ideally you will something logging vast quantities of information, and finding out what that something is (or was) is the first step towards fixing it.

I don't even have enough space to save a screenshot but this is what the terminal said when i typed it in:

Jan 28 11:07:52 daniel-laptop kernel: [ 2289.150343] wlan0: authenticate with AP 00:15:70:43:0d:ac
Jan 28 11:07:52 daniel-laptop kernel: [ 2289.155412] wlan0: authenticated
Jan 28 11:07:52 daniel-laptop kernel: [ 2289.155423] wlan0: associate with AP 00:15:70:43:0d:ac
Jan 28 11:07:52 daniel-laptop kernel: [ 2289.166380] wlan0: RX ReassocResp from 00:15:70:43:0d:ac (capab=0x401 status=0 aid=5)
Jan 28 11:07:52 daniel-laptop kernel: [ 2289.166390] wlan0: associated
Jan 28 11:19:52 daniel-laptop kernel: [ 3009.238943] wlan0: authenticate with AP 00:a0:f8:e9:3f:44
Jan 28 11:19:52 daniel-laptop kernel: [ 3009.240321] wlan0: authenticate with AP 00:a0:f8:e9:3f:44
Jan 28 11:19:53 daniel-laptop kernel: [ 3009.440166] wlan0: authenticate with AP 00:a0:f8:e9:3f:44
Jan 28 11:19:53 daniel-laptop kernel: [ 3009.640585] wlan0: authenticate with AP 00:a0:f8:e9:3f:44
Jan 28 11:19:53 daniel-laptop kernel: [ 3009.840124] wlan0: authentication with AP 00:a0:f8:e9:3f:44 timed out
Jan 28 11:20:04 daniel-laptop kernel: [ 3020.945449] wlan0: authenticate with AP 00:a0:f8:e9:3f:44
Jan 28 11:20:04 daniel-laptop kernel: [ 3020.945936] wlan0: authenticate with AP 00:a0:f8:e9:3f:44
Jan 28 11:20:04 daniel-laptop kernel: [ 3021.144125] wlan0: authenticate with AP 00:a0:f8:e9:3f:44
Jan 28 11:20:05 daniel-laptop kernel: [ 3021.344067] wlan0: authenticate with AP 00:a0:f8:e9:3f:44

i don't know what this means, but thanks again for all the help.

---

### Post by tona_107 on 2009-01-29
I made the same thread in the linux forums, and by zipping the logs I reduced the sizes by a lot, but I feel like this is a band-aid solution.
heres a link to the other thread, [http://www.linuxforums.org/forum/ubuntu-help/139487-log-files-eating-hard-disk-space.html#post663567](http://www.linuxforums.org/forum/ubuntu-help/139487-log-files-eating-hard-disk-space.html#post663567) .

---

