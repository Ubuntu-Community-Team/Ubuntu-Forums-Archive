---
title: "Upgraded Ubuntu - lost Gnome!"
date: 2009-12-05
forum: Wisconsin Team
---

### Post by ckuecker on 2009-12-05
Hello from Beloit,

I am not exactly new to computers, but I've only been using Ubuntu for a few months. So far, it's been working well. I had to replace my old Mandrake 7 machine when it died last summer. I use Linux to run my web server and email, and recently have started work on an embedded Linux application for a customer.

This morning, Ubuntu announced there were upgrades available, so I clicked 'OK" and let the upgrade proceed. When it finished, I was prompted to restart, which I did.

During the restart, the power got interrupted. After the power came back, I restarted the computer. The login screen came up, and I logged in.

A few seconds later, I got an error message box that the session lasted less than 10 seconds. I did a search and found several possible causes and fixes. 

The .xsession-errors file has complaints that the /dev/null file cannot be created. I tried setting permissions on the /etc directory to 777, but no joy.

I was running gnome, as that was the default when I installed Ubuntu. I tried installing kde. Rebooting now gives a kde screen with a login box - when I try to log in, the screen blanks and returns to the login screen again, with no error message. Switching back to gnome brings up the error box as before.

I tried the 'failsafe' session - it puts up the desktop, then puts up two error boxes with no text which go away quickly, then the screen resets. It will loop like that until I switch to a terminal mode.

Anyone have any idea which way I should go next? The email and web servers are working fine yet, but I am not real skilled at doing code development from the command line any more - spoiled by GUIs...

Chuck Kuecker

---

### Post by ckuecker on 2009-12-07
Well, I recovered the system. It was a long, hard road, but I made it.

Now, I need to get my mailserver, DNS, and website back.

Chuck

---

