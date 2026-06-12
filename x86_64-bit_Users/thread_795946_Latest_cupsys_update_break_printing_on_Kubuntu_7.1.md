---
title: "Latest cupsys update break printing on Kubuntu 7.10"
date: 2008-05-16
forum: x86 64-bit Users
---

### Post by mtrainer on 2008-05-16
Hi,

I applied the latest cupsys related updates on Kubuntu 7.10 and remote cups  printing to my machine is now broken.  I get the errors below:

May 16 11:41:39 kubuntu64 kernel: [  156.251050] audit(1210909299.185:46):  type=1503 operation="inode_permission" requested_mask="r" denied_mask="r" name="/var/lib/dbus/machine-id" pid=6897 profile="/usr/sbin/cupsd"
May 16 11:41:39 kubuntu64 kernel: [  156.255211] audit(1210909299.189:47):  type=1503 operation="inode_permission" requested_mask="r" denied_mask="r" name="/home/murray/.Xauthority" pid=7787 profile="/usr/sbin/cupsd"
May 16 11:41:39 kubuntu64 kernel: [  156.257156] audit(1210909299.193:48):  type=1503 operation="inode_permission" requested_mask="r" denied_mask="r" name="/var/lib/dbus/machine-id" pid=6897 profile="/usr/sbin/cupsd"
May 16 11:41:39 kubuntu64 kernel: [  156.261020] audit(1210909299.197:49):  type=1503 operation="inode_permission" requested_mask="r" denied_mask="r" name="/home/murray/.Xauthority" pid=7788 profile="/usr/sbin/cupsd"
May 16 11:41:39 kubuntu64 kernel: [  156.262843] audit(1210909299.197:50):  type=1503 operation="inode_permission" requested_mask="r" denied_mask="r" name="/var/lib/dbus/machine-id" pid=6897 profile="/usr/sbin/cupsd"
May 16 11:41:39 kubuntu64 kernel: [  156.266709] audit(1210909299.201:51):  type=1503 operation="inode_permission" requested_mask="r" denied_mask="r" name="/home/murray/.Xauthority" pid=7789 profile="/usr/sbin/cupsd"

A change in the apparmor config might fix the issue above but the attempted access to $HOME/.Xauthority is going to be a problem for secure NFS home directories mounted with rootsquash enabled.  

Murray

---

### Post by mtrainer on 2008-06-12
I fixed the errors above with some changes to my apparmor config.  When I try and print to a remote cups printer I get the errors below in messages:

Jun 12 12:50:19 kubuntu64-xen kernel: [15714.482171] cupsd[6980]: segfault at 0000000000000038 rip 00002aad96cc759d rsp 00007fff1560fcf0 error 4

and in the cups log file:

E [12/Jun/2008:15:09:41 +0800] [Job 39] Print file was not accepted (Unsupported format 'application/octet-stream'!)!
E [12/Jun/2008:15:09:42 +0800] PID 6213 (/usr/lib/cups/backend/http) stopped with status 1!

Is the latest cups updates on Kubuntu 7.10 broken on a xen kernel?

Thanks

Murray


> **mtrainer said:**
> Hi,

I applied the latest cupsys related updates on Kubuntu 7.10 and remote cups  printing to my machine is now broken.  I get the errors below:

May 16 11:41:39 kubuntu64 kernel: [  156.251050] audit(1210909299.185:46):  type=1503 operation="inode_permission" requested_mask="r" denied_mask="r" name="/var/lib/dbus/machine-id" pid=6897 profile="/usr/sbin/cupsd"
May 16 11:41:39 kubuntu64 kernel: [  156.255211] audit(1210909299.189:47):  type=1503 operation="inode_permission" requested_mask="r" denied_mask="r" name="/home/murray/.Xauthority" pid=7787 profile="/usr/sbin/cupsd"
May 16 11:41:39 kubuntu64 kernel: [  156.257156] audit(1210909299.193:48):  type=1503 operation="inode_permission" requested_mask="r" denied_mask="r" name="/var/lib/dbus/machine-id" pid=6897 profile="/usr/sbin/cupsd"
May 16 11:41:39 kubuntu64 kernel: [  156.261020] audit(1210909299.197:49):  type=1503 operation="inode_permission" requested_mask="r" denied_mask="r" name="/home/murray/.Xauthority" pid=7788 profile="/usr/sbin/cupsd"
May 16 11:41:39 kubuntu64 kernel: [  156.262843] audit(1210909299.197:50):  type=1503 operation="inode_permission" requested_mask="r" denied_mask="r" name="/var/lib/dbus/machine-id" pid=6897 profile="/usr/sbin/cupsd"
May 16 11:41:39 kubuntu64 kernel: [  156.266709] audit(1210909299.201:51):  type=1503 operation="inode_permission" requested_mask="r" denied_mask="r" name="/home/murray/.Xauthority" pid=7789 profile="/usr/sbin/cupsd"

A change in the apparmor config might fix the issue above but the attempted access to $HOME/.Xauthority is going to be a problem for secure NFS home directories mounted with rootsquash enabled.  

Murray

---

