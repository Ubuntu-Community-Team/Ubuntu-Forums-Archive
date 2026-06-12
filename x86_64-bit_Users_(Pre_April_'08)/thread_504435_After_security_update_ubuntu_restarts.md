---
title: "After security update ubuntu restarts"
date: 2007-07-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by liengjai on 2007-07-19
Hi Guys,

Yesterday I received 2 security updates and installed/accepted them.

A short while later in the day ubuntu started restarting every so often. It appeared that the restarts were only associated with Firefox. I started using Epiphinay and the same thing happens.

I am using unbuntu Feisty 7.04 on an Acer Aspire 5050 Laptop

I have tried googling a solution but only a small handful of people are experiencing the same thing with no replies. Any help would be appreciated. If there is a roll back solution I would welcome that or anything to stop the machine from restarting.


daemon log shows:

Jul 19 09:43:38 blowfish gdm[4845]: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
Jul 19 09:43:50 blowfish NetworkManager: <information>^IUpdating allowed wireless network lists. 
Jul 19 09:53:31 blowfish gdm[6482]: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 

The kernal log shows plenty of :
Jul 19 09:25:17 blowfish kernel: [   35.538900] hda_codec: invalid dep_range_val 0:7fff all the way up to Jul 19 09:25:17 blowfish kernel: [   35.632829] hda_codec: invalid dep_range_val 0:7fff

I am not sure if this means anything, it is from the same log
Jul 19 09:39:41 blowfish kernel: [  573.116697] Losing some ticks... checking if CPU frequency changed.
Jul 19 09:43:49 blowfish kernel: [  711.427135] hda_codec: num_steps = 0 for NID=0xd
Jul 19 09:53:42 blowfish kernel: [ 1280.941176] hda_codec: num_steps = 0 for NID=0xd

The sys log shows :

Jul 19 09:31:46 blowfish syslogd 1.4.1#20ubuntu4: restart.
Jul 19 09:31:46 blowfish anacron[5084]: Job `cron.daily' terminated
Jul 19 09:31:46 blowfish anacron[5084]: Normal exit (1 job run)
Jul 19 09:39:41 blowfish kernel: [  573.116697] Losing some ticks... checking if CPU frequency changed.
Jul 19 09:43:38 blowfish gconfd (oliver-5335): Received signal 15, shutting down cleanly
Jul 19 09:43:38 blowfish gconfd (oliver-5335): Exiting
Jul 19 09:43:38 blowfish gdm[4845]: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
Jul 19 09:43:47 blowfish gconfd (oliver-6544): starting (version 2.18.0.1), pid 6544 user 'oliver'
Jul 19 09:43:47 blowfish gconfd (oliver-6544): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jul 19 09:43:47 blowfish gconfd (oliver-6544): Resolved address "xml:readwrite:/home/oliver/.gconf" to a writable configuration source at position 1
Jul 19 09:43:47 blowfish gconfd (oliver-6544): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jul 19 09:43:47 blowfish gconfd (oliver-6544): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jul 19 09:43:47 blowfish gconfd (oliver-6544): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jul 19 09:43:48 blowfish gconfd (oliver-6544): Resolved address "xml:readwrite:/home/oliver/.gconf" to a writable configuration source at position 0
Jul 19 09:43:49 blowfish kernel: [  711.427135] hda_codec: num_steps = 0 for NID=0xd
Jul 19 09:43:50 blowfish NetworkManager: <information>^IUpdating allowed wireless network lists. 


Thanks

---

### Post by liengjai on 2007-07-24
This is becoming really silly now.

The machine restarts whilst browsing.

The last bit of code that I can offer to anyone out there is :

Jul 24 17:01:11 blowfish dhclient: No working leases in persistent database - sleeping.
Jul 24 17:01:21 blowfish gdm[22644]: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
Jul 24 17:03:06 blowfish kernel: [16682.373353] hda_codec: num_steps = 0 for NID=0x19
Jul 24 17:03:06 blowfish NetworkManager: <information>^IUpdating allowed wireless network lists. 
Jul 24 17:06:07 blowfish dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Jul 24 17:06:10 blowfish dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Jul 24 17:06:17 blowfish dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Jul 24 17:06:27 blowfish dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Jul 24 17:06:39 blowfish dhclient: No DHCPOFFERS received.
Jul 24 17:06:39 blowfish dhclient: No working leases in persistent database - sleeping.
Jul 24 17:08:41 blowfish gdm[23206]: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
Jul 24 17:08:54 blowfish NetworkManager: <information>^IUpdating allowed wireless network lists. 
Jul 24 17:08:55 blowfish kernel: [16959.272904] hda_codec: num_steps = 0 for NID=0x19

Is there any way to stop the machine from restarting? If this was MS Windows I would begin to think of it as a virus.


Thank in advance.


:confused:

---

### Post by Kilz on 2007-07-24
Just one question, did you file a bug report on launchpad?

---

