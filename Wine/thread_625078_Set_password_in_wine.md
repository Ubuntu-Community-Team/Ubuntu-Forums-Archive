---
title: "Set password in wine"
date: 2007-11-27
forum: Wine
---

### Post by Shelnutt2 on 2007-11-27
I'm trying to get folding @ home SMP version to work via wine (There is a native Linux client but only for 64 bit machines). It is a dotnet 2.0 application. I've gone through and hacked my way into getting .net 2.0 to work. I followed the app database on winehq, and now .net is working.

My problem appears to be that the software needs windows users to have a password on their account. This would be easy to do in windows but I've never run into this in Linux. I'm getting an error message and I've been told it is because I need my windows account to have a username and password..so how would I setup a password in wine? Any idea?

Thanks

---

### Post by lonce on 2007-11-27
Wish I could help you on this.  I am having the same problem.

---

### Post by cogadh on 2007-11-27
I believe version 5.04 version of the F@H Linux console client is for 32 bit processors. The 6.00 beta version is 64 bit only.

EDIT - Just confirmed, the 5.04 version does work on 32 bit processors.

---

### Post by Shelnutt2 on 2007-11-27
> **cogadh said:**
> I believe version 5.04 version of the F@H Linux console client is for 32 bit processors. The 6.00 beta version is 64 bit only.

You are correct, but I want the SMP version. It produces 3-4x more than just the standard client on multi-core/multi-processor machines.

---

### Post by cogadh on 2007-11-27
I believe the reason F@H needs a user name is because it runs as a service when used in Windows. Since Windows services can't run in Wine, that will never work. However, using the 32 bit Linux client, you can do pretty much the same thing that the SMP version does by running multiple instances of the client in their own directories:
[http://folding.stanford.edu/English/FAQ#ntoc31](http://folding.stanford.edu/English/FAQ#ntoc31)

---

