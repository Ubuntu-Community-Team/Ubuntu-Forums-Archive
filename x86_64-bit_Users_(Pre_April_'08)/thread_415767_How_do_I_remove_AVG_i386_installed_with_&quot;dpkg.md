---
title: "How do I remove AVG i386 installed with &quot;dpkg --force-architecture&quot;?"
date: 2007-04-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by RavanH on 2007-04-20
Hi,

Can anyone tell me how to remove a .i386.deb program package from my x86_64 machine? 

I installed AVG antivirus with
```
sudo dpkg -i --force-architecture avg75fld-r45-a0973.i386.deb
```

But it turnsout it cannot be made to run on 64bit architecture/OS... So wanting to uninstall I tried
```
sudo dpkg --remove avg75fld
```
but that aborted with the output (some in dutch - sorry, but FAIL should be clear)
```
(Database inlezen ... 147445 bestanden en mappen geïnstalleerd.)
avg75fld wordt verwijderd ...
 * Stopping avgdkill: 246: Illegal number: -
local: 246: 5032: bad variable name
( not running)
 *                                                                                      [fail]
invoke-rc.d: initscript avgd, action "stop" failed.
dpkg: fout bij afhandelen van avg75fld (--remove):
 subproces pre-removal script gaf een foutwaarde 150 terug
Fouten gevonden tijdens behandelen van:
 avg75fld
```

So how to proceed?

Thanks for any suggestions.
-- Allard

---

### Post by Tanker Bob on 2007-04-20
What you did should have worked fine.  I've done it repeatedly since yesterday playing with things in 64-bit feisty, mostly fixing broken dependencies.  You can check out [this thread](http://ubuntuforums.org/showthread.php?t=414682) for when I was working with NVU for instance.  I don't read Dutch, so I cannot guess at why the correct procudure failed in your case, but the command looks correct.

---

### Post by RavanH on 2007-04-20
Thanks for your quick response, Tanker Bob.

I had been looking for an answer on the forums before but a few minutes ago, I found that one little post that did the trick: [http://ubuntuforums.org/showthread.php?p=2432248#poststop](http://ubuntuforums.org/showthread.php?p=2432248#poststop)

Turned out to be a problem with AVG and not due to architecture differences, as I thought...

Sorry for bothering you. I hope anyone else has use for the answer on the post above too. I certainly cannot advise AVG on Feisty 64bit, simply does not work. Uninstalling it, is the only option but only possible with the fix above.

Can anyone give me advice on what antivirus I can use on Feisty 64bit? Or just go without AV, because it simply is not needed on Linux?

Thanks anyway :)

---

### Post by Tanker Bob on 2007-04-20
Glad to hear that you got it worked out, RavanH.  I personally don't use any AV under Linux.  There has been some ongoing discussion about it, but I have yet to see evidence of a credible threat.  The only real use would be to scan email and files sent to you in case you forward them to Windows users who may be affected by any attached viruses.  I'm not in the habit of forwarding a lot of email, so I don't see the need for AV there for myself.

ClamAV is in the 64-bit feisty repository.  I've heard that it is a bit slow, but it's primary purpose is what I laid out above for email.  I had it loaded for a short time in edgy, but uninstalled it after a few days.  YMMV.

---

