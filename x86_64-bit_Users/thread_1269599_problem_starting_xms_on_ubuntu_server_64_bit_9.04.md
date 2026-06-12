---
title: "problem starting xms on ubuntu server 64 bit 9.04"
date: 2009-09-18
forum: x86 64-bit Users
---

### Post by Maleficent1 on 2009-09-18
Having problems getting xms mail server to work
on Ubuntu server 64bit v9.04

Installed and copied all the file the files are in there proper location
*tar** xvzf xms-linux-nojvm.tar.gz -C /opt*[I]
 ln -s /opt/xms-2.0.1-linux-nojvm /opt/xmserver
 cp -f xmserver.jar-updated-20071107 /opt/xmserver/lib/xmserver.jar
update-rc.d xmserver start 30 2 3 4 5 . stop 30 0 1 6 .[/I]

when i do the following
*/etc/init.d/xmserver start*
I get *exec: 532: /opt/xms-2.0.1-linux-nojvm/./xmserver: not found*

I think this has something to do with running 64 bit server but not sure what exactly.

---

