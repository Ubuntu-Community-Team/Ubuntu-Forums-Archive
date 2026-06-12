---
title: "[SOLVED] Login Screen Resolution Problem"
date: 2008-10-18
forum: x86 64-bit Users
---

### Post by SwapsRulez on 2008-10-18
Hi there, I'm using Ubuntu Hardy Heron 8.04 :)
I have set the screen resolution of my monitor to 1280 x 1024 which is max of my monitor Samsung Syncmaster 753s. But the problem is, when i boot up my system and it comes to login window, the login window doesn't fit properly to the screen. The option button is half shown. Its displaying fine when I use 1024 x 768 resolution. So my question is, I want to use 1280 x 1024 for normal working and want to use 1024 x 768 for login screen where I enter my username and password. My login screen is default.

Thanks for reading. 

:popcorn: for the person who will solve my problem. :KS

---

### Post by SwapsRulez on 2008-10-22
Anyone? :(

---

### Post by philinux on 2008-10-22
Install startupmanager from synaptic. It run from the Admin menu.

When you run it you'll notice the option to set the login screen resolution as well as other grub stuff. Nice little gui.

---

### Post by phlembob on 2008-10-22
Hi SwapsRulez-
I understand your problem, but I haven't tried to set it up.  Make your questions well, like you did here, and your answers will come.

Philinux has given you a response so please remember to report success for the rest of us to learn too.  People need to learn the combinational effects between monitors and graphics circuitry.  Sometimes one will do things the other can't perform.

---

### Post by Ameneon on 2008-10-23
This, at least for me, did not have the effect that I was looking for. The startupmanager application is a nifty little utility indeed, but what it changes (at least for me) is the progress bar screen shown prior to the login screen. The login screen itself is still the same wrong resolution with the edit boxes for username/password in the lower right hand side of the window rather than the (usual) middle. This is regardless of what resolution I set using startupmanager. This has been the case for quite some time now (since one of the updates some time ago, of course I (alas) don't recall which), and I can't seem to find which file or setting manipulates just the login screen.

startupmanager changes the progress bar, and once we're logged in the resolution is right anyway, but just at the login screen it's off entirely.

---

### Post by Ameneon on 2008-10-23
Ok, I thought I had tried this before but apparently I had done something wrong back then. The piece of advice given by "Anne Onyme" (not the main post but rather a comment further down the page) on this page:

[http://linuxfud.wordpress.com/2006/08/13/gdm-login-screen-resolution-too-big-to-fit-screen-try-this/](http://linuxfud.wordpress.com/2006/08/13/gdm-login-screen-resolution-too-big-to-fit-screen-try-this/)

was what did the trick for me. Finally I can reach those options again :)

---

### Post by SwapsRulez on 2008-11-06
> **Ameneon said:**
> Ok, I thought I had tried this before but apparently I had done something wrong back then. The piece of advice given by "Anne Onyme" (not the main post but rather a comment further down the page) on this page:

[http://linuxfud.wordpress.com/2006/08/13/gdm-login-screen-resolution-too-big-to-fit-screen-try-this/](http://linuxfud.wordpress.com/2006/08/13/gdm-login-screen-resolution-too-big-to-fit-screen-try-this/)

was what did the trick for me. Finally I can reach those options again :)
Sorry mate for late reply. I was out of town these days for holidays in india. Sorry once again. And yes I looked at your link now. Seems link it helped soo many peoples. This thread will help those peoples, I think Its fine now in Ubuntu 8.10. Anyways... thanks a milliion for your and other guys help. I appreciate it. :)

---

