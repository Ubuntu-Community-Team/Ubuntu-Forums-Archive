---
title: "OSX Server logon and other network tasks"
date: 2006-03-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by ashembers on 2006-03-06
Hello,

I am trying to help out a under-funded school that doesn't have an adequate computer lab by attaining donated computers for them and loading them up with Ubuntu. I'm pretty adept at the Windows side of networking with Samba, but they have Mac OS X Server for login, home drives, and directory services. Haven't gone onsite to poke around the server itself, and I honestly wouldn't know where to begin, so I have to ask:

1- Are there any good references for Mac OS X Server that might cover Samba clients? I'd like to read up on this for more info, & any other advice is most welcome!!!

2- How would I handle making a Gnome desktop shortcut for the currently logged-in user's home folder on the OS X server? 

3- Aside from time sync, is there anything else I should be paying attention to with this setup? Anything special to get Samba working with the Mac directory?

Thank you so much!!!

---

### Post by lucky12 on 2006-03-07
I am also in the same boat.  We are running Mac OS X server and would love to use edubutu on some old Windows machines.  I am trying to figure a way to have the edubutu machine authenticate to the Mac server?  Any help would be great.:D

---

### Post by anders_gud on 2006-03-09
What version of OS X server is it?
Maybe there is a possibility of getting LDAP auth working...

Thinking of switching the other way around in my lab, from OS X server to straight Ubuntu/debian servers, tired of all that overhyped proprietary stuff (PrintServer stinks, Netinfo/AuthServer mystifications, no real quota support, AFP user limits, no good CLI docs/manpages, version incompabilities)

---

### Post by lucky12 on 2006-03-09
[QUOTE=anders_gud]What version of OS X server is it?
Maybe there is a possibility of getting LDAP auth working...

Thinking of switching the other way around in my lab, from OS X server to straight Ubuntu/debian servers, tired of all that overhyped proprietary stuff (PrintServer stinks, Netinfo/AuthServer mystifications, no real quota support, AFP user limits, no good CLI docs/manpages, version incompabilities)[/QUOTE]

[COLOR="Blue"]We are running Mac OS X server 10.4, I am almost positive.  We are auth through LDAP.  Switching the other way around would most likly be a big stretch for us.  I am just trying to keep alive some of our older PC's and edubutu is an outstanding way to do that.[/COLOR]

---

### Post by anders_gud on 2006-03-09
Hi Lucky!
If you already are on LDAP there should be no problems Integrating ubuntu/edubunu. Just check out pam-ldap, ssl and nsswitch configuration on the workstations, I suppose you can automount homes from the server via nfs or samba (from LDAP) or from config files on the edubuntu stations (autofs).

(this guide is for the other way round but contains some info on OS X specfic LDAP stuff)
[http://www.spack.org/wiki/AppleOsxIntegrationWithOpenLdap](http://www.spack.org/wiki/AppleOsxIntegrationWithOpenLdap)

---

### Post by lucky12 on 2006-03-09
anders_gud, 
Thanks for the quick response. The info is great.  The problem is that I am still a little bit of a novice when it comes to the network end of things.  Is there an easy to use set of directions? I am also new to the terminal.

Thanks a bunch

---

### Post by anders_gud on 2006-03-09
As I'm new to LDAP myself, I found these sites helpful: 

For debian based distros like Ubuntu
[http://wiki.debian.org/?LDAPAuthentication](http://wiki.debian.org/?LDAPAuthentication)
[http://aqua.subnet.at/~max/ldap/](http://aqua.subnet.at/~max/ldap/)

And the real thing, openldap.org (and links to LDAP admin tools...)
[http://www.openldap.org/doc/admin23/](http://www.openldap.org/doc/admin23/)

samba-ldap setup:
[http://www.idealx.org/prj/samba/smbldap-howto.fr.html](http://www.idealx.org/prj/samba/smbldap-howto.fr.html)

ssl certificates on debian:
[http://www.debian-administration.org/articles/284](http://www.debian-administration.org/articles/284)

autofs:
[http://wiki.bfh.ch/index.php/LDAP_autofs_howto](http://wiki.bfh.ch/index.php/LDAP_autofs_howto)

And the OS X side of things (old docs but then I still run 10.2.8 server :))
[http://www.macdevcenter.com/pub/a/mac/2004/05/25/ldap.html](http://www.macdevcenter.com/pub/a/mac/2004/05/25/ldap.html)
[http://www.padl.com/Articles/AdvancedOpenDirectoryConf.html](http://www.padl.com/Articles/AdvancedOpenDirectoryConf.html)


Cheers!
Anders

---

### Post by lucky12 on 2006-03-10
Thank you very much.  We'll see what I can do.

Lucky12

---

