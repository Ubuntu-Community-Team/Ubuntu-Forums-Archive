---
title: "Is it possible to 'downgrade' to 32 bit from 64 bit?"
date: 2009-11-04
forum: x86 64-bit Users
---

### Post by mbelly on 2009-11-04
I am currently running Ubuntu 9.04 64-bit.  At work I would like to be able to VPN in to work, but the cisco client requires a 32-bit kernel only, or it will lock up the kernel.  Is there an easy way for me to downgrade to a 32-bit system?  Or do I just have to re-install from scratch?

Thanks,
~Matt

---

### Post by dgoosens on 2009-11-04
on 9.04 I did manage to install the Cisco VPN client on the 64-bit flavor...
it was not easy though...

I followed the steps described here:
[http://www.ubuntugeek.com/cisco-vpn-tip-for-ubuntu-904-jaunty-users.html](http://www.ubuntugeek.com/cisco-vpn-tip-for-ubuntu-904-jaunty-users.html)

We finally went for OpenVPN though because our firewall could handle both... maybe that's a solution on your end as well ? 

Finally, I don't think it is possible to change your 64-bit into a 32-bit flavor

---

### Post by mbelly on 2009-11-04
> **dgoosens said:**
> on 9.04 I did manage to install the Cisco VPN client on the 64-bit flavor...
it was not easy though...

I followed the steps described here:
[http://www.ubuntugeek.com/cisco-vpn-tip-for-ubuntu-904-jaunty-users.html](http://www.ubuntugeek.com/cisco-vpn-tip-for-ubuntu-904-jaunty-users.html)

We finally went for OpenVPN though because our firewall could handle both... maybe that's a solution on your end as well ? 

Finally, I don't think it is possible to change your 64-bit into a 32-bit flavor

I am a mere user, not an admin, so I don't have the option of changing what VPN we use.  I'll try that link when I get home tonight.  Thanks.

---

### Post by bford16 on 2009-11-04
> **mbelly said:**
> I am currently running Ubuntu 9.04 64-bit.  At work I would like to be able to VPN in to work, but the cisco client requires a 32-bit kernel only, or it will lock up the kernel.  Is there an easy way for me to downgrade to a 32-bit system?  Or do I just have to re-install from scratch?

Thanks,
~Matt
No.  It is not possible to change your installation from 32-bit to 64-bit or vice versa.

It is often possible to run 32-bit software on a 64-it system, but the reverse is not true.  For instance Ubuntu installs the 32-bit Flash plugin on the 64-bit version by default.  The plugin works via a "wrapper" application called, 'nspluginwrapper.'  However, it is not possible to use the 64-bit Flash plugin on a 32-bit system. (You wouldn't need it anyway.)

If you want to change from 64-bit to 32-bit, you will have to do a clean install of 32-bit Ubuntu on your system.

---

### Post by fela on 2009-11-04
you have to reinstall from scratch.

just want to make something clear: a 64 bit executable is a completely different file from a 32 bit executable and was compiled in a different way. This means that if you want to replace a 64 bit system with 32 bit, or vice versa, you have to replace all the 64 bit executables and their dependencies with 32 bit executables, ie reinstall the system.

---

