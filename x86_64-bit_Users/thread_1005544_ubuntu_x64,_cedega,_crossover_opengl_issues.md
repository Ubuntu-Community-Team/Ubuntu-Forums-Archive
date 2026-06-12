---
title: "ubuntu x64, cedega, crossover opengl issues"
date: 2008-12-08
forum: x86 64-bit Users
---

### Post by Nossie on 2008-12-08
Hi,

I had Wow running perfectly in crossovergames and cedega passed all tests for graphics hardware... I then I think installed a nvidia update and I now cant get anything at all to work?

wow now says I dont have a compatible 3d hardware renderer,
cedega fails opengl tests but passes 3d acceleration
vmware says hardware acceleration is now disabled when I run it


thing is, compiz was working fine and still is....

I'm wondering if this is something to do with a 32bit graphics layer I'm missing but I cant find out what I need...

Any ideas on further things I could do to track down the problem? anyone else have this issue suddenly appear today?

cheers,
Ian.

**EDIT:** resolved by reinstalling nvidia drivers

---

### Post by Nossie on 2008-12-08
problems seem to be permissions related....

I get direct rendering with sudo but not without... can anyone tell me how to fix this?

If I run nvidia x server settings as root I get direct rendering enabled... but disabled without root..

same with glxgears.


from what I've worked out

```

ian@Jupiter-Ubuntu:~$ ls -al /dev/nvidia*
crw-rw---- 1 root video 195,   0 2008-12-08 16:44 /dev/nvidia0
crw-rw---- 1 root video 195, 255 2008-12-08 16:44 /dev/nvidiactl
ian@Jupiter-Ubuntu:~$ 

```

shouldnt the group be 44? what is the best way of changing this back?



cheers. Ian

---

