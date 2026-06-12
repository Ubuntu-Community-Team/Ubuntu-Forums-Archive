---
title: "vnc connectin closes with &quot;End of Stream&quot; after I log in"
date: 2008-03-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by metro2003 on 2008-03-16
Hi, 

I have successfully installed the vnc4server on my server to log in remotely from one of my other PC.s.  I installed the following packages:

vnc4-common_4.1.1+xorg1.0.2-0ubuntu6_amd64.deb
vnc4server_4.1.1+xorg1.0.2-0ubuntu6_amd64.deb
xvnc4viewer_4.1.1+xorg1.0.2-0ubuntu6_amd64.deb

I followed the online instruction to setup the vnc and how to modify the Xvnc file

However, from my other pc, I type in:** vncview myserver:1**, I enter the password, and I see the remote server screen.  it comes up w/o any problems.  I then log in the remote computer screen and then all of a sudden my connection drops and I get the following message:

```

$ sudo xvncviewer 192.168.1.6:1

VNC Viewer Free Edition 4.1.1 for X - built Sep 10 2007 17:17:04
Copyright (C) 2002-2005 RealVNC Ltd.
See http://www.realvnc.com for information on VNC.

Sun Mar 16 17:15:28 2008
 CConn:       connected to host 192.168.1.6 port 5901
 CConnection: Server supports RFB protocol version 3.8
 CConnection: Using RFB protocol version 3.8

Sun Mar 16 17:15:31 2008
 TXImage:     Using default colormap and visual, TrueColor, depth 24.
 CConn:       Using pixel format depth 6 (8bpp) rgb222
 CConn:       Using ZRLE encoding
 CConn:       Throughput 20000 kbit/s - changing to hextile encoding
 CConn:       Throughput 20000 kbit/s - changing to full colour
 CConn:       Using pixel format depth 24 (32bpp) little-endian rgb888
 CConn:       Using hextile encoding

Sun Mar 16 17:15:37 2008
 main:        End of stream


```



also, here's my Xvnc file:

```

service Xvnc
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = root
        server = /usr/bin/Xvnc
        server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/fonts/X11/misc,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,/home/sorin/.fonts -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd -extension XFIXES
        port = 5901
}

```

my server is a Lenovo  AMD X2 processor 4400 desktop. running Kubuntu 7.10

would anyone know what this is happening?

any help is appreciated !!!

thank you.

---

