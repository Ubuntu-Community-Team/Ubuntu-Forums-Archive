---
title: "Security and properly Reading log files"
date: 2007-01-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by Jwilliamhunt on 2007-01-09
I've been using the 64 bit version for a while now and have had no real problems. Today I left Ubuntu on and I was sitting on my couch and my system went to the screen saver as usual. Next I heard it go to the splash log on screen, like the system restarted. Well it did. I tried to read the logs and I read a few report events around 14:40.  A "signal 15" was reported then the system appears to restart. That's what I'm assuming happened. This has never happened in the past I have left my system on for days without a restart. I tried to read the logs but being a noob I don't understand what I'm looking at.
 
I couldn't even figure how to copy and paste the logs or I would have added the correct ones here. I did see some "root" activity and "/redhat" lines and a few lines that where dening "wireless connection" even though I have no wireless network or wireless router. Some lines even refered to "read only partition" then lower it stated "read/write partition".

I guess my question are:

(1) I need to copy the logs. What logs should I copy and how. Just in case I need to show some one.
(2)What are the most important logs and files I should keep an eye on in the future? 
(3) Can I check on my own with little explination or effort to see if my machine has been accessed and is now vulnerable from the network?

Thank you all in advance for your time. any sugestions will be considered

William.

---

### Post by scrooge_74 on 2007-01-09
First question you can try gksudo gedit /var/log/the_file_you_want_to_open

Second questin your sylog and your userlog, but I am no expert so I can't be sure on this one.

Third question> try using firestarter as your iptables interface so you can see any attempt to connect to your PC and check if you have any ports open that should not be open, also remember to update your system regularly.  Remember to have a strong password for your system.

Maybe after posting your logs someone can give you more info

---

### Post by Jwilliamhunt on 2007-01-10
I've read your suggestions and I will look into it tomorrow. I don't quite know how to secure ports just yet. Read, read, read, I guess? I'm aware of Firestarter. but it's not installed yet.

 As for the password I usually do 20+ alpha-numeric.

thank you again 
Cheers!

---

