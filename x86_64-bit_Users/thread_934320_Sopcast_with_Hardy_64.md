---
title: "Sopcast with Hardy 64"
date: 2008-09-30
forum: x86 64-bit Users
---

### Post by Tmorr034 on 2008-09-30
I am a new convert to Ubuntu from Windows and am fairly unsavvy when it comes to using computers.  I am trying to install sopcast (either of the gui versions would suffice) on Hardy and I am using the 64 bit version.  I have tried downloading and unpacking some of the various Debs that have been posted elsewhere on these forums, but they all seem to be for 32bit architecture and I haven't been successful in forcing the architecture.  Does anyone know if it is possible to run Sopcast on the 64bit version and where I might find a how-to do which would walk me through the process?  

Thanks

---

### Post by fluffybacon on 2008-09-30
sudo dpkg -i --force-architecture gsopcast*.deb

worked for me.

---

### Post by Tmorr034 on 2008-10-01
Thanks!  That worked for me like a charm.  

I am still haveing two further problems though.  First, I can't configure either of my browsers (opera or firefox) to launch them by clicking on a sop link. I entered the protocol provided in the about:config in firefox and nothing happens when I click the link.  I have a similar problem on Opera where I changed the associationsfor Sops in preferences/advanced/programs.  

This wouldn't be a big deal if not for my other problem.  If I enter a channel in at the bottom of the channel list and click launch, gsopcast just closes.  I can launch other channels which appear in the populated channel list without a problem.

---

