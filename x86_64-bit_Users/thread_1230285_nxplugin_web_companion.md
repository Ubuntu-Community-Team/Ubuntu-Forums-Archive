---
title: "nxplugin web companion"
date: 2009-08-03
forum: x86 64-bit Users
---

### Post by sdlinux on 2009-08-03
Has anyone successfully installed the nxplugin (web companion) on 64 bit ubuntu? 

The guide is very limited [https://help.ubuntu.com/community/NX_Web_Companion](https://help.ubuntu.com/community/NX_Web_Companion) .  During the install after about 5 seconds it goes back to the bash prompt.

---

### Post by sdlinux on 2009-08-03
I don't think I am getting an answer... so is there some other program that works well for remotely accessing your ubuntu 64 bit desktop graphically? I need something that doesn't require an install on the windows (client) side.

---

### Post by bobince on 2009-08-04
> **sdlinux said:**
> so is there some other program that works well for remotely accessing your ubuntu 64 bit desktop graphically?

[VNC](http://en.wikipedia.org/wiki/VNC)? That's what's typically used (over SSH for security). It requires software on the client (but then so does NXPlugin). There are Java implementations of the VNC client if that's acceptable.

If you really can't run a VNC client on the Windows side, the only built-in remote desktop access protocol on XP is [RDP](http://en.wikipedia.org/wiki/Remote_Desktop_Protocol). I've not tried the [xrdp](http://xrdp.sourceforge.net/) server so I don't know how well that works.

---

### Post by sebastianabate on 2009-08-04
What is the exact error? the only thing I had to do was copy the plugin directory to my httpd root, edit the file /plugin/nxapplet.html, and then copy the session.nxs to the plugin/session directory; thats all, when I enter [http://myserver/plugin/nxapplet.html](http://myserver/plugin/nxapplet.html) in firefox the username:password dialog appears.

---