### Post by Jwilliamhunt on 2007-01-10
Ok this is what I found so far in the syslog right about the time my computer restarted:
an  9 14:44:18 machine -- MARK --
Jan  9 15:04:18 machine -- MARK --
Jan  9 15:17:01 machine /USR/SBIN/CRON[8488]: (root) CMD (   run-parts --report /etc/cron.hourly)
Jan  9 15:44:19 machine -- MARK --
Jan  9 15:47:31 machine gconfd (machine-4674): Received signal 15, shutting down cleanly
Jan  9 15:47:31 machine gconfd (machine-4674): Exiting
Jan  9 15:47:31 machine gdm[4139]: Error reinitilizing server
Jan  9 15:47:34 machine kernel: [ 5615.610944] mtrr: no more MTRRs available
Jan  9 15:47:34 machine kernel: [ 5615.610981] mtrr: no more MTRRs available
Jan  9 15:47:34 machine kernel: [ 5615.610996] mtrr: no more MTRRs available
Jan  9 15:47:34 machine kernel: [ 5615.611009] mtrr: no more MTRRs available
Jan  9 15:48:11 machine gconfd (machine-9315): starting (version 2.16.0), pid 9315 user 'machine'
Jan  9 15:48:11 machine gconfd (machine-9315): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jan  9 15:48:11 machine gconfd (machine-9315): Resolved address "xml:readwrite:/home/machine/.gconf" to a writable configuration source at position 1
Jan  9 15:48:11 machine gconfd (machine-9315): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jan  9 15:48:11 machine gconfd (machine-9315): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jan  9 15:48:11 machine gconfd (machine-9315): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jan  9 15:48:12 machine gconfd (machine-9315): Resolved address "xml:readwrite:/home/machine/.gconf" to a writable configuration source at position 0
Jan  9 15:48:13 machine NetworkManager: <information>^IUpdating allowed wireless network lists. 
Jan  9 15:48:13 machine NetworkManager: <WARNING>^I nm_dbus_get_networks_cb (): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Jan  9 16:02:24 machine gconfd (machine-9315): Exiting
Jan  9 16:02:24 machine gdm[4123]: Master halting...
Jan  9 16:02:26 machine init: tty1 process (3658) killed by signal 15
Jan  9 16:02:26 machine init: tty2 process (3659) killed by signal 15
Jan  9 16:02:26 machine init: tty3 process (3660) killed by signal 15
Jan  9 16:02:26 machine init: tty4 process (3661) killed by signal 15
Jan  9 16:02:26 machine init: tty5 process (3662) killed by signal 15
Jan  9 16:02:26 machine init: tty6 process (3663) killed by signal 15
Jan  9 16:02:30 machine NetworkManager: <WARNING>^I nm_signal_handler (): Caught signal 15, shutting down normally. 
Jan  9 16:02:30 machine NetworkManager: <information>^ICaught terminiation signal 
Jan  9 16:02:30 machine NetworkManager: <debug info>^I[1168387350.758487] nm_print_open_socks (): Open Sockets List: 
Jan  9 16:02:30 machine NetworkManager: <debug info>^I[1168387350.758570] nm_print_open_socks (): Open Sockets List Done. 
Jan  9 16:02:30 machine NetworkManager: <information>^IDeactivating device eth0. 
Jan  9 16:02:30 machine dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 4591
Jan  9 16:02:30 machine dhclient: killed old client process, removed PID file
Jan  9 16:02:30 machine dhclient: DHCPRELEASE on eth0 to 192.168.2.1 port 67
Jan  9 16:02:30 machine dhcdbd: dhco_input_option: Value 4294967295 cannot be converted to type L 
Jan  9 16:02:30 machine dhcdbd: dhco_parse_option_settings: bad option setting: old_dhcp_lease_time = 4294967295 
Jan  9 16:02:31 machine NetworkManager: <information>^IDeactivating device eth1. 
Jan  9 16:02:31 machine hcid[4430]: Got disconnected from the system message bus
Jan  9 16:02:33 machine exiting on signal 15

I also found two user logs:( user.log )and (user.log.0) should this be?
this is from my user.log:
an  9 15:47:31 machine gconfd (machine-4674): Received signal 15, shutting down cleanly
Jan  9 15:47:31 machine gconfd (machine-4674): Exiting
Jan  9 15:48:11 machine gconfd (machine-9315): starting (version 2.16.0), pid 9315 user 'machine'
Jan  9 15:48:11 machine gconfd (machine-9315): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jan  9 15:48:11 machine gconfd (machine-9315): Resolved address "xml:readwrite:/home/machine/.gconf" to a writable configuration source at position 1
Jan  9 15:48:11 machine gconfd (machine-9315): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jan  9 15:48:11 machine gconfd (machine-9315): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jan  9 15:48:11 machine gconfd (machine-9315): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jan  9 15:48:12 machine gconfd (machine-9315): Resolved address "xml:readwrite:/home/machine/.gconf" to a writable configuration source at position 0
Jan  9 16:02:24 machine gconfd (machine-9315): Exiting
Jan  9 16:02:30 machine dhcdbd: dhco_input_option: Value 4294967295 cannot be converted to type L 
Jan  9 16:02:30 machine dhcdbd: dhco_parse_option_settings: bad option setting: old_dhcp_lease_time = 4294967295 
Jan  9 21:24:20 machine hpiod: 1.6.9 accepting connections at 2208... 
Jan  9 21:24:23 machine dhcdbd: Started up.

I don't know if these logs will clarify, or help, but this is when the incident happened 3:40 in the afternoon.. Now to find out how to shut down ports not used.

Thanks for any input.

Cheers!

---

### Post by scrooge_74 on 2007-01-10
I am not that good reading logs, it seems after a CRON job then a little while later it when on a reboot.
It says something about not storing any wireless network info, but I cant make sense of the rest.

About sys logs I do know that after a while they get compress to save space user.log.0 is the previous user.log to the current one.  If you check /var/log you are going to find other logs that are compress i usually delete those after a while

---

