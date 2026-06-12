---
title: "Firewall for Ubuntu 64 bit"
date: 2006-11-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by lexus_is250_awd on 2006-11-19
Does the base Ubuntu install come with firewall install and turned on?
Where can I configure it also?

Where can I get wine from?

Thanks

---

### Post by RAOF on 2006-11-19
The base Ubuntu comes with no services on internet-listening ports.  The IPTables firewall is built into the kernel, but by default allows everything.

**Firestarter** is a GUI frontend to IPtables, which you can install any way you want (Applications->Add/Remove, System-Administration->Synaptic, **apt-get install firestarter**, or **aptitude install firestarter**).

You can get wine from [wine-hq.org](wine-hq.org) :).

---

### Post by Kilz on 2006-11-19
> **lexus_is250_awd said:**
> Does the base Ubuntu install come with firewall install and turned on?
Where can I configure it also?

Where can I get wine from?

Thanks

Yes as I understand it, Ubuntu comes with a firewall called iptables. A search for iptables in Synaptic will bring up a lot of configuration tools for it. But for the most part its one of those things that I have never botherd to mess with. Because it works as is.

There is a howto for wine in my signature, it works on Edgy also.

---

### Post by incubus on 2006-11-19
As pointed by RAOF and Kilz, iptables is very powerful and extensible, plus it runs at the kernel level.  If you want to do something complicated and don't mind writing a script, that would be the way to go.

But iptables does have a somewhat steep learning curve.  If you're uncomfortable, I would suggest some graphical client too.  Firestarter is probably the most popular interface for iptables out there.  If you are using KDE, you may also consider guarddog (firewall) and guidedog (port forwarding).

All those programs do is to write the "tables" for you.  So you can run iptables, check what they did, and learn from that.  If you're interested in knowing more about the nuts and bolts of how the Internet packets work, the manual for iptables is well worth reading.

best,
incubus

---

### Post by lexus_is250_awd on 2006-11-19
Thanks for the info guys. Now if I decide not to configure the firewall and leave as is from the basic install, would that protect me or not?

---

### Post by RAOF on 2006-11-19
> **lexus_is250_awd said:**
> Thanks for the info guys. Now if I decide not to configure the firewall and leave as is from the basic install, would that protect me or not?

The default installation requires no protection - there's nothing listening to the internet, so there's nothing to protect.  Essentially only advanced users need to deal with a firewall at all on Ubuntu.

---

### Post by lexus_is250_awd on 2006-11-19
So for a home desktop I should have nothing to worry about?

---

### Post by RAOF on 2006-11-19
Exactly.

---

### Post by incubus on 2006-11-19
I agree.  I wouldn't bother either.  : )

If you start to run some network daemons (services) and want them to only be available locally, for example, then you would have to worry about setting up a firewall.   Or if you wanted to block some websites, or wanted to forward some packets to a different computer, etc.  Otherwise, you're fine.

incubus

---

### Post by lexus_is250_awd on 2006-11-19
Cool Thanks!!

---

### Post by lexus_is250_awd on 2006-11-19
One more question question about security. Do linux users need antivirus software on there machine?

---

### Post by RAOF on 2006-11-19
No.  Not unless you want to scan for **Windows** viruses, so you don't inadvertantly pass them on.

---

