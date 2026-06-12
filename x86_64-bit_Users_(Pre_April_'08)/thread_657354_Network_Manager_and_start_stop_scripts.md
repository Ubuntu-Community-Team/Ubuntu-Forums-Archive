---
title: "Network Manager and start stop scripts"
date: 2008-01-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by moofoo on 2008-01-03
On shutdown or reboot I get the following message:
```
NetworkManager: <WARN>  nm_signal_handler (): Caught Signal 15, shutting down normally
NetworkManager: <info>  Caught terminal signal
NetworkManager: <debug> [1199654771.356623] nm_print_open_sock (): Open Sockets List
NetworkManager: <debug> [1199654771.981488] nm_print_open_sock (): Open Sockets List Done
NetworkManager: <info>  Deactivating device eth0
NetworkManager: <WARN>  nm_hal_deinit(): libhal shutdown failed - Connection is closed
NetworkManager: nm_dbus_signal_device_status_change: assertion `sb_data->dbus_connection' failed
NetworkManager: nm_dbus_signal_device_status_change: assertion `sb_data->dbus_connection' failed
```

I did a bunch of digging, but I'm afraid I don't have the experience to to understand my findings and really need some help.

I found that networking is set for run level S for start, and levels 0 and 6 for stop (shutdown, reboot).
```

:/etc$ ls -o rc*|grep network
lrwxrwxrwx 1 root  20 2008-01-03 12:35 K60networking -> ../init.d/networking
lrwxrwxrwx 1 root  20 2008-01-03 12:35 K60networking -> ../init.d/networking
lrwxrwxrwx 1 root  20 2007-12-31 17:28 S40networking -> ../init.d/networking

```

Ok, found the networking script. The script seems to not define or call any functions that actually stop, start, or restart networking for some reason.
```
sudo gedit /etc/init.d/networking
```

Running it gives formated output for usplash and console, but does nothing
```
sudo /etc/init.d/networking stop
```

So I dig further, and I find...
```

$ ls -o /etc/dbus-1/event.d/
total 12
-rwxr-xr-x 1 root 1766 2007-10-15 13:55 25NetworkManager
-rwxr-xr-x 1 root 1684 2007-10-15 13:55 26NetworkManagerDispatcher
-rwxr-xr-x 1 root 1892 2007-09-17 07:59 70system-tools-backends

```

Looking in both ***25NetworkManager*** and ***26NetworkManagerDispatcher***, I see they have defined stop and start functions, but very plain string formating on the ouput.

Running the following actually will kill networking, and does prevent the shutdown messages from appearing...
```
sudo /etc/dbus-1/event.d/25NetworkManager stop
```

So, I've found the script file that can actually stop/start networking.  I can run it manually before shutdown or reboot to prevent the message, but I want to have the system do it automatically, and if possible, properly.  Now, I'm not sure how to actually make networking stop properly on shutdown and reboot.

So far I have tried defining the stop function in */etc/init.d/networking* using */etc/dbus-1/event.d/25NetworkManager* as a reference.

Now when I run...
```
sudo /etc/init.d/networking stop
```
...networking actually does stop just like when running *25NetworkManager stop*. This also prevents the fail messages in the console on shutdown.  Now with that, I expect that K60networking found in runtime 0 and 6 will still call */etc/init.d/networking stop* as usual with it's pretty formatting, but also actually shutdown network manager.  Unfortunately this is not the case, and am left without any more ideas.  Please, and help is appreciated.  I'm soooooo stuck.

Gutsy 7.10 AMD64 single core.
MB K8T Neo (MS-6702 Version 1.1 G52-M6702X7)
Power Management is on in the BIOS and works within Ubuntu.
K8T800 chipset
2 GB RAM
Onboard network card - 1 wired network connection, no wiFi.
ATIX800
Onboard sound.
8 total USB ports.

---

### Post by moofoo on 2008-01-06
Try 2.  I dig deeper...

Looking at the runlevels 0 and 6 (shutdown, reboot) 
```
cd /etc/rc0.d
or
cd /etc/rc6.d
```

It seems k60networking is numberred 60, which is 3rd from last to run.  So I figured I would try making it the first thing to run at shutdown and reboot.  Based on the idea that a script starting with "K" will be run with the "stop" command, I try making my own symbolic link, but number this one 00.
```
cd /etc/rc0.d
sudo ln -s ../init.d/networking K00mynetworking

:/etc/rc0.d$ ls -o | grep network
lrwxrwxrwx 1 root  20 2008-01-06 13:44 K00mynetworking -> ../init.d/networking
lrwxrwxrwx 1 root  20 2008-01-03 12:35 K60networking -> ../init.d/networking
```

Did the same for rc6.d.  Testing my link by running...
```
sudo /etc/rc0.d/K00mynetworking stop
```

Sure enough that does stop networking.  Ok, startup networking again and try a few reboots and shutdowns.  Still get error messages for Network Manager on reboot and shutdown.

Here's a video guide I found.  Seems I'm on the right path, but I must be missing something key.
```
http://www.youtube.com/watch?v=d39izaupvEg
```

---

### Post by moofoo on 2008-01-06
Finally was able to get a full snapshot of the shutdown message.  The first post has been updated with the full message.

The mentioning of dbus makes me think now it has more to do with how the GUI is shutting down.  So I tried restarting from the log in screen (before X is loaded), and sure enough, the network manager messages did not show up.  Restarting from the GUI, how ever still produces the above errors messages.

What is dbus and/or gdm doing at shutdown and reboot that the subsystem is not doing?

---

### Post by Fisslefink on 2008-01-12
I see this too on every shutdown.  Kudos on the extremely thorough post of your efforts -- I'm stumped too, but I can say that this problem is not unique to you.

I'll try stopping the Network Manager as you did to see if it prevents the messages.  If so, we can add that command to an existing script in /etc/rc6.d or make our own little script.

---

### Post by Fisslefink on 2008-01-12
Looks like some good clues here. but I don't have time to follow them:

[http://ubuntuforums.org/archive/index.php/t-588496.html](http://ubuntuforums.org/archive/index.php/t-588496.html)

---

### Post by moofoo on 2008-01-15
Thanks for the heads up on that forum post.  I think I may have seen it my searchings, but glossed over it.  When I have some time later today, I'll try all the suggested solutions in that thread and report back with my findings.

PS:   I'm doing this testing on my secondary computer, so its not an issue for me to reinstall.  Sooo, if anyone has any ideas they feel might be too risking to suggest, I say don't sweat it.  I can test this issue into the ground without fear of losing anything.

---

### Post by koveitan on 2008-02-01
Hi
i have the same beavior, i cannot restart or shutdown my machine properly
did you find a solution ?
if not a bug must be opened
Note: i am on ubuntu 7.10 on the previous versions that did not happen
my specs:
thinkpad R50e
using wireless networking

---

### Post by mish on 2008-07-07
Found this

[https://help.ubuntu.com/community/NetworkManager#Disabling%20NetworkManager](https://help.ubuntu.com/community/NetworkManager#Disabling%20NetworkManager)

In case it gets edited or something, the short version is

Stop network manager

sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop
sudo /etc/dbus-1/event.d/25NetworkManager stop

Create two files with only the word 'exit' in them. These files are:

/etc/default/NetworkManager
/etc/default/NetworkManagerDispatcher

---

