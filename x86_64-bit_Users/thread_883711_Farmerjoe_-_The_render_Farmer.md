---
title: "Farmerjoe - The render Farmer"
date: 2008-08-08
forum: x86 64-bit Users
---

### Post by flufin on 2008-08-08
hi to all. I new to ununtu.
I have a major problem and need your help to solve it :(
here what I have and what I need
I have one master computer x86 64 ubuntu and 8 slaves
farmer joe works on my master computer but i have no clue how to start farmerjoe on at least one slave.
this is guide 
[http://blender.formworks.co.nz/farmerjoe/README.html](http://blender.formworks.co.nz/farmerjoe/README.html)
but this part makes me confused
# LINUX

Here is the line I have in my /etc/fstab on my linux slaves

//<master server>/farmerjoe /render smbfs guest,uid=lobo,gid=lobo 0 0

which mounts the shared directory on /render when they boot up. 

please help me with this slave computers. 
I'll send burger king via fedex to everyone who help me  :mrgreen:

---

### Post by cariboo on 2008-08-08
> //<master server>/farmerjoe /render smbfs guest,uid=lobo,gid=lobo 0 0

From what I can see all the slaves mount the farmerjoe directory on your master server to a directory called render.

So each of your slave has to have a directory named render in the root directory and in the above example they belong to user lobo group lobo

Hope this clears things up a bit.

Jim

---

