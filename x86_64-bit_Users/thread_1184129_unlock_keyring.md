---
title: "unlock keyring"
date: 2009-06-10
forum: x86 64-bit Users
---

### Post by inphektion on 2009-06-10
I just changed my user passwd.  Now on reboot the network manager applet says it needs to "unlock keyring" in order to connect.  I have to enter my old user pass in there to unlock it.  How do I update this keyring with my new user pass so I don't get prompted for this anymore?

---

### Post by inphektion on 2009-06-10
i found this: [http://www.stchman.com/keyring_password.html](http://www.stchman.com/keyring_password.html)
weird I'd have to install a package to fix this just cause i changed my password...

also I don't have a keyring manager here:  Go to System--->Administration--->Keyring Manager

---

### Post by inphektion on 2009-06-10
libpam-gnome-keyring    - PAM module to unlock the GNOME keyring upon login    

this is installed already.  it seems i need to somehow tell this PAM module my new password as well so it can unlock the keyring on login.  This is what must've broke when I changed my pass.  the keyring stays with the old.

---

### Post by Clancy_s on 2009-06-10
You may be able to do it using post # 9 in this thread

[http://ubuntuforums.org/showthread.php?t=320308&highlight=enter+password+default+keyring+unlock](http://ubuntuforums.org/showthread.php?t=320308&highlight=enter+password+default+keyring+unlock)

but put in your new password instead of leaving the new password field blank.  I used it with the blank option to disable the keyring, it looks to me as though you could use it to get it to recognise your new password instead, but I don't know that for sure.

the relevant post is

> To get rid of the keyring prompt after automatic login in hardy 8.04 you can:

System > Preferences > Encryption and Keyrings
Under Password Keyrings click on "login Automatically unlocked when user logs in."
Click "Change Unlock Password"
Enter your old password, but leave the new password fields blank.
Ok , confirm and you should be set.

Related bug report (kinda) : [https://bugs.launchpad.net/ubuntu/+s...ng/+bug/108993](https://bugs.launchpad.net/ubuntu/+s...ng/+bug/108993)

I have also followed the part of this tutorial where you edit the etc/pam.d/gdm file. not sure if this has to do anything with it, too lazy to revert the changes and reboot to find out.
[http://ubuntu-tutorials.com/2007/07/...g-pam-keyring/](http://ubuntu-tutorials.com/2007/07/...g-pam-keyring/)

---

### Post by inphektion on 2009-06-11
I changed my password back to what it was.... problem solved.

If anyone knows how to change a password and update the keyring with the new one as well let me know.. hopefully this can be fixed at one point.

---

### Post by vanshark on 2009-07-01
I ran into the same issue when changing my user login password. Found the answer in this thread: 

[http://ubuntuforums.org/showthread.php?t=1178458&highlight=change+password+keyring+doesn%27t+work](http://ubuntuforums.org/showthread.php?t=1178458&highlight=change+password+keyring+doesn%27t+work)

Relevant post:

The keyring password can be changed (or removed) in Applications/Accessories/Passwords and Encryption Keys. ON the Passwords-tab right-click the "Passwords:login"-keyring and select "Change Password".

Hope this helps!

---

