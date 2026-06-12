---
title: "WoW via SSH"
date: 2008-01-06
forum: Wine
---

### Post by trebor147 on 2008-01-06
Hey guys,

I am new to Linux, previously a Windows user.  I have very limited knowledge of my distro, Ubuntu but do have a good knowledge of Windows.  I can navigate everything fine and understand how many things work but my problem is that I dont know many of the good applications.

Im a WoW player and decided I would install it on Ubuntu.  All works fine, The graphics and everything are ok, using WINE.

My problem is this, I live in university halls, and they block alot of traffic, based on it being non-educational.  I can understand that for blocking things like p2p and BitTorrent, bandwidth hogs.

I dont really see why they block WoW, very low bandwidth requirements.


Anyway, I got around this on Windows by using Putty to connect to my shell and then using Proxifier to tunnel all traffic from Wow.exe.  I have also used socksify if that helps you understand what I was doing.

What I need is a way of "trapping" all traffic from wow.exe and sending it to my own machine (127.0.0.1) where it can be forwarded to my shell and around their restrictions.

I have tried the various bash commands to connect to a shell but they dont work.  Im behind a Proxy that seems to mess everything up.  To connect to my shell on Linux I have to use Putty.  Not a big deal, I only really use it for WoW.  So many SSH bash commands dont work for me.


Thanks for any comments.

Robert

---

### Post by foolsh on 2008-01-06
putty compiles and runs in linux
you can get the source from here [http://the.earth.li/~sgtatham/putty/latest/putty-0.60.tar.gz](http://the.earth.li/~sgtatham/putty/latest/putty-0.60.tar.gz)
you will need to install the build-essential and libgtk1.2-dev packages to compile
just uncompress it and change to the /putty-0.60/unix directory and run "make -f Makefile.gtk" to compile it 
then "./putty" and there you have it just like in windows

---

### Post by trebor147 on 2008-01-06
I have Putty installed on this setup, got it from "Add / Remove...." on Ubuntu. 

What I need is some way of directing the Wow.exe to this tunnel.  Like Freecap or Socksify can for Windows.

Thanks

---

### Post by trebor147 on 2008-01-07
I managed to get it working, well I can connect to my SSH shell now through the proxy server.  

[http://www.mtu.net/~engstrom/ssh-proxy.php](http://www.mtu.net/~engstrom/ssh-proxy.php)
Nice guide and the author is very helpful, he refered me to this, [http://wiki.linuxquestions.org/wiki/Corkscrew](http://wiki.linuxquestions.org/wiki/Corkscrew).

Combined both pages and all is well.

---

