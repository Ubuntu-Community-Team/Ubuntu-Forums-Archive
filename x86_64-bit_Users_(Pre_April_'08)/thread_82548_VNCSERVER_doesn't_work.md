---
title: "VNCSERVER doesn't work"
date: 2005-10-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by kingkong on 2005-10-26
vncserver doesn't start. I mean it shows it does but netstat -l doesn't how port 5901.. also tightvncserver gives error saying that fontpath in incorrect and process xvnc coun't start.

vncserver or tightvnc don't work. Remote desktop seems to work fine. I tried changing the fontPath in vnc.conf to match the fontpath in xorg files but still the same error. I have AMD64. Also vnc4 is not available in the repositories universe/multiverse included.
Any help would be greatly appreciated since I need to use vncserver very very frequently.
Please help.

---

### Post by kingkong on 2005-10-26
[QUOTE=kingkong]vncserver doesn't start. I mean it shows it does but netstat -l doesn't how port 5901.. also tightvncserver gives error saying that fontpath in incorrect and process xvnc coun't start.

vncserver or tightvnc don't work. Remote desktop seems to work fine. I tried changing the fontPath in vnc.conf to match the fontpath in xorg files but still the same error. I have AMD64. Also vnc4 is not available in the repositories universe/multiverse included.
Any help would be greatly appreciated since I need to use vncserver very very frequently.
Please help.

[/QUOTE]

I am pretty sure that this is specific to amd64 version of breezy since 32 bit installation i did previously worked without any problem.
Does it work for anybody at all?

---

### Post by queenorych on 2005-10-27
check the debian amd64 lists.  There is a problem with vnc on amd64.  There are patches floating around.  I hard that vnc-x11, which uses the current X session works without a hitch.

---

### Post by kingkong on 2005-10-31
[QUOTE=queenorych]check the debian amd64 lists.  There is a problem with vnc on amd64.  There are patches floating around.  I hard that vnc-x11, which uses the current X session works without a hitch.[/QUOTE]

After several days of effort this did not work for me. The patches are for X11F86 while ubuntu has x.org apart from several dependency problems. Did it work for anybody? Is there an alternative ?
I want multiple users to be able to log into this server with desktop of their own. I used vnc quiet successfully before. What else can I use? 
By the way, I used redhat enterprise linux before and vncserver does work on their x86-64 version. So I presume it does work in Fedora 4. 

I would prefer somebody who actually has a working solution to comment.

---

### Post by Belfast on 2005-11-06
i had the same problem

after reading anither post on this forum somewhere I edited the /etc/vnc.conf and added the following to the bottom of the file:
$fontPath .= "/usr/share/X11/fonts/misc/,";
$fontPath .= "/usr/share/X11/fonts/75dpi/:unscaled,";
$fontPath .= "/usr/share/X11/fonts/100dpi/:unscaled,";
$fontPath .= "/usr/share/X11/fonts/Type1/,";
$fontPath .= "/usr/share/X11/fonts/Speedo/,";
$fontPath .= "/usr/share/X11/fonts/75dpi/,";
$fontPath .= "/usr/share/X11/fonts/100dpi/,";
$fontPath .= "/usr/share/X11/fonts/freefont/,";
$fontPath .= "/usr/share/X11/fonts/sharefont/";

bingo it worked

---

### Post by Rugger on 2006-01-05
That takes care of the font problem but not the fact that port 5901 is not showing up in netstat even though the script said vncserver was started. It works fine oh my other computers, but they are x86 and not an AMD 64.

---

### Post by Rugger on 2006-01-10
So am I the only one who hasn't got vncserver to work with AMD64 and Kubuntu?  When I start vncserver, the script saids that the service was started successfully.  However netstat doesn't show port 5901 as running. I checked and made sure it wasn't running on any other port also.  Also, when I do a vncserver -kill :1 it saids it's terminated the service, but there are still locks in the tmp folder (X1-lock) that I have to manually delete or next time I run vncserver it saids there's a lock then starts the service on the next unlocked number (i.e. 2).  So the starting of the vncserver isn't working and then the kill command isn't working also.  Help please.

---

### Post by gmontag on 2006-01-11
I am seeing the same thing.  I am also looking at trying to freenx working on the 64 bit install.  SSH works but I would like something graphical.

---

### Post by awi on 2006-01-16
Hello, I'm having the same kind of problems trying to use 

vncserver 3.3.7-7ubuntu1 from Miscelaneous - Graphical (Universe)

and got this message on /var/log/syslog

Jan 15 16:21:06 localhost kernel: [ 1395.376150] Xrealvnc[9096]: segfault at ffffffffab3a96e8 rip 00002aaaab1fa84b rsp 00007fffff8cbeb0 error 4

Even though, as reported on this thread, the script reports that was started ok. I tried the "font fix", and did not work.
I found this thread on debian's bug list:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=276948](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=276948)

it seems that there is no solution to the problem yet :(

I'm running Ubuntu 5.10 on AMD64 (Sempron)

---

### Post by kingkong on 2006-02-09
Hi, I got the vncserver working!!

Check out the debs

vnc4server, vnc4common xvnc4viewer etc deb files from the following website and install by doing
sudo dpkg -i [all .deb file names here]

[http://qt1.iq.usp.br/download](http://qt1.iq.usp.br/download)

[http://lists.debian.org/debian-amd64/2005/10/msg00657.html](http://lists.debian.org/debian-amd64/2005/10/msg00657.html)

Works perfectly for me!
I have amd64.

:KS :) :KS

---

### Post by ecliptik on 2006-03-16
I used these debs and they worked great for a couple days. Then all of a sudden the VNC session wouldn't start any new apps, so I just figured it was a bug and killed/restarted the vncserver (vncserver -kill :02). When I brought it backup though I just had the grey X screen and cursor. 

I played around with ~/.vnc/xstart, ~/.Xsession, ~/.xinitrc but no matter what I got the same screen. Finally I ran Xvnc by itself and passed the options I wanted (/usr/bin/vncserver is a perl script) and it only worked when I did a -query localhost to pull up GDM, which then started a window manager.

Using GDM lead to other problems, if I wanted to restart GDM on screen 0 (something I commonly do to test out some mythtv tweaks) it takes down my GDM vncsession. It also occasionally won't refresh while typing, I have to move the mouse to get it to do a screen refresh.

I'm downloading and making the debs from the source (amd64 deb repositories) and see what happens. But has anyone else experienced something similiar? Maybe have any ideas on how to get a window manager to run without GDM.

Thanks.

---

### Post by ecliptik on 2006-03-17
I also tried using the 32bit debs in a chroot and still no luck.

---

### Post by ecliptik on 2006-03-17
I'm an idiot, it was a problem with my /etc/hosts. The hostname of the machine must be related to 127.0.0.1 not a real IP address. It only did this after I tried diablo II because D2 needs the hostname to have a real IP.

---

### Post by kingkong on 2006-03-18
I just type gnome-session in the terminal once I start the vncserver and open it through vncviewer. It will start the gnome environment. I guess you can put that in .vnc/xstartup file at the end..
So far I am happy with it, but fedora 64 bit vncserver is very stable and works just fine. There you just have to comment out a couple of lines in the .vnc/xstartup file. I suppose that rpm can be converted to .deb if reqd.

---

### Post by kalahari875 on 2006-04-27
I had the same problem with vncserver starting until I did the following:

[QUOTE=Belfast]i had the same problem

after reading anither post on this forum somewhere I edited the /etc/vnc.conf and added the following to the bottom of the file:
$fontPath .= "/usr/share/X11/fonts/misc/,";
$fontPath .= "/usr/share/X11/fonts/75dpi/:unscaled,";
$fontPath .= "/usr/share/X11/fonts/100dpi/:unscaled,";
$fontPath .= "/usr/share/X11/fonts/Type1/,";
$fontPath .= "/usr/share/X11/fonts/Speedo/,";
$fontPath .= "/usr/share/X11/fonts/75dpi/,";
$fontPath .= "/usr/share/X11/fonts/100dpi/,";
$fontPath .= "/usr/share/X11/fonts/freefont/,";
$fontPath .= "/usr/share/X11/fonts/sharefont/";[/QUOTE]

Now I am trying to set up xinetd to start VNC upon request and give a KDM login screen (I am running Kubuntu 5.10). I am having a devil of a time with this. I have tried using [these instructions]("http://groups.google.com/group/DerekYang/browse_thread/thread/37e6d6c192a32ab1/3502dd4a042384c4?lnk=st&q=ubuntu+vncserver+xinetd&rnum=1#3502dd4a042384c4"), but they are aimed at GDM. 

I have set up xinetd.conf as follows:

defaults {}

includedir /etc/xinetd.d
service vnc1024
{
	disable = no
	socket_type = stream
	protocol = tcp
	wait = no
	user = nobody
	server = /usr/bin/Xvnc
	server_args = -inetd :1 -broadcast -geometry 1024x768 -depth 16 -once -fp /usr/share/X11/fonts/misc unix/:7100 -securitytypes=none
}

However, when I try to connect to display 1 from either inside or outside of the machine, I just get refused connections:

user@machine:~$ vncviewer :1
vncviewer: ConnectToTcpAddr: connect: Connection refused

I don't know how to enable XDMCP for KDM, which is likely part of the problem. Does anyone know how to do this in Kubuntu Breezy?

If I start the vncserver outside of xinetd on display 1 I can connect to it. Any thoughts? Thanks!

---

