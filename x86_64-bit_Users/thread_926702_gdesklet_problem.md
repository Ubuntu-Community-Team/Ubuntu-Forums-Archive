---
title: "gdesklet problem"
date: 2008-09-22
forum: x86 64-bit Users
---

### Post by gumnaam on 2008-09-22
hi all ubuntu users.
i am new to ubuntu .i have installed gdesklet on ubuntu studio.but it does not start .it give s erro "Cannot establish connection to daemon: timeout!  "

one time it did started but gave some exception 


Starting gdesklets-daemon...
Connected to daemon in 804 milliseconds.

==========================================================[09/22/08-17:29:05]===
=== Unhandled error! Something bad and unexpected happened. ===

[EXC]
in /usr/bin/gdesklets: line 393 <module>
in /usr/bin/gdesklets: line 268 parse_command
in /usr/bin/gdesklets: line 177 __open_profile
in /usr/bin/gdesklets: line 167 __client_daemon
in /usr/lib/gdesklets/main/client.py: line 208 set_remove_command
in /usr/lib/gdesklets/main/client.py: line 38 __send
in /usr/lib/gdesklets/utils/xdr.py: line 75 recv
[EXC]/usr/lib/gdesklets/utils/xdr.py

[---]   70     chunk = ""
[---]   71     while (True):
[---]   72         try:
[---]   73             length = ord(s.recv(1))
[---]   74         except:
[ERR]>  75             raise XDRError
[---]   76 
[---]   77         if (length): chunk += s.recv(length)
[---]   78 
[---]   79         flag = s.recv(1)
[---]   80         if (flag == _CONT): continue
[---]   81 



plzzz help

---

### Post by bford16 on 2008-09-23
Maybe you are missing some dependencies? Did you try "sudo apt-get install -f" to see if anything is missing?

---

