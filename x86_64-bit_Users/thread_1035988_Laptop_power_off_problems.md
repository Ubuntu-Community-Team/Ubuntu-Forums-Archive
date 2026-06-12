---
title: "Laptop power off problems"
date: 2009-01-10
forum: x86 64-bit Users
---

### Post by Shadowclaw on 2009-01-10
Hello everybody, not sure if this is the right forum for my problem but oh well.

I've been dual-booting Linux for several years and have just recently switched from Fedora to Ubuntu .  (easier wireless support:)).  Any way my problem is this: after running Ubuntu 8.04 under a virtual machine for a while to make sure it would work for me, I installed 8.04 on my laptop (Compaq Presario V6000) and while everything works fine, the computer emits a loud beep (not sure if its a bios beep or not) when ever I tell the computer to shut down, restart, etc.  Basically anything that will shut off the power.  Ubuntu also did this while running under the virtual machine as well.  Whether or not the speakers are muted has no effect.  This behavior has continued after updating to 8.10 as well.

Any advice would be appreciated.  It doesn't seem to effect system performance but it is rather annoying.

---

### Post by paddy2706 on 2009-01-10
would you try to put your computer to standby, then resume and check for any obvious messages in either /var/log/syslog /var/log/dmesg?

---

### Post by Shadowclaw on 2009-01-11
Ok I look at the logs and I didn't see anything out of the ordinary.  However, it didn't beep when I told it to into standby, just when I tell it to restart, hibernate, or shutoff.

---

### Post by Yellow Pasque on 2009-01-11
I'm guessing it's the system speaker. To test this, try removing the pc speaker kernel module(s) before you shut down.
```
sudo modprobe -r pcspkr
sudo modprobe -r snd_pcsp
```
If that's the problem, you can permanently solve it by blacklisting the kernel modules if it annoys you. Open your blacklist file with:
```
gksudo gedit /etc/modprobe.d/blacklist
```
Copy and paste this at the end of the file:
```
blacklist pcspkr
blacklist snd_pcsp
```
Save and quit. Note that this won't take effect until the next boot, so the beep will annoy you one last time unless you modprobe -r the module(s) again.

---

### Post by Shadowclaw on 2009-01-12
> **Temüjin said:**
> I'm guessing it's the system speaker. To test this, try removing the pc speaker kernel module(s) before you shut down.
```
sudo modprobe -r pcspkr
sudo modprobe -r snd_pcsp
```
If that's the problem, you can permanently solve it by blacklisting the kernel modules if it annoys you. Open your blacklist file with:
```
gksudo gedit /etc/modprobe.d/blacklist
```
Copy and paste this at the end of the file:
```
blacklist pcspkr
blacklist snd_pcsp
```
Save and quit. Note that this won't take effect until the next boot, so the beep will annoy you one last time unless you modprobe -r the module(s) again.

Thank you, that fixed it.

---

