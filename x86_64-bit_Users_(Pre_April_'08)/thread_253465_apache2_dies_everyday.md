---
title: "apache2 dies everyday"
date: 2006-09-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by davesbedroom on 2006-09-08
I have a development server that I have loaded dapper drake on and I have a simple apache2 setup running and every day when i wake up and go to check on apache, it isn't running.

The only thing I get in the error log.

[Thu Sep 07 12:40:02 2006] [notice] Apache/2.0.55 (Ubuntu) PHP/5.1.2 mod_ssl/2.0.55 OpenSSL/0.9.8a mod_perl/2.0.2 Perl/v5.8.7 configured -- resuming normal operations
[Fri Sep 08 06:25:18 2006] [notice] caught SIGTERM, shutting down

The server doesn't get any load really, not running anything in production and there is no traffic to speak of.  I updated it apt often.

](*,)

---

### Post by p!=f on 2006-09-14
I have the very same problem. Logs are silent. There's nothing else than [06:25] [notice] caught SIGTERM, shutting down. Every day, same time.

Do you have Ubuntu Dapper Drake 6.06, 64-bit installed?

---

### Post by p!=f on 2006-09-15
Solved: in /etc/logrotate.d/apache2 change

```

/etc/init.d/apache2 restart > /dev/null

```
to
```

/etc/init.d/apache2 reload > /dev/null

```

---

### Post by davesbedroom on 2006-09-19
yes I have Ubuntu Dapper Drake 6.06, 64-bit installed

Your fix fixed my problem!! you're the man! :D 


now why isn't this a major bug that people everywhere are having problems with?

I almost switched to a different distro because something as important as apache wasn't rolling smoothly.

I did have SSL certs, do you?

---

### Post by p!=f on 2006-09-20
> **davesbedroom said:**
> yes I have Ubuntu Dapper Drake 6.06, 64-bit installed

Your fix fixed my problem!! you're the man! :D

Wasn't me but Launchpad. :)
[https://launchpad.net/distros/ubuntu/+source/apache2/+bug/23938](https://launchpad.net/distros/ubuntu/+source/apache2/+bug/23938)

> **davesbedroom said:**
> 
now why isn't this a major bug that people everywhere are having problems with?

I almost switched to a different distro because something as important as apache wasn't rolling smoothly.

Seems like it wouldn't help you much. The same "bug" is presented in other distributions. :)
Adam Conrad wrote this (read in the link above):
> 
... The default is to do a hard restart because we've seen many other instances where graceful would cause the server to die completely when some rogue extension or other segfaults as the parent reloads, leaving you with NO apache from 6:25 onward. I decided at that time that the current compromise was the lesser of two evils.

I'm still trying to figure out the best way to serve everyone well here without the world blowing up. ;)

Looks like to choose restart or reload depends on your configuration.
Check this site for differences between hard and graceful restart for more information:
[http://httpd.apache.org/docs/2.0/stopping.html](http://httpd.apache.org/docs/2.0/stopping.html)

> **davesbedroom said:**
> 
I did have SSL certs, do you?

Yes. Once they are "removed" it works just fine with the restart option.

I should note I've never experienced this when using Apache 1.3. Perhaps I should stick with it. ;)

EDIT: Forgot to mention nice utility called monit
```

apt-cache show monit
or
wajig show monit

```

---

