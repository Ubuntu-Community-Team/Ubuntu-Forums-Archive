---
title: "network just stopped workin???"
date: 2006-02-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by bobbymcsteels on 2006-02-07
Like the titles says my network has stopped working(was working tho) in kubuntu 5.10 amd64 breezy. Tried control pannel-network-admin tried to enable it but as soon as i click enable it goes back to being disabled. Its configured to dhcp and is exactly how it was before it stopped working..... Any ideas whats goin on?

---

### Post by sirlancelot on 2006-02-07
I am having the same problem. When I go to Konsole and enter 'ifconfig' nothing shows up. It seems that my networking interface is not starting or is starting then stopping, I type 'sudo /etc/init.d/networking restart' and stopping the interface fails, but starting it comes back as ok.

I may have messed with something last night but I was really tired and don't remember what it was :(

Any help would be greatly appreciated.

EDIT: I am not using the 64bit version, I have the XFree86 version

---

### Post by sirlancelot on 2006-02-08
After further research I foud this thread that seemed to have fixed my problem. Perhaps it may help you too.

Major thanks and props to Amohanty!

[http://www.ubuntuforums.org/showthread.php?t=99059]("http://www.ubuntuforums.org/showthread.php?t=99059")

---

### Post by bobbymcsteels on 2006-02-08
yeah that seemed to do the trick.... nice 1;)

---

