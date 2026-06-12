---
title: "Need Help with Samba"
date: 2009-11-10
forum: x86 64-bit Users
---

### Post by aglc2005 on 2009-11-10
I have had this issue with Samba since I installed 9.04. I have upgraded to 9.10, but still have the same issue. The problem is when enabling a file share (right click on folder and click share method). Both computers are on the MSHOME workgroup, however on the Windows machine when I go to view workgroup computers, I get:

Mshome is not accessible. You might not have permission to use this network resource. Contact the administrator of this server to find out if you have access permissions.

The list of servers for this workgroup is not currently available.


I also cannot get a list of servers when going from Ubuntu to a Windows file share. Can anyone give me some help and a push in the right direction? I really need this working.

---

### Post by timgood on 2009-11-11
If you edit /etc/samba/smb.conf you can change the default name from Workgroup to that of your share. You can edit it by entering:

sudo gedit /etc/samba/smb.conf in a terminal.  In the global section you will see:

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP


So change that to the name of your workgroup.

Save the file and then type in a terminal:

sudo /etc/init.d/samba restart 

which will restart samba. Try to access your shares again. Hope this helps.

---

### Post by aglc2005 on 2009-11-11
Thank you for the response. Both computers are on the same workgroup (MSHOME) and I am still having the same issue. Below is my smb.conf file.

```

[global]
netbios name = Samba24
server string = Samba file and print server
workgroup = MSHOME
security = user
hosts allow = 127. 192.168.1.111
interfaces = 127.0.0.1/8, 192.168.1.144/24
bind interfaces only = yes
remote announce = 192.168.1.255
remote browse sync = 192.168.1.255
printcap name = cups
load printers = yes
cups options = raw
printing = cups
guest account = smbguest
log file = /var/log/samba/samba.log
max log size = 1000
null passwords = no
username level = 6
password level = 6
encrypt passwords = true
unix password sync = yes
socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
local master = no
domain master = no
preferred master = no
domain logons = no
os level = 33
logon drive = m:
logon home = \\%L\homes\%u
logon path = \\%L\profiles\%u
logon script = %G.bat
time server = no
name resolve order = wins lmhosts bcast
wins support = no
wins proxy = no
dns proxy = no
preserve case = yes
short preserve case = yes
client use spnego = no
client signing = no
client schannel = no
server signing = no
server schannel = no
nt pipe support = yes
nt status support = yes
allow trusted domains = no
obey pam restrictions = yes
enable spoolss = yes
client plaintext auth = no
disable netbios = no
follow symlinks = no
update encrypted = yes
pam password change = no
passwd chat timeout = 120
hostname lookups = no
username map = /etc/samba/smbusers
smb passwd file = /etc/samba/smbpasswd
passwd program = /usr/bin/passwd '%u'
passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
add user script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null '%u'
add user to group script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null -g '%g' '%u'
add group script = /usr/sbin/groupadd '%g'
delete user script = /usr/sbin/userdel '%u'
delete user from group script = /usr/sbin/userdel '%u' '%g'
delete group script = /usr/sbin/groupdel '%g'
add machine script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /dev/null -M '%u'
machine password timeout = 120
idmap uid = 16777216-33554431
idmap gid = 16777216-33554431
template shell = /dev/null
winbind use default domain = yes
winbind separator = @
winbind cache time = 360
winbind trusted domains only = yes
winbind nested groups = no
winbind nss info = no
winbind refresh tickets = no
winbind offline logon = no

[homes]
comment = Home Directories
path = /home
read only = no
available = yes
browseable = yes
writable = yes
guest ok = no
public = no
printable = no
share modes = no
locking = no

[netlogon]
comment = Network Logon Service
path = /home/netlogon
read only = no
available = yes
browseable = yes
writable = no
guest ok = no
public = no
printable = no
share modes = no
locking = no

[profiles]
comment = User Profiles
path = /var/samba/profiles
read only = no
available = yes
browseable = no
writable = yes
guest ok = no
public = no
printable = no
locking = no
create mode = 0600
directory mask = 0700

[printers]
comment = All Printers
path = /var/spool/samba
browseable = yes
writable = no
guest ok = no
public = no
printable = yes
share modes = no
locking = no

[pdf-documents]
path = /home/pdf-documents
comment = Converted PDF Documents
available = yes
browseable = yes
writeable = yes
guest ok = yes

[pdf-printer]
path = /tmp
comment = PDF Printer Service
printable = yes
guest ok = yes
use client driver = yes
printing = bsd
print command = /usr/bin/gadmin-samba-pdf %s %u
lpq command =
lprm command =

[Media]
path = /home/andrew/xbox360
comment = media share
valid users = andrew
read only = no
available = yes
browseable = yes
writable = no
guest ok = yes
public = no
printable = no
share modes = no
locking = no

```

---

### Post by blueridgedog on 2009-11-11
Samba is not installed by default in Karmic.  Is is installed?

Have you created user accounts for the users that match the accounts they use on windows including passwords?  Have you use the smbpasswd command on your Ubuntu system to give passwords to those accounts that again match the Linux system password and the windows password that they use?  See the link in my signature, especially section 1.1.

---

### Post by aglc2005 on 2009-11-11
> **blueridgedog said:**
> Samba is not installed by default in Karmic.  Is is installed?

Have you created user account for the users that match the accounts they use on windows including passwords?  Have you use the smbpasswd command on your Ubuntu system to give passwords to those accounts that again match the Linux system password and the windows password that they use?  See the link in my signature, especially section 1.1.

Thank you so much. I followed your directions to the T and it works perfectly now. I really didn't like the whole right click to enable the share anyway. I did have Samba installed, but it wasn't until I moved into my apartment at school that I wanted to share my files to my netbook that it not working because an issue. Thanks again!

---

### Post by blueridgedog on 2009-11-11
Excellent!  Most people miss the following when setting up samba:

Just for future "searchers"

For a user "joe" with password "mypassword" who uses a windows computer and wants to access files on a Ubuntu/Linux samba server:

Windows needs a user joe with password mypassword
Ubuntu/Linux needs a user joe with password mypassword
Samba needs to have a samba password created for user joe that is mypassword.

The command for the samba password is

```
smbpasswd -a joe 
```
 (entering the password when prompted)

---

### Post by aglc2005 on 2009-11-12
> **blueridgedog said:**
> Excellent!  Most people miss the following when setting up samba:

Just for future "searchers"

For a user "joe" with password "mypassword" who uses a windows computer and wants to access files on a Ubuntu/Linux samba server:

Windows needs a user joe with password mypassword
Ubuntu/Linux needs a user joe with password mypassword
Samba needs to have a samba password created for user joe that is mypassword.

The command for the samba password is

```
smbpasswd -a joe 
```
 (entering the password when prompted)

Something I would like to add that I experimented with all of this:

Windows does not care about the capital letters for your username, but if you are trying to connect to a Linux Samba, it matters. Example:

Samba username: andrew
Windows logged in as: Andrew

this will NOT work but:

Samba username: andrew
Windows logged in as: andrew

this will work.

Windows will login as either, the 'A' vs 'a' doesn't matter. But if you try to connect to a Samba with 'A' it will not work.

---

