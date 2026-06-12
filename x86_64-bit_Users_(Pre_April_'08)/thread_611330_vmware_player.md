---
title: "vmware player"
date: 2007-11-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by ashadocat on 2007-11-12
vmware player dosn't seem to have a 64-bit version in the repositories. should it?

---

### Post by dabl on 2007-11-13
There was ver. 1.5.xx VMWare Player in the Gutsy 64-bit repo when the RC was released, but it was broken, and I see they have subsequently removed it.

Go to the VMWare site and download the Ver. 2.0 tarball -- they have one for 64-bit.  It works flawlessly -- just follow the PDF instruction sheet.  :)

---

### Post by fjgaude on 2007-11-13
Great, do you see anything noteworthy in the Beta?

---

### Post by dabl on 2007-11-13
Yes, I was amazed that it saw my previous .vmx and .vmdk files and asked if I wanted to "move" them to Ver. 2.  I said "YES" and it opened up the previous machine, with the OS and apps complete, and I did not need to do anything.  It just worked -- very impressive.

---

### Post by fjgaude on 2007-11-13
Great, that's what I did going from 1.03 to 1.04... all worked perfectly. Now it will do it again with 2.0 Beta. I think I'll wait until 2.0 is released... I have no real issues with 1.04 Server presently.

Have you tried to mount an USB flash drive?

---

### Post by dabl on 2007-11-13
You know, I just looked at their web site and they're not referring to Player 2.0 as "beta" any more:

[http://www.vmware.com/products/player/faqs.html](http://www.vmware.com/products/player/faqs.html)

Yes, my USB thumb drive, which I formatted NTFS, mounts in my VM Player machine which is Win XP.  Also I have sound (as long as I don't try to play something in Linux first) and my USB Logitech webcam works too.  :guitar:

---

### Post by fjgaude on 2007-11-13
Thanks... well, I'll see if the Server is no longer Beta. Maybe version 2.0 will permit USB drives, though I don't really use such it's nice to have. As long as printers and scanners work I'm a happy camper.

---

### Post by relph on 2007-11-13
I tried it and when I attempted to log in via the web interface I got "web service url malformed". end of story.  Any ideas?

        -- John

---

### Post by dabl on 2007-11-13
> **relph said:**
> I tried it and when I attempted to log in via the web interface I got "web service url malformed". end of story.  Any ideas?

        -- John

Log in?

It's just a commercial web site -- there's no "log in" to it.  You do have to register your name and some information about your use environment prior to downloading the free Player, but it's just a tarball to download.  Make sure you pick the 64-bit tarball.

---

### Post by fjgaude on 2007-11-14
> **relph said:**
> I tried it and when I attempted to log in via the web interface I got "web service url malformed". end of story.  Any ideas?

        -- John

Here's the site I'd use:

[http://www.vmware.com/beta/server/?elq=C8997B56FF78484EB7A6A0DECF7376E8](http://www.vmware.com/beta/server/?elq=C8997B56FF78484EB7A6A0DECF7376E8)

Good luck.

---

### Post by samarium on 2007-11-18
> **relph said:**
> I tried it and when I attempted to log in via the web interface I got "web service url malformed". end of story.  Any ideas?

        -- John

I have the same issue.  Just installed.  Haven't found anything yet.

---

### Post by samarium on 2007-11-18
See [http://communities.vmware.com/message/798112#798112](http://communities.vmware.com/message/798112#798112) for the fix that worked for me.

---

### Post by dupuy on 2008-02-12
> **dabl said:**
> Log in?

It's just a commercial web site -- there's no "log in" to it.  You do have to register your name and some information about your use environment prior to downloading the free Player, but it's just a tarball to download.  Make sure you pick the 64-bit tarball.

I'm getting the same error as relph - this is when trying to login to access the VMware Server 2 web UI, not the vmware.com website.  VMware Server 2 eliminated the "server console" which displays under X and replaced it with a proxy web service, so that you access your vm images via a web browser (Mozilla is supported, I tried Konqueror and got nothing at all, not even the login screen).

Anyone who actually has an idea why it is giving this "Web service URL malformed." error - advice would be much appreciated.  :confused:

@alex

---

