---
title: "Gutsy 64 + custom kernel + nvidia drivers = won't reboot?"
date: 2007-10-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by James79 on 2007-10-22
Hi guys&gals,

I built myself a simple HTPC around an Asus M2NPV-VM (onboard geforce 6150). It's been running Feisty32+Mythtv for seveal months now without incident. As such I've been a little hesitant to muck around with it.

Now that Gutsy has been released, I installed in on a free partition and decided I would have some fun poking and hacking away at it with all the things I've wanted to try without fear of breaking it for a change ;)

So here's what I've done so far.

- Installed Ubuntu Gutsy 64bit. 
- Downloaded the "plain vanilla" kernel source from kernel.org (2.6.23.1).
- Determined what I needed as a bare minimum for my hardware, and started hacking away the fat. Compiled my custom kernel and installed it. Reboot, everything is working fine.
- Ran the installer for Nvidia (NVIDIA-Linux-x86_64-100.14.19-pkg2.run). It compiles fine. The installer then offers to install OpenGL 32bit compatability; this fails (anyone know why it would?), but the installer doesn't seem to concerned about it and completes.
- I let it edit my xorg.conf

I reboot, and everything works great! Boot time is fast, desktop loads without incident. Enable Compiz, and everything is beautiful.

Here's the problem: I can't reboot! I can _shutdown_ just fine. But if I choose to reboot, Ubuntu goes thru its normal shutdown procedure. And just when it would normally restart the system, the screen goes blank. And that's it - frozen. The screen is blank. Even the reset button doesn't snap it out of its daze. I have to power cycle the system.

I can hear my cpu fan go to full speed (normally cool and quiet keeps it running slowly) which it always does when it is first started.

If I revert the changes to my xorg.conf to the original one (using the vesa driver), everything goes back to normal (ie I can reboot again). Changing it back to "nvidia" brings the reboot problem back.

Any insight would be appreciated!

As a side question as I continue to find new ways to break my system even further: why is it that once I started using a custom kernel I no longer have access to restriced modules? Is there a technical reason for it or is it simply Ubuntu's way of saying "you're on your own from now on!" :) I've noticed that it's now impossible to install flash (among others) via apt-get (claiming "broken packages"), for instance.

Congrats to the Ubuntu team for another great release!

---

### Post by ACLerok on 2007-10-23
Have you tried doing a "sudo shutdown -r now" from the terminal and watched the screen?  

How about tailing your /var/log/messages file to see if any funny business took place?

---

### Post by James79 on 2007-10-23
Thanks for replying.

Here are the last few lines I see after the system is booted:

> Oct 23 19:29:37 ubuntu dhcdbd: Started up.
Oct 23 19:29:39 ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Oct 23 19:29:41 ubuntu kernel: NET: Registered protocol family 17
Oct 23 19:29:43 ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
Oct 23 19:29:43 ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Oct 23 19:29:43 ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers

And here are the only lines written immediately after I give the reboot command:

> Oct 23 19:33:53 ubuntu kernel: compiz.real[5681]: segfault at 0000000000000020 rip 000000000040ee10 rsp 00007fffac69c760 error 4
Oct 23 19:33:56 ubuntu exiting on signal 15


And that's it. The next lines after that are from the subsequent startup.

I guess it's logical to assume that compiz has something to do with it, as the problem doesn't manifest itself when I'm running the default vesa driver (and hence compiz gets disabled). Why would compiz prevent my computer from rebooting but not shutdown?

---

### Post by James79 on 2007-10-23
Well I disabled compiz effects (preferences->appearance) and the error does indeed go away. But the reboot problem remains.

So compiz segfaults on shutdown but that appears to be unrelated.

So somehow the combination of my custom kernel with the nvidia 64bit driver renders my system unable to reboot for some reason.

Any ideas?

---

### Post by chris.zeman on 2007-10-30
I just had the same thing start happening. I am running Gutsy Desktop (32-bit) and changed my hostname from the network control panel. The only way into my system now is through SSH. I can enter my username and password, but Gutsy hangs at that point displaying a blank desktop.

Chris

EDIT: Just fixed it. I had changed my hostname to RC4 - Ubuntu. I guess it didn't like that.

---

