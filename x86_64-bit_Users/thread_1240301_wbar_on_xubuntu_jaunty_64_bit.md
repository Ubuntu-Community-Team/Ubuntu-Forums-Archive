---
title: "wbar on xubuntu jaunty 64 bit"
date: 2009-08-14
forum: x86 64-bit Users
---

### Post by kvstb on 2009-08-14
How can i install wbar on xubuntu jaunty 64 bit?

---

### Post by Yellow Pasque on 2009-08-15
Have you tried building from source?

---

### Post by mark1124 on 2009-08-19
> **kvstb said:**
> How can i install wbar on xubuntu jaunty 64 bit?

[https://launchpad.net/ubuntu/karmic/amd64/wbar/1.3.3+dfsg1-1]("https://launchpad.net/ubuntu/karmic/amd64/wbar/1.3.3+dfsg1-1"):guitar:

You can grab any dependencies from here too.

---

### Post by Alfons81 on 2009-08-31
Thanks a lot Mark,

I was trying to compile it, forcing architecture,...I was going mad with that Wbar. At the end I have it, but now I need the Wbarconf for amd64. I was searching it on Launchpad and Google and I didn't find it.

Any ideas on how i could run Wbarconf?

---

### Post by Alfons81 on 2009-09-01
Done it. I downloaded wbarconf_0.7.2-1_i386.deb and then I instelled it like this: 

$ sudo dpkg -i --force-architecture wbarconf_0.7.2-1_i386.deb And 

Is working good with the Wbar.deb for amd64 that Mark recommend us.

And here it is working...

---

### Post by mark1124 on 2009-09-13
Glad I could help.  My problem is I'm running dual monitors and would like to get wbar in the bottom center of my main monitor.  when I center it, it splits across both monitors, or is to the far left or right if I try otherwise.  Anyone got any ideas?

---

