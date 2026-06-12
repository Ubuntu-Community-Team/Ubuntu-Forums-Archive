---
title: "Samba Share Permissions Issue?"
date: 2007-10-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by trmentry on 2007-10-28
I'm working on bringing up a new server and decided to give Ubuntu
7.10 64 bit a try.  I installed it to a vmware instance along with
Samba to test it out before hand while waiting for all the hardware to
show up.

I made my smb.conf file similar to what I have on my Gentoo server
that is working fine.  My goal is to have read only shares for most
users but with ability to write by admins.

This is what I have for my gentoo machine (working). (Just showing the
shares portion.)
```

[files]
       comment = Misc Files and Programs
       path = /shares/files
       valid users = @users
       admin users = @admin
       write list = @admin

```
With Ubuntu the above doesn't work at all.  Clients can't connect.
Users are added into smbpasswd and are in the 'users' group.  Admins
are in admin.  Clients get prompted for user/passwd over and over with no success. 

I followed an Ubuntu wiki on Samba and came up with this.
```

[files]
       comment = Misc Files and Programs
       path = /shares/files
       read only = yes
       create mask = 644
       directory mask = 755
       force user = nobody
       force group = nogroup
       #valid users = @users
       #admin users = @admin
       #write list = @admin

```
My clients can connect but I had to comment out the lines above to get
it to work.

So I tried this.
```

[files]
       comment = Misc Files and Programs
       path = /shares/files
       create mask = 644
       directory mask = 755
       write list = user1

```
Again, able to connect, but no joy on writes for user1.  I only have 2 admins so don't mind just putting their account names in the write list paramater rather than the group, but still Ubuntu Samba appears to ignore it.


I'm not really sure on next steps.  And confused as those options work
fine on my Gentoo install but can't get them working at all on Ubuntu.

I did find this post: [http://ubuntuforums.org/showthread.php?t=516363](http://ubuntuforums.org/showthread.php?t=516363)  but I'm not setup as a PDC and don't use scripts to map the shares on windows clients.  Its the same issue I'm having in that 
shares with user security aren't using the proper flags in smb.conf (valid users, write list, admin users, etc)  This seems to be a Ubuntu issue with Samba install as these flags work on Gentoo fine but I'm wanting to move to Ubuntu for the simple install and constancy of the rest of my systems being Ubuntu already. :)

Can someone please point me in the right direction?

Thank you

---

### Post by trmentry on 2007-10-28
I did this:

```

sudo apt-get remove samba
sudo apt-get remove samba-common
sudo mv /etc/samba/smb.conf /tmp
sudo apt-get install samba

```

And then rebuilt my smb.conf file with the original way I had it and now everything is working.  My guess is that installing Samba during install has a 'glitch' in it.

---

