---
title: "Oops! (sudo chown -R www-data:www-data) Please help recover permissions."
date: 2008-07-24
forum: x86 64-bit Users
---

### Post by DigitalisAkujin on 2008-07-24
First post, be gentle :)

I made the mistake of forgetting what my cd was when I ran this command from /var.

[sudo chown -R www-data:www-data]

So now while the system is stable I had a few issues (like mySQL not working right cause it had no permissions).

I already fixed that one (/var/lib/mysql) but I'm not all knowing about every single thing that runs on the machine.

Can anyone please refer me to a list of other directories in /var I might wanna fix as well?

```
henry@misbelle:/var$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 8.04.1
Release:        8.04
Codename:       hardy

```
I installed everything just last night.

I also installed ubuntu-desktop through apt-get last night so keep in mind there's a lot of packages the server doesn't include stock.

Thanks :)

---

### Post by cariboo on 2008-07-25
Here is a list of /var:

```
drwxr-xr-x  2 root root  4096 2008-07-24 09:39 backups
drwxr-xr-x 18 root root  4096 2008-07-14 17:28 cache
drwxr-xr-x  2 root root  4096 2008-06-30 12:52 crash
drwxr-xr-x  2 root root  4096 2008-07-12 12:21 games
drwxr-xr-x 57 root root  4096 2008-07-23 21:17 lib
drwxrwsr-x  2 root staff 4096 2008-04-28 11:37 local
drwxrwxrwt  2 root root    60 2008-07-24 02:05 lock
drwxr-xr-x 16 root root  4096 2008-07-24 11:51 log
drwxrwsr-x  2 root mail  4096 2008-07-23 08:58 mail
drwxr-xr-x  2 root root  4096 2008-07-12 11:55 opt
drwxr-xr-x 18 root root   780 2008-07-24 12:49 run
drwxr-xr-x  9 root root  4096 2008-07-18 20:54 spool
drwxrwxrwt  3 root root  4096 2008-07-24 11:58 tmp
```

as you can see all of the directories are owned by root, but different groups.

Jim

---

