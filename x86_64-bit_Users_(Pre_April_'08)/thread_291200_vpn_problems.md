---
title: "vpn problems"
date: 2006-11-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by sarag76 on 2006-11-02
I need to connect to my work vpn - which is windows of course.
Network manager works, and I configure the vpn part ok- but it does not connect and i'm not sure why -have reams of debug code i do not understand (am a techno-weenie :confused: ). 

i've heard that pptp-config works a treat but there appears to be no amd64 version of it - so i cannot use it - does anyone have any ideas?

thanks

---

### Post by kuja on 2006-11-02
A quick apt-cache search shows me a handful of related packages:
pptp-linux and pptpd, which I guess would be required most likely. Aside from that, there are two frontends that you haven't touched as of yet, maybe they'll work where networkmanager did not? They are: kvpnc, knet

---

### Post by speedothebrief on 2007-02-17
I am an AMD64 user as well, and I just went through all of this.

I've tried kvpnc and several other worhtless vpn clients. Don't even screw around with them... they all suck. They only worthwhile vpn client is pptpconfig... which you hit on already... it just isn't available to Ubuntu AMD64 users. I've tried building it several times, but there seems to be some kind of conflict.

The solution is this:
just configure pptp by hand, which is MUCH easier than it sounds. It took me 15 minutes to get up and running. The only problem I had was some strange packet size problem, which I fixed by adding the following line to my tunnel's config file:
```
mtu 1404
```

Here is a link to the configuration HOWTO (written by the master of all things PPTP himself, James Cameron):
[http://pptpclient.sourceforge.net/howto-debian.phtml#configure_by_hand]("http://pptpclient.sourceforge.net/howto-debian.phtml#configure_by_hand")

Good luck!

---

### Post by old_salt on 2007-03-15
I'm trying to connect to a Cisco VPN. KVPNC worked great on Suse and Fedora however I've not had any luck getting KVPNC to install let alone connect under Kubuntu-64. Tons of postings here for Windows VPN's but nothing on Cisco. Any advice would be appreciated. I'm encountering the TUN and socket errors.

......Thanks

---

### Post by cdenning on 2007-11-09
Has any gotten the Cisco VPN Client to work when this error message is being generated?


HTPC-Repository:~$ vpnclient connect DDNA-NY
Cisco Systems VPN Client Version 4.8.00 (0490)
Copyright (C) 1998-2005 Cisco Systems, Inc. All Rights Reserved.
Client Type(s): Linux
Running on: Linux 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64
Config file directory: /etc/opt/cisco-vpnclient

Initializing the VPN connection.
Secure VPN Connection terminated locally by the Client
Reason: The Connection Manager was unable to read the connection entry, or the connection entry has missing or incorrect information.
There are no new notification messages at this time.

---

### Post by kd7swh on 2007-11-09
I use both PPTP and Cisco VPNs for both work and school. 

For PPTP under gusty I had some work to do.

the PPTP plugin for NetworkManager in gusty only works with the eth0 interface, so I had to change my wireless card to eth0. if you need to do this check this thread: [http://ubuntuforums.org/showthread.php?t=601671](http://ubuntuforums.org/showthread.php?t=601671)

On the Cisco side of things I just use vpnc.

I created a .conf file in /etc/vpnc. In this case it is called um.conf:

```
IPSec gateway 00.0.0.000
IPSec ID IDGOESHERE
IPSec secret PLAINTEXTPASSWORDHERE
Xauth username usernamehere
Xauth password passwordhere
```

Then I created a small script (vpn.sh) with the settings from my IT department. (They didn't give them to me I got them from the Cisco profile that they gave me for windows) 

```
echo "Automated VPN Script"
echo "For the University of Montana Wireless Network"
echo "Jon Pielaet 2007" 
echo "Under GPL of User's Choice"

sudo vpnc um --local-port 10000
```

so when I want to use it I just type:
```
./vpn.sh
```
in the terminal and I am connected to the vpn.

I hope this helps someone.

- Jon

---

### Post by stuffelse on 2008-01-04
I followed the above directions, and this details my progress:


After the Cisco client was not available from my school, I used VPNC from the Synaptic, and I've got it working. I had to download the installation package and pick data from the .pcf profile. The main hangup for me was that the group password was hashed in the profile, for which [**this decoder tool**](http://www.unix-ag.uni-kl.de/~massar/bin/cisco-decode) came in VERY handy!: 

I was able to SSH to a lab computer on campus from 155 miles away at my parents house, so i'm fairly sure it worked!

Hope this helps someone!

---

### Post by stuffelse on 2008-01-04
um... so maybe i'm an idiot, but vpnc-disconnect is not actually disconnecting. it says "no vpn session detected" or something to that effect, but it is definitely connected. Any clues?

---

### Post by kd7swh on 2008-01-05
Glad you got it working. I am also glad you found a hash decoder. (sorry I forgot to say you needed the plain text group password.)

as far as disconnecting go's I just kill the client.

```
sudo kill pid#
```

vpnc gives you the pid# when it launches.

if you don't know what pid # vpnc is using you can try this:

```
pgrep vpnc -l
```

that will give you the pid # that you can use in the kill command.

For more help use man.
```
 man kill 
```
```
 man pgrep 
```

---

### Post by stuffelse on 2008-01-05
Sweet, the kill worked!

now here's what I'd LOVE to accomplish: I've got my script:```
echo "VPN Attempt"
sudo vpnc um --local-port 10000

``` I've assigned a launcher icon in my toolbar(?) up top to run this script in terminal, and what i'd love to do is essentially this:```
IF(vpn is not active)
{
echo "VPN Attempt"
sudo vpnc um --local-port 10000
}
ELSE
{
var pid = pgrep vpnc -l
sudo kill pid
} 
```so I can click it for enable and disable. am i kicking a dead horse, or is this easily doable?

EDIT: apparently if it's not connected, pgrep vpnc -l echos nothing in terminal, so could i do something like```
IF(pgrep vpnc -l){
sudo kill pgrep vpnc -l
}
ELSE{
sudo vpnc um --local-port 10000
}
```

---

### Post by kd7swh on 2008-01-06
yes, that should work.  you could also use an "exit status".

```
sudo pgrep -l vpnc 
$?
```

The "$?" will echo a "0" if the pgrep found a pid for vpnc.

so you could make an IF 0 line then ELSE for other vars.

enjoy.

---

### Post by Alpinist on 2008-01-06
> **stuffelse said:**
> IThe main hangup for me was that the group password was hashed in the profile, for which [**this decoder tool**](http://www.unix-ag.uni-kl.de/~massar/bin/cisco-decode) came in VERY handy!: 
!

Hmm, I didn't need to decode my group password.  I just put the encoded group password in my vpnc.conf file on a line with IPSec obfuscated secret.  VPNC can use the encoded hash.

---

### Post by stuffelse on 2008-01-06
> **kd7swh said:**
> yes, that should work.  you could also use an "exit status".

```
sudo pgrep -l vpnc 
$?
```

The "$?" will echo a "0" if the pgrep found a pid for vpnc.

so you could make an IF 0 line then ELSE for other vars.

enjoy.

cool, thanks for the nugget of knowledge! just one problem... I can't figure out how to declare a variable! #-o Can you declare variables in a similar style to c++/java or php? are they typed?
should one of these work?

```
var $pid = pgrep vpnc -l
```
```
int pid = pgrep vpnc -l
```

i'm so confused... :???:

---

### Post by kd7swh on 2008-01-06
try making a menu to connect and disconnect

```
echo "VPNC Menu"
echo "Jon Pielaet <jon.pielaet@umontana.edu>"
echo "2008"
echo "Root Password Required"

echo "______________________________________________________________________________"

OPTIONS="Connect Disconnect Quit "
select opt in $OPTIONS; do 
if [ "$opt" = "Quit" ]; then
exit
elif [ "$opt" = "Connect" ]; then
exec sudo vpnc um --local-port 10000
clear
elif [ "$opt" = "Disconnect" ]; then
exec sudo killall vpnc
clear
echo bad option
fi
done
```

that will do the trick.

---

### Post by kd7swh on 2008-01-06
> **Alpinist said:**
> Hmm, I didn't need to decode my group password.  I just put the encoded group password in my vpnc.conf file on a line with IPSec obfuscated secret.  VPNC can use the encoded hash.

It depends on how the hash is encoded. Some work others don't.

---

### Post by kd7swh on 2008-01-06
> **stuffelse said:**
> cool, thanks for the nugget of knowledge! just one problem... I can't figure out how to declare a variable! #-o Can you declare variables in a similar style to c++/java or php? are they typed?
should one of these work?

```
var $pid = pgrep vpnc -l
```
```
int pid = pgrep vpnc -l
```

i'm so confused... :???:

```
var=1
echo $var
```
will echo \ or "print" 1


```
 var1=$ pgrep vpnc > /dev/null && echo already_connected || echo not_connected
if
[$var1 > = not_connected ]
then
echo "vpnc is now connecting..." 
sudo vpnc um --local-port 10000
else
echo "You can't connect twice at one time!"
fi
exit 
```
would check to see if vpnc was running with pgrep and then run it if it wasn't

---

