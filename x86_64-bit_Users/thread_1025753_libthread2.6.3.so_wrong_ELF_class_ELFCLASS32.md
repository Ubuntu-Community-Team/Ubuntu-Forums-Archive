---
title: "libthread2.6.3.so: wrong ELF class: ELFCLASS32"
date: 2008-12-30
forum: x86 64-bit Users
---

### Post by jutaymfm on 2008-12-30
Hi,
i trying to execute a Oracle DBA monitoring tool (named ASHMON/PERFVISION OEMLITE - [www.perfvision.com](www.perfvision.com)) but i received the following error:

./ashmon.sh
Error in startup script: couldn’t load file “/app/oracle/ashmon/bin/../lib/thread2.6.3/libthread2.6.3.so”: /app/oracle/ashmon/bin/../lib/thread2.6.3/libthread2.6.3.so: wrong ELF class: ELFCLASS32
while executing
“load $env(MON_SHARED_LIB)/../lib/thread2.6.3/libthread2.6.3.so”
(file “../funcs/begin.tcl” line 168)

I logged this error in the following blog of perfvision team, but i still got no answer (you can see my request in [http://ashmasters.com/ash-tools/](http://ashmasters.com/ash-tools/) and the actions that i have taken).
My plataform is UBUNTU 8.10 x86_64

I need a help.

---

