---
title: "how can i install oracle 10g on xubuntu 64?"
date: 2008-11-13
forum: x86 64-bit Users
---

### Post by lnthai2002 on 2008-11-13
Hi guys,
I am runnung xubuntu 8.04 x64 on my laptop. I need to install oracle 10g (both client and server) so that i can test my ruby on rails application. I know lot of people would prefer 32bit oracle however, since my ruby is 64bit and thus the DB connector must be built agains this ruby version, i can not use 32bits oracle server. If anyone has any idea or documentation on how to set up oracle 10g x64 on ubuntu 64, please let me know
Thanks in advance.
Thai

---

### Post by doorman on 2009-01-21
hy!

[this article]("http://littlebrain.org/2008/05/12/how-to-install-oracle-xe-in-ubuntu-64-bit/") looks promising. Haven't tried the method yet, but when/if I do, I'll post the results

EDIT: tried the instructions read in the article mentioned and the database is up & running!

---

### Post by RomanIvanov on 2009-01-21
How I did it:
1. sudo dpkg -i .....
2. configure
3. gedit /usr/lib/oracle/xe/app/oracle/product/10.2.0/server/bin/oracle_env.sh
replace
NLS_LANG=?$ORACLE_HOME/bin/nls_lang.sh? > NLS_LANG='$ORACLE_HOME/bin/nls_lang.sh'

run /usr/lib/oracle/xe/app/oracle/product/10.2.0/server/bin/oracle_env.sh

4.
or to ease .. To solve your problem related with

nls_lang.sh: 114: [[: not found

during your bash session is just to edit the "nls_lang.sh" file to use the proper SHELL that you use.
let say .. if you use BASH .. you should change (as root or sudo) the first line in the "nls_lang.sh" from
#! /bin/sh
to
#! /bin/bash

4.1 set "<YOUR USER NAME>" in DBA group
4.2 Restart PC

5. If you have problem with running of HomeWeb Page do this:
	in sqlplus "exec dbms_xdb.sethttpport(8087);"
	to apply chages: "sudo /etc/init.d/oracle-xe force-reload

!!!!!and after each restart to RUN DB "sudo /etc/init.d/oracle-xe force-reload"

6. If you choose to do not run oracle on PC start up please use 
"sudo /etc/init.d/oracle-xe force-reload" each time before using oracle.

Edit your .bashrc file to include the lines:
ORACLE_HOME=/usr/lib/oracle/xe/app/oracle/product/10.2.0/server
PATH=$PATH:$ORACLE_HOME/bin
export ORACLE_HOME
export ORACLE_SID=XE
export PATH

For more information:
Uninstall\Uninstall: [http://download.oracle.com/docs/cd/B25329_01/doc/install.102/b25144/toc.htm#CIHBCFDD](http://download.oracle.com/docs/cd/B25329_01/doc/install.102/b25144/toc.htm#CIHBCFDD)

Install: 
[http://forums.oracle.com/forums/thread.jspa?messageID=1542334](http://forums.oracle.com/forums/thread.jspa?messageID=1542334)
[http://forums.oracle.com/forums/thread.jspa?messageID=3135330&#3135330](http://forums.oracle.com/forums/thread.jspa?messageID=3135330&#3135330)

---

### Post by isparkes on 2009-10-08
I did this on 8.04 X86-64 - I think the how to is pretty detailed. Once it is bottomed out completely (hint hint, please comment on the procedure) I'll put in in as a "How To".

There's a bit more to it than first meets the eye, in terms of installing the required libraries for 32/64 bit software and compilation, and setting the correct kernel parameters.

It should all be in the guide:

[http://blog.open-bss.com/?p=23](http://blog.open-bss.com/?p=23)

---

