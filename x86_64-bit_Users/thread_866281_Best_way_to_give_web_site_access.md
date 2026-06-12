---
title: "Best way to give web site access"
date: 2008-07-21
forum: x86 64-bit Users
---

### Post by inphektion on 2008-07-21
I'm running a hardy 64 8.04.1 apache server.  A couple developers need ssh access to the site contents.  whats the best way to do this without giving them full access to the box.  

I know about visudo but that doesn't let them cd somewhere they don't have permissions.

What I did was created a webDevel group and made that the group on /var/www/site.  then I made www-data the owner and added the user accounts to members of webDevel.  Is this the best way?  Seems inefficient and maybe now that www-data is the owner it has too many perms.

---

### Post by inphektion on 2008-08-04
anyone with suggestions?

---

### Post by inphektion on 2008-08-05
....

---

### Post by cariboo on 2008-08-05
I would create a limited user, then only give them acces to that users directory. Create a simlynk to /var/www and then then don't need any extra acces. To create a symlink in /var/www:

```
sudo ln -s /home/<limiteduser> html
```

Then chage your docroot in in apache2.conf to point to the directory you just created. Also change ownership of /var/www back to www-data.www-data

Jim

---

