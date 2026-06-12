---
title: "Consistant error prevents system update!"
date: 2006-05-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by Doobie9 on 2006-05-28
I keep getting this error after trying to update and/orr fix broken packages:

The following problems have been found with your system, blah blah:

	"   	 	 	 	 	 	 	E: /var/cache/apt/archives/ntp-server_1%3a4.2.0a+stable-8.1ubuntu5_powerpc.deb: subprocess new pre-removal script returned error exit status 1" 


NOTHING at ALL fixes the problem. I've tried running 'repair packages' in synaptic, doesn't work. I've try uninstalling the bad package, that doesn't work. 




Please, help! ](*,)

---

### Post by ssam on 2006-05-29
sounds like [http://www.ubuntuforums.org/showthread.php?t=183533](http://www.ubuntuforums.org/showthread.php?t=183533)

---

### Post by nkbj on 2006-05-29
A new version of ntp-server (4.2.0a+stable-8.1ubuntu6) was released Today fixing this specific problem. From the changelog:

ntp (1:4.2.0a+stable-8.1ubuntu6) dapper; urgency=low
 .
   * Call dh_installinit with --error-handler=true, which will prevent
     ntp-server's prerm and postinst from bombing out on upgrades from
     previous broken versions.  ntp-{simple,refclock} still try to
     restart the server in their postinst, so it won't be left dead.

Regards,
Niels Kristian

---

