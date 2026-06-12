---
title: "Problem with Kismet in Amd64"
date: 2008-11-12
forum: x86 64-bit Users
---

### Post by KDB9000 on 2008-11-12
I have installed Intrepid Amd64 onto my AMD64 laptop and would like to use Kismet. It works fine but when I quit the program it stops and I can't kill the process. Here is the out put:

$ sudo kismet
[sudo] password for administrator: 
Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (kismet): Enabling monitor mode for rt2500 source interface wlan1 channel 6...
Source 0 (kismet): Opening rt2500 source interface wlan1...
Will attempt to put networkmanager to sleep...
Allowing clients to fetch WEP keys.
WARNING:  Disabling GPS logging.
Logging networks to /var/log/kismet/Kismet-Nov-12-2008-2.network
Logging networks in CSV format to /var/log/kismet/Kismet-Nov-12-2008-2.csv
Logging networks in XML format to /var/log/kismet/Kismet-Nov-12-2008-2.xml
Logging cryptographically weak packets to /var/log/kismet/Kismet-Nov-12-2008-2.weak
Logging cisco product information to /var/log/kismet/Kismet-Nov-12-2008-2.cisco
Logging data to /var/log/kismet/Kismet-Nov-12-2008-2.dump
Writing data files to disk every 300 seconds.
Mangling encrypted and fuzzy data packets.
Tracking probe responses and associating probe networks.
Reading AP manufacturer data and defaults from //etc/kismet/ap_manuf
Reading client manufacturer data and defaults from //etc/kismet/client_manuf
Using network-classifier based data encryption detection
Not tracking duplicate IVs
Putting networkmanager to sleep...
Dump file format: wiretap (local code) dump
Crypt file format: airsnort (weak packet) dump
Kismet 2008.05.R1 (Kismet)
Logging data networks CSV XML weak cisco
Listening on port 2501.
Allowing connections from 127.0.0.1/255.255.255.255
Registering builtin client/server protocols...
Registering requested alerts...
Registering builtin timer events...
Gathering packets...
Launching kismet_client: //usr/bin/kismet_client
Launched client, pid 6345
Looking for startup info from localhost:2501..... found.
Connected to Kismet server 2008.05.R1 on localhost:2501

(GUI starts at this point I believe. From here it is when I Capital-Q)

Reading AP manufacturer data and defaults from //etc/kismet/ap_manuf
Reading client manufacturer data and defaults from //etc/kismet/client_manuf

When I do a ctrl-c:

(Picking up from Capital-Q)

Reading AP manufacturer data and defaults from //etc/kismet/ap_manuf
Reading client manufacturer data and defaults from //etc/kismet/client_manuf
^CSelect failed: Bad file descriptor
Didn't see any weak encryption packets, unlinking weak file
WARNING: Sometimes cards don't always come out of monitor mode
         cleanly.  If your card is not fully working, you may need to
 Trying to wake networkmanager back up...
Kismet exiting.
Done.

But doesn't close. I still don't have a prompt. When I open a new terminal and do a "sudo killall kismet" it appears to work but doesn't. Same for killing the PID. Any thoughts? Would like to get this fixed soon.

---

### Post by bismark on 2008-11-13
What is your wireless card?

---

### Post by NDLunchbox on 2008-11-17
I'm having the same problem - 8.10 AMD64 on a Lenovo x200 (Intel wlink 5300 or 5100... not sure which.)

The adapter stays in promiscuous mode - a bad think IMO - and ```
$ sudo ifconfig wlan0 -promisc
``` doesn't work.  Kistmet is setup to use the IPW3945, the latest adapter supported that seemed to work.

Other than that, Kismet seems to work normally... for instance, I launch Wireshark and am able to sniff - unfortunately it keeps sniffing after I close Kismet.

---

