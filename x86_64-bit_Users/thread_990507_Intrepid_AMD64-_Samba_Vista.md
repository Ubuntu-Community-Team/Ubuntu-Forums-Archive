---
title: "Intrepid AMD64- Samba Vista"
date: 2008-11-22
forum: x86 64-bit Users
---

### Post by sam702 on 2008-11-22
Hi everyone.  I'm new to the Linux world.

I'm building a Samba file server so that vista users can have access to read and write on the network.

I installed the Ubuntu 8.10 Server AMD64 and Samba file server on an ECS g33t-m2 board, with e6200 core duo, 8M DDR2 800 memory, on a 300G Seagate7200.10 drives raid 1 setup.  The installation was smooth, no hiccups.

I am in the process of configuring the Samba smb.conf file .  The following is the smb.conf setup-

[global]
workgroup = workgroup
guest account = nobody
security = share
browseable = yes
guest ok = yes
guest only = no
log level = 1
max log size = 100
encrypted passwords = yes
dns proxy = no
netbios name = working_samba

[share1]
path = /opt/share/samba1
read only = no
writeable = yes
browseable = yes
public = yes


----end---- of file

I did create the samba1 file and change the folder permission to 777.  I also updated the secpol.msc in vista for the LAN Manager Authentication Level send LM & NTLM - use NTLMv2 session security if negotiated.

My goals are:

1.  Access shared folders on the Samba file server from vista.
2.  One folder for read and write capability.
3.  Another folder for read only.

I'm not worried about security at this time, just file access.

I know "search" is my friend and it has got me this far.  I can't drink any more caffeine.  Please help.  Send a complete workable smb.config if possible.  

Also, what other settings/configurations on both Intrepid and vista should I verify?

Thank you much.

---

### Post by cariboo on 2008-11-22
I didn't have to do anything in vista to connect to my server, the shares just showed up like they are supposed to. I've attached a copy of my smb.conf file.

Jim

---

### Post by sam702 on 2008-11-24
Thank you.

After a few more cups of coffee.  I solved it.

Changed the security = user

Create user and password in samba using smbpasswd.
Create user and password in the root account using useradd and passwd.
Make sure the folders are set to proper permission.

and VOILA!  solved.

I CREATED A HEADLESS SERVER!!!!!  :) hahaha.

---

