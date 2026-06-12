---
title: "apache autostart"
date: 2006-08-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by alexn on 2006-08-28
I'm bewbe to ubuntu and don't know how to make my source installed apache to run on boot. At the red hat I used chkconfig. What should  I do?
Thanks.

---

### Post by RAOF on 2006-08-28
Why did you build it from source?  The Ubuntu packaged apache sets everything up for you :).

If you've got a daemon script in /etc/init.d, you could use **bum** (it's in the repositories) to add it to your startup services.

---

### Post by alexn on 2006-08-29
> **RAOF said:**
> Why did you build it from source?  The Ubuntu packaged apache sets everything up for you :).

If you've got a daemon script in /etc/init.d, you could use **bum** (it's in the repositories) to add it to your startup services.

I prefer the source builded.:D 
How to install **bum**? 
If use the ubuntu apache hackage, could You say, are there any ubuntu packages for ***mod_perl*** and ***libapreq2***?:-k 

Thanks.

---

### Post by mw888 on 2006-08-29
The simple way would be to add the apache startup command (e.g. /usr/local/apache/bin/apachectl start) to /etc/rc.local.

---

### Post by RAOF on 2006-08-29
> **alexn said:**
> I prefer the source builded.:D 
How to install **bum**? 
If use the ubuntu apache hackage, could You say, are there any ubuntu packages for ***mod_perl*** and ***libapreq2***?:-k 

Thanks.

Yes.  **aptitude search apache** shows:
```
...
p   libapache2-mod-annodex          - Provides server-side support for Annodex m
p   libapache2-mod-apreq2           - generic Apache request library - Apache mo
p   libapache2-mod-auth-kerb        - apache2 module for Kerberos authentication
p   libapache2-mod-auth-mysql       - Apache 2 module for MySQL authentication
p   libapache2-mod-auth-pam         - module for Apache2 which authenticate usin
p   libapache2-mod-auth-pgsql       - Module for Apache2 which provides pgsql au
p   libapache2-mod-auth-plain       - Module for Apache2 which provides plaintex
p   libapache2-mod-auth-sys-group   - Module for Apache2 which checks user again
p   libapache2-mod-cband            - An Apache 2 module for bandwidth limiting
p   libapache2-mod-chroot           - run Apache in a secure chroot environment
p   libapache2-mod-dnssd            - Apache 2 module which adds Zeroconf suppor
p   libapache2-mod-encoding         - Apache2 module for non-ascii filename inte
p   libapache2-mod-fastcgi          - Apache 2 FastCGI module for long-running C
p   libapache2-mod-fcgid            - an alternative module compat with mod_fast
p   libapache2-mod-geoip            - GeoIP support for apache2
p   libapache2-mod-jk               - Apache 2 connector for the Tomcat Java ser
p   libapache2-mod-layout           - Apache2 web page content wrapper
p   libapache2-mod-ldap-userdir     - Apache2 module that provides UserDir looku
p   libapache2-mod-macro            - Create macros inside apache2 config files
p   libapache2-mod-mime-xattr       - Apache2 module to get MIME info from files
c   libapache2-mod-mono             - Run ASP.NET Pages on UNIX with Apache 2 an
p   libapache2-mod-musicindex       - Browse, stream, download and search throug
p   libapache2-mod-ngobjweb         - Apache2 module for the SOPE application se
p   libapache2-mod-perl2            - Integration of perl with the Apache2 web s
p   libapache2-mod-perl2-dev        - Integration of perl with the Apache2 web s
p   libapache2-mod-perl2-doc        - Integration of perl with the Apache2 web s
c   libapache2-mod-php4             - server-side, HTML-embedded scripting langu
c   libapache2-mod-php5             - server-side, HTML-embedded scripting langu
p   libapache2-mod-proxy-html       - Apache2 filter module for HTML links rewri
p   libapache2-mod-python           - Apache 2 module that embeds Python within
p   libapache2-mod-python-doc       - Apache 2 module that embeds Python within
p   libapache2-mod-python2.4        - Apache 2 module that embeds Python 2.4 wit
p   libapache2-mod-rpaf             - module for Apache2 which takes the last IP
p   libapache2-mod-ruby             - Embedding Ruby in the Apache2 web server
p   libapache2-mod-scgi             - Apache module implementing the SCGI protoc
p   libapache2-mod-security         - Tighten web applications security for Apac
p   libapache2-mod-speedycgi        - apache2 module to speed up perl scripts by
p   libapache2-mod-suphp            - Apache2 module to run php scripts with the
p   libapache2-mod-vhost-ldap       - Apache 2 module for Virtual Hosting from L
p   libapache2-mod-xmlrpc2          - XMLRPC Server module for Apache2 web serve
p   libapache2-modxslt              - XSLT processing module for Apache 2.0.x ba
...

```

To install stuff in Ubuntu, you use either:
GUI:
1) Synaptic package manager (System->Administration->Synaptic)
2) Add/Remove programs (more simple)

command-line:
1) aptitude (preferred) or apt-get
Typical usage is "sudo aptitude install *pkgname*"

So, for example:
```

sudo aptitude install apache2 libapache2-mod-perl2 libapache2-mod-apreq2

```
would install apache2, -mod-perl, and -mod-apreq2, all their dependencies, and set them up.

---

### Post by alexn on 2006-08-30
> **RAOF said:**
> 
To install stuff in Ubuntu, you use either:
GUI:
1) Synaptic package manager (System->Administration->Synaptic)
2) Add/Remove programs (more simple)

command-line:
1) aptitude (preferred) or apt-get
Typical usage is "sudo aptitude install *pkgname*"

So, for example:
```

sudo aptitude install apache2 libapache2-mod-perl2 libapache2-mod-apreq2

``` would install apache2, -mod-perl, and -mod-apreq2, all their dependencies, and set them up.


Thanks, **RAOF** - that usefull information.

Now my way:
I'm running server edition, so I need custom applications to be installed. For example, I need perl 5.8.8.

How solve "apache starting on boot":

[LIST=1]
[*]cope ***apachectl*** file from apache's /bin directory to /etc/init.d
[*]sudo chmod +x /etc/init.d/apachectl
[*]sudo update-rc.d apachectl defaults[/LIST]
Wow, it works...](*,)

---

