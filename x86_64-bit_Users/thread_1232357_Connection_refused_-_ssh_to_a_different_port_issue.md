---
title: "Connection refused - ssh to a different port issue"
date: 2009-08-05
forum: x86 64-bit Users
---

### Post by emamm on 2009-08-05
Hello

I had /etc/ssh/ssh_config edited in order to change the default port to 45022.  After editing, I issued the command /etc/init.d/ssh restart to make the changes available.

Unfortunately when I issue the command ssh -p 45022 -l xxx  192.168.1.3, the system returns an error msg: ssh: connect to host 192.168.1.3 port 45022: Connection refused.  

There is no problem if ssh uses the default port.

Have I done something wrong?

many thanks

Ed

---

