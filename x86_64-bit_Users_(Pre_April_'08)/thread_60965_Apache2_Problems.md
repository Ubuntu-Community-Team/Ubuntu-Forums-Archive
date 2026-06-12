---
title: "Apache2 Problems"
date: 2005-08-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by jewishj on 2005-08-29
I have looked around for a while and havent been able to find a solution to this problem on these forums or on google.

I am running hoary 5.04 amd64 and used synaptic to install apache2.
After the install, I tried opening [http://localhost/](http://localhost/) in firefox and it opened the apache directory in the browser just as it should have.

I then compiled php 5 from source and installed that.
I also changed the wwwroot in /etc/apache2/apache.conf /etc/apache2/sites-available/default and /etc/apache2/sites-enabled/000-default to /mnt/storage/wwwroot (/mnt/storage/ is a mounted fat32 drive that is shared between this and windows).

After making these changes, I get a "The connection was refused when attempting to contact localhost" when I tried to go to [http://localhost/](http://localhost/)

I changed all the wwwroot references back to the defaults and still get the same error.  I also get the same error if i try to go to [http://127.0.0.1](http://127.0.0.1) except "localhost" is replaced with "127.0.0.1" in the error message.

I have checked and the rw permissions are set to 0777 with chmod.

Also, whenever I reboot, the apache process fails to stop every time.

Thanks for any help.

---

### Post by DancingSun on 2005-08-30
I'm not quite sure how to solve the Apache problem.  But you could try to uninstall then re-install it again.  Also, make sure apache is running when you access it.

What do you mean by failing to stop?  To manage services, you might want to try this:
[http://ubuntuforums.org/showthread.php?t=42129](http://ubuntuforums.org/showthread.php?t=42129)

---

