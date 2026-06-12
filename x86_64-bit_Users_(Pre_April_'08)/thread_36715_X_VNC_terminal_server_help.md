---
title: "X VNC terminal server help"
date: 2005-05-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by KRavEN on 2005-05-24
So I'm a suse convert.  I loaded 9.3 AMD64 but I didn't like that low availability of packages for that dist and it's very tiresome to do anything from source with it because of all their custom config files.

I've gotten most things I want working in ubuntu now, but the one thing I really liked about suse was it's remote administration function using vnc.  Now I know there is kfrb and the other for gnome, but I don't like the way they work and they are much less responsive than vnc.

I've been following the tutorials here [http://linuxreviews.org/howtos/xvnc/](http://linuxreviews.org/howtos/xvnc/)  and here [http://gentoo-wiki.com/HOWTO_Xvnc_terminal_server](http://gentoo-wiki.com/HOWTO_Xvnc_terminal_server) 

They are much the same and it's fairly easy to translate into what I need to do for ubuntu.

I've run into the issue already with tightvnc and realvnc (via apt vncserver pkg) both segfault on AMD64.  I overcame this by using binaries from the fedora x86_64 rpm.  They've somehow been able to fix whatever the bug was, as has suse.

Following the tutorial I am stuck at the point where I am always asked for a password when trying to open the vnc session.  I've tried setting a different user than nobody and using vncpasswd to set a passwd but it is never accepted.  I'm sure the Xvnc is working because I get authentication failed and not another error message.  I also get the appropriate responces when telneting to the listening port.

My ultimate goal is to be able to get a KDM or GDM login screen when I open my vncviewer to the appropriate port and not get asked for a password except when logging into kdm or gdm.  This is the way it works with suse.

Icing on the cake would be the ability to reconnect to an existing session or close the existing session if I log back in after closing my vncviewer, similar to the way remote desktop does with terminal server on windows.

Does anyone have any experience getting this to work?

---

### Post by BigCdaAnswer3 on 2005-05-25
If fedora has a working amd64 package available then you could use the alien command to debianize it.

---

### Post by KRavEN on 2005-05-25
[QUOTE=BigCdaAnswer3]If fedora has a working amd64 package available then you could use the alien command to debianize it.[/QUOTE]

Yeah, thats how I got the working binaries to begin with.  That's just the binaries though, similar to the ubuntu vncserver package, it doesn't setup anything for the remote vnc administration.  I suppose I could try getting the suse package and seeing how that works.  Probably take a lot of fiddling with to change the various scripts and config files it uses.

---

### Post by KRavEN on 2005-05-30
Okay, well I got this working like I wanted now.  Was actually quite easy and works exactly as the default SuSE does.

Need 3 RPM's from the 9.3 SuSE x86_64 DVD:

tightvnc-1.2.9-182.x86_64.rpm <--- This you alien and install the deb, rm /etc/slp.reg.d/vnc.reg (you can remove the dir too if its empty) and rm /etc/xinetd.d/vnc(if you're using the default inetd and the dir is empty remove it too)

xorg-x11-Xvnc-6.8.2-30.x86_64.rpm <--- This you just alien and install the deb

resmgr-0.9.8-65.x86_64.rpm <--- this one you only need the libresmgr libraries so you copy them out of /lib64 and /usr/lib64, dpkg -P the package, and then move them back if you want.  I don't think it will hurt anything if the other stuff stays though.

Next you add the following lines to /etc/services :
```

vnc1    5901/tcp
vnc2    5902/tcp
vnc3    5903/tcp
vnchttpd1       5801/tcp
vnchttpd2       5802/tcp
vnchttpd3       5803/tcp

```
Then you edit inetd.conf and add the following lines:

```

vnc1    stream  tcp     nowait  nobody  /usr/X11R6/bin/Xvnc     Xvnc :42 -inetd -once -query localhost -geometry 1024x768 -depth 16
vnc2    stream  tcp     nowait  nobody  /usr/X11R6/bin/Xvnc     Xvnc :42 -inetd -once -query localhost -geometry 1280x1024 -depth 16
vnc3    stream  tcp     nowait  nobody  /usr/X11R6/bin/Xvnc     Xvnc :42 -inetd -once -query localhost -geometry 1600x1200 -depth 16
vnchttpd1       stream  tcp     nowait  nobody  /usr/X11R6/bin/vnc_inetd_httpd vnc_inetd_httpd 1024 768 5901
vnchttpd2       stream  tcp     nowait  nobody  /usr/X11R6/bin/vnc_inetd_httpd vnc_inetd_httpd 1280 1024 5902
vnchttpd3       stream  tcp     nowait  nobody  /usr/X11R6/bin/vnc_inetd_httpd vnc_inetd_httpd 1600 1200 5903

```
now you sudo /etc/init.d/inetd restart

All done, now you have 3 options for VNC: 

1024x768x16 on [http://localhost:5801](http://localhost:5801) from your browser or strait localhost 5901 with your vncviewer of choice. Ports 5802/5902 are 1280x1024x16 and ports 5803/5903 are 1600x1200x16.  You can of course change or add to these by editing /etc/services and /etc/inetd.conf

When the vncviewer prompts for a password just leave it blank and you will be presented with the KDM or GDM login screen
 
Be cool if someone could do a remote admin package for this on ubuntu.  I've never done a deb so I wouldn't know where to start.

---

### Post by nanjil on 2007-08-12
tow questions onthsi one.

1. how do i find out whether inetd or xinetd is running

which is the best place to put this; inetd.conf or xinted.conf ?

thanx

---

### Post by nanjil on 2007-08-12
I just tried miodfying the inetd.conf and restarting inetd.
I am not sure whether by inetd is running a t all 
because when i tyoed

sudo /etc/init.d/inet restart 
I did not get any messages.

The I tried the xinetd route. I copeid my vnc file from my suse system to /etc/xinet.d directory ; the contents of that files are

# default: off
# description: This serves out a VNC connection which starts at a KDM login \
#	prompt. This VNC connection has a resolution of 1024x768, 16bit depth.
service vnc1
{
	socket_type     = stream
	protocol        = tcp
	wait            = no
	user            = nobody
	server          = /usr/X11R6/bin/Xvnc
	server_args     = :42 -inetd -once -query localhost -geometry 1024x768 -depth 16
	type		= UNLISTED
	port		= 5901
}
# default: off
# description: This serves out a VNC connection which starts at a KDM login \
#	prompt. This VNC connection has a resolution of 1280x1024, 16bit depth.
service vnc2
{
	type		= UNLISTED
	port		= 5902
	socket_type	= stream
	protocol	= tcp
	wait		= no
	user		= nobody
	server		= /usr/X11R6/bin/Xvnc
	server_args	= :42 -inetd -once -query localhost -geometry 1280x1024 -depth 16
	disable		= yes
}
# default: off
# description: This serves out a VNC connection which starts at a KDM login \
#	prompt. This VNC connection has a resolution of 1600x1200, 16bit depth.
service vnc3
{
	type		= UNLISTED
	port		= 5903
	socket_type	= stream
	protocol	= tcp
	wait		= no
	user		= nobody
	server		= /usr/X11R6/bin/Xvnc
	server_args	= :42 -inetd -once -query localhost -geometry 1600x1200 -depth 16
	disable		= yes
}
# default: off
# description: This serves out the vncviewer Java applet for the VNC \
#	server running on port 5901, (vnc port 1).
service vnchttpd1
{
	socket_type     = stream
	protocol        = tcp
	wait            = no
	user            = nobody
	server          = /usr/X11R6/bin/vnc_inetd_httpd
	server_args     = 1024 768 5901
	type		= UNLISTED
	port		= 5801
}
# default: off
# description: This serves out the vncviewer Java applet for the VNC \
#	server running on port 5902, (vnc port 2).
service vnchttpd2
{
	disable         = yes
	socket_type     = stream
	protocol        = tcp
	wait            = no
	user            = nobody
	server          = /usr/X11R6/bin/vnc_inetd_httpd
	server_args     = 1280 1024 5902
	type		= UNLISTED
	port		= 5802
}
# default: off
# description: This serves out the vncviewer Java applet for the VNC \
#	server running on port 5902, (vnc port 3).
service vnchttpd3
{
	disable         = yes
	socket_type     = stream
	protocol        = tcp
	wait            = no
	user            = nobody
	server          = /usr/X11R6/bin/vnc_inetd_httpd
	server_args     = 1600 1200 5903
	type		= UNLISTED
	port		= 5803
}

then I restarted xinetd

now when i access port 5801 through my browser , the hjava script starts up . but the connection gets closed imediatley after I try to login

network error: remote side closed connection

any clues?
thanx

---

