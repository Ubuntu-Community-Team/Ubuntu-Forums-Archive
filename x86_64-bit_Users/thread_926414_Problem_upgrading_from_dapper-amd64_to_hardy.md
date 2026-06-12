---
title: "Problem upgrading from dapper-amd64 to hardy"
date: 2008-09-21
forum: x86 64-bit Users
---

### Post by tim-m89 on 2008-09-21
I recently tried to upgrade from dapper to hardy changing what packages it looks for.

vim /etc/apt/sources.list
:%s/dapper/hardy/

then i did a apt-get update. apt-get upgrade. reboot.

Unfortunately though it decided to install 32 bit kernel along with various other 32 bit stuff. This left the machine failing when trying to boot up and the sshd server did not start back up. Why would it decide to use 32 bit :confused:

I've searched around and could not find anything like this. Is this a known issue?

---

