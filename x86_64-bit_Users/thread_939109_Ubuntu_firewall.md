---
title: "Ubuntu firewall"
date: 2008-10-05
forum: x86 64-bit Users
---

### Post by kyo007 on 2008-10-05
hi, i have problem about ubuntu firewall, i open Virtual Servers 5442 but when i check it, it's not correct, so i think i have problem with ubuntu firewall, how can i disable or allow port in ubuntu ?

Thanks.

---

### Post by nowshining on 2008-10-05
what version of ubuntu are u using??

---

### Post by Sef on 2008-10-05
Easiest way is to download ufw from the repositories.   Applications > Add/Remove > SHOW: All Available Applications > SEARCH: ufw > click on the box next to ubuntu firewall > apply changes > apply > close.

---

### Post by Yellow Pasque on 2008-10-06
```
$ ufw --help

Usage: ufw COMMAND

Commands:
  enable			Enables the firewall
  disable			Disables the firewall
  default ARG			set default policy to ALLOW or DENY
  logging ARG			set logging to ON or OFF
  allow|deny RULE		allow or deny RULE
  delete allow|deny RULE	delete the allow/deny RULE
  status			show firewall status
  version			display version information

dan@harvest:/etc$
```

If you need to do more configuration, read the manual:
```
man ufw
```

---

### Post by Yellow Pasque on 2008-10-06
I guess I should say that disabling ufw entirely isn't a good idea. Try to read the manual and set up appropriate rules. ufw aims to be easy to configure.

```
EXAMPLES
       Deny all access to port 53:

         ufw deny 53

       Allow all access to tcp port 80:

         ufw allow 80/tcp

       Allow all access from RFC1918 networks to this host:

         ufw allow from 10.0.0.0/8
         ufw allow from 172.16.0.0/12
         ufw allow from 192.168.0.0/16

       Deny access to udp port 514 from host 1.2.3.4:

         ufw deny proto udp from 1.2.3.4 to any port 514

       Allow access to udp 1.2.3.4 port 5469 from 1.2.3.5 port 5469:

         ufw allow proto udp from 1.2.3.5 port 5469 to 1.2.3.4 port 5469

```

---

