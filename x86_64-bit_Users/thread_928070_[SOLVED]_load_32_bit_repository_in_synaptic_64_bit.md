---
title: "[SOLVED] load 32 bit repository in synaptic 64 bit"
date: 2008-09-23
forum: x86 64-bit Users
---

### Post by sjbaugh on 2008-09-23
I wish to get involved in a third-party open-source project. The project has a debian repository. The web site tels me to give the apt command:

deb [http://paparazzi.enac.fr/ubuntu](http://paparazzi.enac.fr/ubuntu) hardy main

When I do this it is accepted by Synaptic in:
Settings>Repositories>Third Party Software>Add
but when I reload I get:
Failed to fetch deb [http://paparazzi.enac.fr/ubuntu](http://paparazzi.enac.fr/ubuntu) hardy main
/binary-amd64/Packages.gz  404 Not Found

When I look at the url there is .../main/binary-i386/Packages.gz

Is there a way to force synaptic to load this?

Thanks, Steve, England

---

### Post by Kilz on 2008-09-23
> **sjbaugh said:**
> I wish to get involved in a third-party open-source project. The project has a debian repository. The web site tels me to give the apt command:

deb [http://paparazzi.enac.fr/ubuntu](http://paparazzi.enac.fr/ubuntu) hardy main

When I do this it is accepted by Synaptic in:
Settings>Repositories>Third Party Software>Add
but when I reload I get:
Failed to fetch deb [http://paparazzi.enac.fr/ubuntu](http://paparazzi.enac.fr/ubuntu) hardy main
/binary-amd64/Packages.gz  404 Not Found

When I look at the url there is .../main/binary-i386/Packages.gz

Is there a way to force synaptic to load this?

Thanks, Steve, England

Not in synaptic. Also never, ever, ever force install 32bit libraries. They could overwrite existing 64bit libraries and make your system unstable.

You can use [getlibs]("http://ubuntuforums.org/showthread.php?t=474790") to safely install 32bit software, forcing an application is ok, bu never libraries.

Since its development work, you might want to do this development in a 32bit virtual machine if you have room.

---

### Post by sjbaugh on 2008-09-23
Klitz,

I see your point about the libraries. I already have VirtualBox running under Ubuntu (it's running another Linux distro I wanted to try), so I could create a 32 bit Hardy installation in it. This does seem the best way to go.

Thanks,

Steve

---

### Post by Kilz on 2008-09-23
> **sjbaugh said:**
> Klitz,

I see your point about the libraries. I already have VirtualBox running under Ubuntu (it's running another Linux distro I wanted to try), so I could create a 32 bit Hardy installation in it. This does seem the best way to go.

Thanks,

Steve

Its always best to have a sandbox, and a virtual machine is a perfect one. Good luck.

---

### Post by sjbaugh on 2008-09-23
Kilz,

Yes, it is a good idea to insulate its goings-on from the main OS!

I have set up a 32 bit Virtual Machine and I been able to install the software on it.

Thanks for your sound advice,

Steve

---

