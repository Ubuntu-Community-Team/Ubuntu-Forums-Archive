---
title: "3DM2 3ware issues"
date: 2008-11-19
forum: x86 64-bit Users
---

### Post by DarkPhoenixTSi on 2008-11-19
hey guys,

I was able to install the 3ware 3DM2 software on my server (Ubuntu 8.04 64bit) but for some reason I get the following error when attempting to start the software.

```
(0x0C:0x0005): Failed to start listening socket
```

I am trying to troubleshoot an array rebuild that is stuck at 72% on a 9650SE 12L Raid Card.

Thanks to all that can help.

---

### Post by mogliii on 2008-11-19
Hi,

Maybe 3DM2 is not installed.
Apparently it uses uname -i/-p to determine the architecture. However Ubuntu Kernel returns "unknown", so the installer refuses to proceed.

I am not sure if this is the case for you. You might also try tw_cli from the command line.

If you use the 3DM2 installer, you can force it to use console mode , eg.
```
./setupLinux_x86.bin -console
```

I did not fix it on my computer yet as I didn't have time/need.

---

### Post by DarkPhoenixTSi on 2008-11-21
I installed both the CLI and the 3DM2 from Synaptic using the Unofficial Debian Repository. Driving me nuts!!

Thanks for you help.

---

### Post by xxsludgexx on 2009-03-08
Here's what I did that fixed it:
all in the terminal

sudo mv /bin/uname /bin/uname.dist

then create a new file named /bin/uname whose contents are:
#!/bin/bash
echo "x86"

then in the terminal:
sudo chmod 755 /bin/uname

then run the installer
./setupLinux_x86.bin -console

let it do it's thing

then:
sudo rm /bin/uname
sudo mv /bin/uname.dist /bin/uname

done and done

---

### Post by gotmonkey on 2009-03-21
> **xxsludgexx said:**
> Here's what I did that fixed it:
all in the terminal

sudo mv /bin/uname /bin/uname.dist

then create a new file named /bin/uname whose contents are:
#!/bin/bash
echo "x86"

then in the terminal:
sudo chmod 755 /bin/uname

then run the installer
./setupLinux_x86.bin -console

let it do it's thing

then:
sudo rm /bin/uname
sudo mv /bin/uname.dist /bin/uname

done and done

Thanks for the post, I was having a problem installing the 3ware software. This did the trick.

---

