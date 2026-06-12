---
title: "GPG error : Problem with Update Manager"
date: 2006-09-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by Floren on 2006-09-10
Hi,

From one day to the next without (apparently) touching any system files I get this problem: When I try to run the Update Manager and click on check I get:

[PHP]W: GPG error: http://us.archive.ubuntu.com dapper Release: Unknown error executing gpgv 
W: GPG error: http://us.archive.ubuntu.com dapper-updates Release: Unknown error executing gpgv 
W: GPG error: http://us.archive.ubuntu.com dapper-backports Release: Unknown error executing gpgv 
W: GPG error: http://archive.canonical.com dapper-commercial Release: Unknown error executing gpgv 
W: GPG error: http://security.ubuntu.com dapper-security Release: Unknown error executing gpgv  [/PHP]

If I try 'sudo apt-get update' from the console, I get the same answer. And I also noticed that all software that I try to install with Synaptic appears as 'Not authenticated'.

Any idea what's wrong?

---

### Post by kuja on 2006-09-11
I've no idea what is wrong, but I have an idea of something that you could try.

Seeing as you really can't access apt, it makes it a tad more difficult. I would remove the ~/.gnupg directory, and run "sudo dpkg-reconfigure gnupg"

```

rm -rf ~/.gnupg
sudo dpkg-reconfigure gnupg

```

Let me know if it helps.

---

