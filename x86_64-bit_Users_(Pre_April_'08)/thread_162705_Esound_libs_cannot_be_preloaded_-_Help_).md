---
title: "Esound libs cannot be preloaded - Help :)"
date: 2006-04-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by ivangotoy on 2006-04-19
i run my ubuntu amd64 happily (breezy 5.10) but i decided at some point to 

manage Skype sound despotism.

first of all let me say : i run a statically untarred 32 bit skype via console command 

using "linux32 ./skype"

then... it is pointless to discuss Skype OSS addiction here

i found some info about Esound which could solve the problem but alas :(

so i compiled esound-0.2.36 and successfully installed it on my machine.

when i try "esd" command i get a message that esound is already running and 

thus i am sure it works somehow :)

now comes the interesting thing :

root@ubuntu-amd64:/home/ivan/Desktop/SKYPE# esddsp -m ./skype ERROR: 

ld.so: object '/usr/local/lib/libesddsp.so.0' from LD_PRELOAD cannot be preloaded: 

ignored.

ERROR: ld.so: object '/usr/local/lib/libesd.so.0' from LD_PRELOAD cannot be 

preloaded: ignored.

my Skype works after that error output but again using OSS
  
i tried : LD_PRELOAD="/usr/lib/libesd.so.0 /usr/lib/libesddsp.so.0"

and  export LD_PRELOAD but it did not help 

if someone has any idea how to make skype more sound resources tolerant 

please tell me 

thank you

---

