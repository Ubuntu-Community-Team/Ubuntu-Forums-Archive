---
title: "OpenVPN on Xubuntu"
date: 2007-05-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by Sladi on 2007-05-22
I have "VPN Connection Manager (OpenVPN)" installed but I can't find anything about it. According to Synaptic it should be in the Internet menu but that's not in my menu, there is only Network. 
How can I use an ovpn file? 

I tried Kvpnc but it notifies me every minute about a successful connection and I think it's buggy. It seems to create 0 byte files in my home folder. 

With that I also tried Rapid SVN but it shows an error (attachment) when I try to do anything (with Kvpnc). 

Can somebody help please? 


Regards, 
Sladi

---

### Post by madhu542 on 2007-05-23
hai...

Have u installed the openvpn and configured the .ovpn or .conf files correctly check it out...

then...

try this command...

/etc/init.d/openvpn start          in teriminal as root user

then it will give u like this...

root@madhu-desktop:/home/madhu# /etc/init.d/openvpn start
Starting virtual private network daemon:.


then run the .conf or .ovpn file in the terminal, it will ask u the username and password ... then check with the ping command

---

### Post by Sladi on 2007-05-24
Thanks madhu! :)

Unfortunately the conf file doesn't work. I got it finished and in windows it works fine. 

Here is a part of it: 
```
tls-client
client
dev tun
proto udplzo
tun-mtu 1400
remote x.x.x.x xxxx
pkcs12 x.p12
cipher BF-CBC
comp-lzo
verb 3
ns-cert-type server
```
When I run it with sh sladi.conf it gives errors: 
```
: not foundic-TO-IPCop.conf: 2: tls-client
: not foundic-TO-IPCop.conf: 3: client
SladjanRistic-TO-IPCop.conf: 4: dev: not found
SladjanRistic-TO-IPCop.conf: 5: proto: not found
SladjanRistic-TO-IPCop.conf: 6: tun-mtu: not found
SladjanRistic-TO-IPCop.conf: 7: remote: not found
SladjanRistic-TO-IPCop.conf: 8: pkcs12: not found
SladjanRistic-TO-IPCop.conf: 9: cipher: not found
: not foundic-TO-IPCop.conf: 10: comp-lzo
SladjanRistic-TO-IPCop.conf: 11: verb: not found
SladjanRistic-TO-IPCop.conf: 12: ns-cert-type: not found
```

Regards, 
Sladi

---

