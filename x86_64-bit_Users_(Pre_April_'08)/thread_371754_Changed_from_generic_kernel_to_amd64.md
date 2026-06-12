---
title: "Changed from generic kernel to amd64"
date: 2007-02-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by Thyme on 2007-02-27
I've just installed the 2.6.21-rc1 kernel on ubuntu edgy because I couldn't stand sitting with kernel 2.6.17-generic and I wanted to see the new features etc... However, when configuring the new kernel I selected amd64 in the "cpu architecture" section. So it's something like 2.6.21-rc1-amd64 or similar - I would think.

I'm now getting iptables errors being thrown at me and configuring/selecting the DHCP option within firestarter is greyed out - not selectable/checkable. Also. ipv6 worked great before the new kernel update but now the option to configure it in firestarter isn't even present (although this may be related to the actual problem).

So I'd like to know whether:

1) Configuring the new kernel with a different CPU architecture type i.e. from generic to amd64 is definitely not on! (This IS a 64bit Ubuntu Edgy OS)

2) or whether iptables has become problematic because I didn't configure the new kernel properly (like the DHCP stuff etc... - Although I'm pretty sure I did)

Many thanks to anybody who can help me!

---

### Post by Thyme on 2007-02-27
I've made some progress, positive or none - depending which way you look at it! 

(firestarter:5138): GLib-WARNING **: GError set over the top of a previous GError or uninitialized memory.
This indicates a bug in someone's code. You must ensure an error is NULL before it's set.
The overwriting error message was: There was an error launching the default action command associated with this location.

(The above resulted after I clicked on the "Explain The DHCP Function.." during the initial configuration dialogues)

I'm using Glib 2.12.9.

---

