---
title: "smbfs not working"
date: 2007-10-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by spawnlcd on 2007-10-27
Hi Everyone, 

     I have upgraded from Ubuntu Server 6.0.6.1, to 7.10, and I all of a sudden I started having problems with my smbfs mounts not loading. Here is what I did, I placed the mounting points for the smbfs on the /etc/fstab, as so:

#NAS Shared Folders

//192.168.1.xx/xx_share /NAS/xx_share smbfs auto,username=,password=

//192.168.1.xx/xx_client /NAS/xx_client smbfs auto,username=,password=

//192.168.1.xx/xx_server /NAS/xx_server smbfs auto,username=,password=

//192.168.1.xx/xx_share /NAS/xx_share smbfs auto,username=,password=

//192.168.1.xx/xx1 /NAS/xx1 smbfs auto,username=,password=

and when I issued a "mount -a", the mounts loaded, and I saw them on the "mount" output. However, as soon as I reboot the server, the mounts no longer loads. I tried issuing the "mount -a" command again, but I only get this:

Could not resolve mount point /NAS/xx
Could not resolve mount point /NAS/xx_client
Could not resolve mount point /NAS/xx_server
Could not resolve mount point /NAS/media_share
Could not resolve mount point /NAS/xx1

Another thing I am noticing is when I issue a "ls /NAS/<Any of the mounts I created>" it locks up. :(


The strange part is that I have another another Ubuntu server runnning 7.10 that is running the same smbfs configuration with no problems. Any ideas or direction would be great.

Thanks,

Rafael

---

### Post by amtam on 2007-10-27
> Could not resolve

Looks like a name-resolution issue. Can you ping your server using it's hostname?

---

