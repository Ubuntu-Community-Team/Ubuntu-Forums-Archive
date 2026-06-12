---
title: "Unable to boot Ubuntu"
date: 2008-11-20
forum: x86 64-bit Users
---

### Post by daleybortolon on 2008-11-20
I was installing samsung printer scx-4200 driver UnifiedLinuxDriver.tar.gz when the desktop froze. I rebooted the system (dual boot xp-ubuntu)and now I get the the message "unable to cd home/daleybortolon".
What shall I do?
Can anybody help?:(

---

### Post by nikgare on 2008-11-20
Where do you you get that meddage? On the desktop, while you boot?
How far does Ubuntu boot?

---

### Post by daleybortolon on 2008-11-20
Ubuntu loads and then becomes black and I noticed that 2 lines fail to load:

start-stop-daemon: Unable to start/sbin/klogd: Permission denied (Permission denied): failed

Starting Avahi nDNS/DNS-SD Daemon avahi-daemon: Failed

---

### Post by daleybortolon on 2008-11-20
after thosetwo sentences, after a while, i then get "unable to cd home/daleybortolon".
Please, can anybody help?
This has happened to my work computer!

---

### Post by Thelasko on 2008-11-20
How did you try to install this program?  Where did you get it from?

---

### Post by jrettyw691 on 2008-11-20
There is [**wow gold**](http://veryge.com/) for sale,the cheapest wow gold. Have a fun of our trading. Because we have mass available stock of gold at the moment, so we can really provide an instant delivery.

---

### Post by daleybortolon on 2008-11-20
> **Thelasko said:**
> How did you try to install this program?  Where did you get it from?
I downloaded the driver from Samsung's site, unzipped, entered it and executed autorun. It went fine to about 98% of the installation and then it froze. I was using openoffice at the time( I don't know if it helps). I had to reboot and now I can't start Ubuntu!

---

### Post by Thelasko on 2008-11-20
> **daleybortolon said:**
> I downloaded the driver from Samsung's site, unzipped, entered it and executed autorun. It went fine to about 98% of the installation and then it froze. I was using openoffice at the time( I don't know if it helps). I had to reboot and now I can't start Ubuntu!

[This site]("http://jacobo.tarrio.org/code/scx4200/") says there's a bug in the driver.

Edit: It looks like the fix is to change the permissions on the file stated in the error.  I'm not sure how to do that (maybe someone else knows?) on a broken system.  Your other option is to reinstall.

---

### Post by daleybortolon on 2008-11-21
> **Thelasko said:**
> [This site]("http://jacobo.tarrio.org/code/scx4200/") says there's a bug in the driver.

Edit: It looks like the fix is to change the permissions on the file stated in the error.  I'm not sure how to do that (maybe someone else knows?) on a broken system.  Your other option is to reinstall.

Thanks anyway!!!
I just hope someone will be able to help me.

---

### Post by korami on 2008-11-25
Hi there,

I am having the same issue... but I'm not even sure what I did... I just know I changed the permissions to all of the files and folders within a user's home folder.

But I'm not even reaching the home folder.

Is  there a general workaround to fix this issue?

---

