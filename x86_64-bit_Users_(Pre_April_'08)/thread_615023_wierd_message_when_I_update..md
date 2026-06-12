---
title: "wierd message when I update."
date: 2007-11-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by ve3rpm on 2007-11-16
I've been getting this for a couple of weeks now.  Update manager tells me to update and seems to get some updates in and then i GET THIS MESSAGE.  I'm thinking that it's important.

E: mhc-utils: subprocess post-installation script returned error exit status 10

Any suggestions?  thanx Dan  BTW I just don't miss windows, at all.

---

### Post by bren on 2007-11-16
and i got the wierd message that some packages could not be downloaded by the updater with the following info as text

> W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbfs_3.0.26a-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbfs_3.0.26a-1ubuntu2.1_i386.deb)
  403 Forbidden


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.26a-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.26a-1ubuntu2.1_i386.deb)
  403 Forbidden


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba_3.0.26a-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba_3.0.26a-1ubuntu2.1_i386.deb)
  403 Forbidden


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.26a-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.26a-1ubuntu2.1_i386.deb)
  403 Forbidden


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.26a-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.26a-1ubuntu2.1_i386.deb)
  403 Forbidden


---

### Post by shad0w_walker on 2007-11-16
I'm afraid i don't have any suggestions for your original issue off the top of my head. The new error however is due to a error in the latest samba update. The files have had access restricted to prevent users updating to the dodgy packages. It's being worked on right now and from what I have heard hopefully should be fixed soon.

---

### Post by ve3rpm on 2007-11-16
k then, I'll just keep checking back.  It hasn't affected me yet that I can tell, so I suppose that's the joy of these forums.  thanx! Dan

---

### Post by snkmad on 2007-11-16
Im having the same samba problems.
Ill just wait, since i dont access other machines using smb here.

Off-topic: is it safe to update the latest nvidia-glx-new from update mananger? Since theres no changelog included, and here its running so smooth, im afraid of breaking things....

---

