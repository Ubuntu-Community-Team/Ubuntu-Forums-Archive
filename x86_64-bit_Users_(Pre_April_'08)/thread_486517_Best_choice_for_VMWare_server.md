---
title: "Best choice for VMWare server"
date: 2007-06-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by gheywood on 2007-06-28
Hello, 

Ultimately, I would like to get soem VMWare server images running on ubuntu. I have a few questions though.

1) Should I be running ubuntu server or ubuntu workstation?
2) If I use ubuntu server, which GUI should I be using for remote control? It looks like I intalled xfce, but people have suggested gnome (or KDE)?
3) If I want to run gnome (or a.n. other), how do I uninstall xfce and then install gnome?

Or should I just reformat the machine and install workstation?

---

### Post by 92fs on 2007-06-28
I'm running VMware Server on ubuntu 7.04 desktop 64-bit and it runs fine. I followed the instructions on ubuntuguide.org hope that helps

---

### Post by gheywood on 2007-06-28
Thanks. Looks like that could be the way to go then. I will reformat and stick it on.

---

### Post by scxtt on 2007-06-28
> 1) Should I be running ubuntu server or ubuntu workstation?if you like starting/stopping your VMs via CLI and "vmware-cmd", then go server ... or if you like to connect from another box, via VMware console - server would be fine too (using xinetd/port 902) ...
> 2) If I use ubuntu server, which GUI should I be using for remote control? It looks like I intalled xfce, but people have suggested gnome (or KDE)?what's the point of installing server if you're gonna stick a GUI on it?  and there's no real +/- to using gnome/kde/xfce w/ vmware's program ...
> 3) If I want to run gnome (or a.n. other), how do I uninstall xfce and then install gnome?you don't need to remove any of them in order to put another one on, unless you're low on space ,,,

---

### Post by gheywood on 2007-06-28
Great, thanks for the info. I didn't think VMWare Server had a remote console ability like ESX does.

Given that I have xfce installed, how then do I boot back a command line interface (rather than automatically going straight into the GUI?

I guess if I can do that, I can then install VMWare Server, and hopefully from there admin it. 

Can I presume from your comment about 902, that is is blocked by default?

I realise that this is probably basic stuff, but my knowledge of *nix is practically zero.

---

### Post by scxtt on 2007-06-28
> Given that I have xfce installed, how then do I boot back a command line interface (rather than automatically going straight into the GUI?you'll just need to stop xdm/gdm/kdm from being loaded @ bootup - not to hard to do ...

> I guess if I can do that, I can then install VMWare Server, and hopefully from there admin it.yeah, just make sure you insall  "vmware-server-console", which actually i'm not sure i've seen in an ubuntu repo, i've seen it in Gentoo (might be out there for ubuntu in someone's repo :)) ... but i'd imagine you could do **ssh -X user@vmware-host** and launch **vmware &** and have it show up on your non-vmware host ...

there's also the MUI that you could use to manage them via the apache/httpd daemon it installs ... and at worst you can download the console via vmware.com ...

> Can I presume from your comment about 902, that is is blocked by default?ubuntu doesn't block anything by default, it just doesn't install anything that LISTENS, by default ... so as soon as xinetd and vmware server are installed, as long as you don't have iptables/firewall blocking the port - you're good to go :)

---

