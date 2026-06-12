---
title: "mounting to my G5 from a linux CLI..."
date: 2006-05-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by tombalkwill on 2006-05-07
As a relatively new linux user I would really appreciate anyones help on this.

I am currnently running a linux box allongside a mac G5. The mac has a RAID attached which I need to be able to use from within linux (for video files). It is vital that it is mounted as a mountpoint. This works well in other setups where the secondary machine is acting as a server. But my mac is not.

I can login to the mac through ssh...

$ ssh username@10.0.0.10

After typing my password I have logged in OK and can see all files, including the RAID. But the bespoke software I am running rewuires a mountpoint to use the files. I suspect NFS could help me, or some way of setting the mac to have a host name available to replace the "username@10.0.0.10" bit.

Any suggestions? Thanks in anticipation...:)

---

### Post by eddie303 on 2006-05-07
Look out for sshfs, you can mount a remote partition via ssh, or using NFS, you tell in /etc/exports what to share in which manner, and to whom, such as:
/usr/local   192.168.0.1(ro) 192.168.0.2(ro)
/home        192.168.0.1(rw) 192.168.0.2(rw)
then on the linux box:
mount othermachine:/home /<local mount point>

---

### Post by tombalkwill on 2006-05-07
Thanks for the repply, eddie.

So I am editing the /etc/exports on the G5? Can I do that?

---

### Post by eddie303 on 2006-05-07
[QUOTE=tombalkwill]Thanks for the repply, eddie.

So I am editing the /etc/exports on the G5? Can I do that?[/QUOTE]
If it has the same nfs server, which Linux has, it should be that way. Right now I am installing sshfs on my box, it is a mount tool to mount filesystems via ssh, I share my experience in a couple of minutes :)

---

### Post by tombalkwill on 2006-05-07
Eddie you are a good man. Thanks.

---

### Post by eddie303 on 2006-05-07
Thanks :)

so, try with sshfs, it may be much simple:
sudo apt-get install sshfs

then:

sshfs user@10.0.0.10:/the/directory/you/want/to/mount /where/to/mount

then to umount:

fusermount -u /where/to/mount 

:)

---

### Post by tombalkwill on 2006-05-07
Brilliant. I will try it when I get home.

Cheers for that.

:D

---

