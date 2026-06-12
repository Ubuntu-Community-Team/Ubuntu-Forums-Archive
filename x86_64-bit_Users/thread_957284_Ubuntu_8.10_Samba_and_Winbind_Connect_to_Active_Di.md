---
title: "Ubuntu 8.10 Samba and Winbind Connect to Active Directory"
date: 2008-10-24
forum: x86 64-bit Users
---

### Post by kylea on 2008-10-24
I have moved my desktop to 8.10 and love it. nearly everything I need works and it looks great.

The one last problem is being able to login to a clients Windows 2003 Active Directory.

I can get the Kerberos security module to return tickets:

[INDENT]
kylea@kylea-e6500:~$ klist
Ticket cache: FILE:/tmp/krb5cc_1000
Default principal: [email]kylea@XXXXXXXX.AD[/email]

Valid starting     Expires            Service principal
10/24/08 21:08:36  10/25/08 07:08:39  krbtgt/INNOPARK.AD@INNOPARK.AD
	renew until 10/25/08 21:08:36

[/INDENT]


And I can see the LDAP server 

kylea@kylea-e6500:~$ net ads info
LDAP server: 172.16.1.114
LDAP server name: ifdc99.XXXXXXX.ad
Realm: XXXXXXXX.AD
Bind Path: dc=XXXXXXX,dc=AD
LDAP port: 389
Server time: Fri, 24 Oct 2008 21:10:42 EST
KDC server: 172.16.1.114
Server time offset: -1

But I cannot for the life of me get wbinfo to work (it used to) and logging I get the errors below:

If anyone has time can you try and get it working and send me some info.

I have tried the link  

[https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto?highlight=(stop)|(samba)|(howto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto?highlight=(stop)|(samba)|(howto)) (its for 8.04)

but its not quite right.

Oct 24 20:46:01 kylea-e6500 login[13627]: pam_winbind(login:auth): request failed: Access denied, PAM error was System error (4), NT error was NT_STATUS_ACCESS_DENIED

HAVE spent days on it.

---

