---
title: "Wine script"
date: 2019-09-11
forum: Wine
---

### Post by skphoen1x on 2019-09-11
Hi,

I would like to make a script for a dedicatedServer for FarmingSimulator 19
atm i need todo several steps to start the server and I want to do this with an automated Script

Steps I do

open new tmux session
add a split screen (left/right)
on the right side i su and set ```
ip link set lo down
```
on the left side I Start the server via ```
wine .wine/drive_c/FS19/dedicatedServer.exe
```
on the right side i set ```
ip link set lo up
```
and then i detach the session

Problem is every some hours (around 16-72hrs) the webservice is not anymore respondable then I had to kill the wine process and start again.
I have the lxc container running on a proxmox server, and I would like to only restart the server to get it back running.

The gameserver is working in the background without any issues only the webserver from GIANTS is off.

Hope someone can help me.

would be nice if someone can help me build a sysctl with this information.

Regards Alex

---

### Post by skphoen1x on 2019-09-12
Update:

```
ip link set lo down/up
```
are not needed anymore. do it now with portforwarding with Iptable.

only thing I don't know if I can do an easy script what start the dedicated server as a service.

Regards Alex

---

