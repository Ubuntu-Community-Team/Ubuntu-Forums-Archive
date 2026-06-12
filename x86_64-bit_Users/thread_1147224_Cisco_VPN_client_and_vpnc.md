---
title: "Cisco VPN client and vpnc"
date: 2009-05-03
forum: x86 64-bit Users
---

### Post by wdavidow on 2009-05-03
Before anyone tells me to search the forums, I have; and I've been searching google for the past couple days...

I just installed Jaunty and I've got vpnclient-x86_64-4.8.02.0030-k9 patched and installed.  I am able to then start daemon using the vpnclient_init script, but when I try to use the client (using the same PCF I had working previously in earlier installs of ubuntu) I get the following error:

bash: /usr/local/bin/vpnclient: No such file or directory

I've also tried using vpnc, which results in the error 'The VPN Connection '...' failed because there were no valid VPN secrets.

Can anyone tell me how to get up and running in jaunty 64?  I'm clearly missing something, or do I just have to downgrade back to 32 bit?

---

### Post by dcstar on 2009-05-04
> **wdavidow said:**
> Before anyone tells me to search the forums, I have; and I've been searching google for the past couple days...

I just installed Jaunty and I've got vpnclient-x86_64-4.8.02.0030-k9 patched and installed.  I am able to then start daemon using the vpnclient_init script, but when I try to use the client (using the same PCF I had working previously in earlier installs of ubuntu) I get the following error:

bash: /usr/local/bin/vpnclient: No such file or directory

I've also tried using vpnc, which results in the error 'The VPN Connection '...' failed because there were no valid VPN secrets.

Can anyone tell me how to get up and running in jaunty 64?  I'm clearly missing something, or do I just have to downgrade back to 32 bit?

```
whereis vpnclient
locate vpnclient
```

---

### Post by shairozan on 2009-05-11
It may be important to note that most 64 bit systems, including windows, cannot run the VPN client required for communicating with Cisco VPNs. 

We run a VPN with a Cisco ASA 5510 as the endpoint, and I could only ever get Ubuntu x32 to connect to it. That was using the linux based cisco VPN client as well. 

Still, you'd think the 64 bit system would be able to run it as an x86 prog, but I'll see if I can figure anything out.

---

### Post by ionFreeman on 2009-05-19
I had the problem on 32-bit Jaunty Jackalope. For days I've been fooling with configuration files and installing and uninstalling various packages. vpnc and network-manager-vpnc I needed. But, I was still getting the apparently insoluble "there were no valid vpn secrets" error. A comment on [Launchpad bug #360818]("https://bugs.launchpad.net/ubuntu/+source/network-manager-vpnc/+bug/360818") solved it, though, to the effect of "well, of course you have to restart nm."

I don't know how one should restart nm but 

> ps aux | grep NetworkManager 
> sudo kill <that process id>
> sudo NetworkManager --(same arguments from the process snapshot listing)

worked for me. I can now make VPN connections!

---

### Post by vectorm12 on 2009-05-19
I've also tried to run the old Cisco clients on 9.04 x64 but had exactly the same issue, the only way I've gotten it to work is under 32bit 9.04.

Just as a side note Windows Vista/7 x64 has exactly the same problem. In the end I opted to change the VPN protocol to L2TP for which most OS:es(not sure about 9.04) has builtin clients for.

---

### Post by craigeo on 2009-05-19
Connecting to a Cisco VPN
Although Cisco has a Linux VPN client I found it much easier to use vpnc.
Here is the steps I used to get it work:
1. install vpnc with synaptic
2. open terminal, type sudo gedit /etc/vpnc/default.conf
An example of default.conf:
IPSec gateway ip.to.vpn.server
IPSec ID VPNservergroupname
IPSec obfuscated secret cryptedpasswordfrompcffile
Xauth interactive
4. sudo vpnc-connect
5. enter your vpn user name, enter
6. enter pin code or what ever kind of system you have, enter. Now you're inside vpn tunnel
7. after you're done, sudo vpnc-disconnect

Quick and simple and works great.
I just created icons on my toolbar for 'sudo vpnc-connect' and 'sudo vpnc-disconnect' and have them run in a terminal.

---

