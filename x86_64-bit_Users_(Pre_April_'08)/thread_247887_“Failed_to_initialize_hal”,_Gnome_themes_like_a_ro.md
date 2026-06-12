---
title: "“Failed to initialize hal”, Gnome themes like a robotic chipmunk on lsd."
date: 2006-08-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by mikesherman on 2006-08-31
Hello world, I’ve been using Ubuntu (DD/6.06) for about 3 months now and generally am happy with it, its even replaced Windows on my main desktop.  Last night I (successfully) installed smbfs and netkit-inetd (samba and swat have been installed for ages) so that I could easily set up file sharing with my windows 2k box and mount the shares on this system, everything worked just how it was meant to and with this knowledge I went to bed.

But… and there’s always a but, This morning when I logged after entering my password for firestarter I was greeted with an error message saying, “Failed to initialize hal” as the desktop was loading and when I tried using the sudo command I got the message “segmentation fault” but everything else seemed fine.

After a reboot this did not happen again but the firestarter firewall crashed at start up and the whole system still seems very slow.  Also after rebooting whenever I clicked on anything, or to be technical set the mouse focus, the whole desktop changed to the default Gnome theme (Gnomes blue default one not Ubuntu’s orange one) and then change back to my theme, and the whole system was running much slower then usual.  Also the package manager wouldn’t load; after entering my password nothing happened although apt-get did work from the command line.

One more reboot later and again I’m greeted with  “Failed to initialize hal” but as far as I can tell everything else is working how it’s supposed to.

So I was wondering:
1)	What is “hal” and what dose it do? (Dose it stand hardware abstraction layer by any chance?)
2)	What would be trying to initialze it (firestarter or gnome)?
3)	What would on that one occasion cause gnome to flick between current and default themes as described earlier on?

If anyone needs any info about hardware spec or software config I will be happy to post I’m not really sure what would be relevant.

---

