---
title: "Failed to initialize HAL"
date: 2006-05-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by Slavus on 2006-05-08
Pretty much an out of box install, i got my video working with a vesa driver, and right after logging in I get this

Internal Error!
Failed to initialize HAL!

What is HAL, why do i need it, and how can i manually start it?

Also, I cant open .exe's i dont know if this has anything to do with HAL or not but it is annoying, since my mouse driver install is a .exe

---

### Post by markba on 2006-05-15
[QUOTE=Slavus]Pretty much an out of box install, i got my video working with a vesa driver, and right after logging in I get this

Internal Error!
Failed to initialize HAL!
[/QUOTE]

See this thread:
[http://www.ubuntuforums.org/showthread.php?t=174445](http://www.ubuntuforums.org/showthread.php?t=174445)

Bug is filed under:
[https://launchpad.net/distros/ubuntu...hal/+bug/37683](https://launchpad.net/distros/ubuntu...hal/+bug/37683)

---

### Post by el3ktro on 2006-06-03
[QUOTE=Slavus]Also, I cant open .exe's i dont know if this has anything to do with HAL or not but it is annoying, since my mouse driver install is a .exe[/QUOTE]

You don't man Windows .exe files don't you? .exe files are Windows executables - you can't run them under Linux!

Tom

---

### Post by nbjayme on 2006-07-04
hello,

   i encountered this experience with placing auto mountable smbfs in /etc/fstab

  if this is the case try the solution:

1) place  a noauto option in your /etc/fstab smbfs entry

2) mount network shares using /etc/rc.local
    if your network share is to be mounted to /mnt/shared then within /etc/rc.local 
    place

    mount /mnt/shared

    the mount command will further check fstab for correct mount options

Placing it in /etc/rc.local ensures that all modules are loaded before mounting the network share.

Hope this helps....

:)

---

