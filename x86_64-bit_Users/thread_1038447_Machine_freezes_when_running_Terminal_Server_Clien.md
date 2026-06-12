---
title: "Machine freezes when running Terminal Server Client"
date: 2009-01-12
forum: x86 64-bit Users
---

### Post by cherukan on 2009-01-12
After my upgrade to 64bit Ubuntu 8.10, I have been having trouble with Terminal Server client sessions. I connect to my Windows PC at work via VPN (Cisco) and find that after about 5-10 mins of working my linux machine just freezes up. Both mouse and keyboard are rendered useless. Ctrl+Alt+Backspace doesn't work, nor does Ctrl+Alt+Del/F1/F2/F3. I end up having to hit the reset button on my computer.

It does not seem to be a problem with the Windows host, because I can boot up another linux machine nearby and access the same host while the first one is locked up.

I also don't experience this problem if I run a virtual windows machine within my linux box using VirtualBox and run Windows' Remote Desktop Connection within that.

Any clues on what might be going on?


Configuration:
AMD X2 6000+/2 GB/Ubuntu 8.10 with all the latest updates.
Compiz enabled.

---

### Post by cherukan on 2009-01-14
Update: Today this happened while I was not running Terminal Server client but when VPN connection was active (but not actively being used), so next suspect seems to be Cisco VPN client (4.8.01). I have the 32-bit version which is reported on some sites as not compatible with 64bit Linux. Can anyone else confirm this?

---

### Post by mister_doctor on 2009-01-14
I wasn't aware that the Cisco VPN client even worked at all in Ubuntu. I know some of my workmates have tried compiling from source. That said, Cisco has openly stated that they do not have any plans to support 64 bit OSes, including windoze. This is becoming a problem for us as more employees are buying home PCs with 64bit Vista installed on them...

You could try using **vpnc** with **kvpnc** as a GUI front-end. It is supposed to be compatible with most Cisco hardware. I've managed to get it to connect with the ASA 5500 we have here. Give it a shot, the GUI makes configuration much easier.

---

### Post by cherukan on 2009-01-14
Thanks. I tried vpnc, but got this error..

```

$ sudo vpnc MyProfile
vpnc was built without openssl: Can't do hybrid or cert mode.

```

Update: I followed steps on this site, and applied all available patches for the cisco vpn client, but to no avail.

[http://projects.tuxx-home.at/?id=cisco_vpn_client](http://projects.tuxx-home.at/?id=cisco_vpn_client)

---

### Post by SleeperGTP on 2009-01-23
I am also having this issue but I am not using VPN.  When I connect to a PC on my LAN the drop down list next to "Computer" appears in my session and I lose all mouse control.  I can type for a moment before the machine locks up and I have to reset the PC.

---

### Post by roscowgo on 2009-02-04
If it's the same problem I'm having with 8.10 TSC, it's caused by the drop down menu in the address bar in the client.    If you connect without clicking in the address field to get the blank textbox to go back up, the mouse etc will stop responding.

Look for a white box after you connect... thats my telltale.  I can usually retain kb control long enough to cancel out of the login process on the remote machine, which kills the tsc so I can close the box.

---

### Post by zaber on 2009-03-09
> **roscowgo said:**
> If it's the same problem I'm having with 8.10 TSC, it's caused by the drop down menu in the address bar in the client.    If you connect without clicking in the address field to get the blank textbox to go back up, the mouse etc will stop responding.

Sounds like it is related to an issue I ha experiencing.  The bug report is here: [https://bugs.launchpad.net/ubuntu/+source/tsclient/+bug/288868](https://bugs.launchpad.net/ubuntu/+source/tsclient/+bug/288868)

---

### Post by themtx on 2009-03-09
> **zaber said:**
> Sounds like it is related to an issue I ha experiencing.  The bug report is here: [https://bugs.launchpad.net/ubuntu/+source/tsclient/+bug/288868](https://bugs.launchpad.net/ubuntu/+source/tsclient/+bug/288868)

I found this bug [https://bugs.launchpad.net/ubuntu/+source/tsclient/+bug/270374](https://bugs.launchpad.net/ubuntu/+source/tsclient/+bug/270374) a while back, added my own comments, and someone ("Mick K")recently coded a patch that resolves the issue (i386 and amd64).  See the thread for the .deb's.

However - I don't think the OP is seeing this - sounds like he's getting true hard lockups, as have I and many others.

---

### Post by pablosanchezuy on 2009-03-12
I have the same problems. 
At first i thought it was pptp client (network-manager-pptp) but the issue happens on connection with ts client. I'll try not to click in the address bar and see.
Ubuntu 8.10 amd64

Regards.
Pablo .

---

