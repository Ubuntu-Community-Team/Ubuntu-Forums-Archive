---
title: "Problems with TightVNC"
date: 2006-07-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by jdmpike on 2006-07-27
All,

I am following this ([http://www.vanemery.com/Linux/VNC/vnc-over-ssh.html](http://www.vanemery.com/Linux/VNC/vnc-over-ssh.html)) great tightVNC tutorial and am getting the following error.

```
tightvncserver :64 -geometry 1024x768 -depth 16 -name luckyseven
Couldn't start Xtightvnc; trying default font path.
Please set correct fontPath in the tightvncserver script.
Couldn't start Xtightvnc process.

MAXSOCKS=1000
MAXSOCKS=1000


```

I have scoured the net and it seems this might be an amd64 issue?
([http://www.usalug.org/phpBB2/viewtopic.php?p=67230](http://www.usalug.org/phpBB2/viewtopic.php?p=67230))

Here is my /etc/vnc.conf

```

# /etc/vnc.conf written by Marcus Brinkmann. This file is in the Public Domain.
#
# This is the configuration file for the vncserver package.
# It is perl syntax, but only variable assignment is allowed.
# A semicolon will be added if missing.
# Every value has suitable defaults, so you probably don't need any file.
#
# This file will be sourced by `vncserver' and `vncpasswd'.
# After this file, $(HOME)/.vncrc will be sourced, so values can be
# overwritten on a per-user basis. If you want to reactivate the default
# value there, you have to specify an empty value. For example, $fontPath
# will set to the default value after
#
# $fontPath = "/foo";
# $fontPath = "";
#
# If you are missing something, please let me know.
# Marcus.Brinkmann@ruhr-uni-bochum.de

# System configuration
# --------------------
#
# This section contains entries that should be true for all users.

#$vncClasses should be the path to the java classes of server.
#$vncClasses = "/usr/share/vncserver";

# $XFConfigPath   can be set to the global XF86Config file. This will be
#                 parsed to gain default values for $fontPath and $colorPath.
#                 If you want to disable this feature, point it to an
#                 invalid file, "/foo" for example.
$XFConfigPath = "/etc/X11/xorg.conf";

# $fontPath should be a comma seperated list of fonts to be added to the font
#           path. If not specified, and $XFConfigPath is valid, vncserver
#           will read the $fontPath from there. If both are not set, the
#           default will apply.
# Example: $fontPath = "tcp/localhost:7100";     # would make vnc to use xfs.
# Example: $fontPath = "";
$fontPath = "/usr/share/X11/fonts/misc/"
$fontPath .= "/usr/X11R6/lib/X11/fonts/misc/,";
$fontPath .= "/usr/X11R6/lib/X11/fonts/75dpi/:unscaled,";
$fontPath .= "/usr/X11R6/lib/X11/fonts/100dpi/:unscaled,";
$fontPath .= "/usr/X11R6/lib/X11/fonts/Type1/,";
$fontPath .= "/usr/X11R6/lib/X11/fonts/Speedo/,";
$fontPath .= "/usr/X11R6/lib/X11/fonts/75dpi/,";
$fontPath .= "/usr/X11R6/lib/X11/fonts/100dpi/,";
$fontPath .= "/usr/X11R6/lib/X11/fonts/freefont/,";
$fontPath .= "/usr/X11R6/lib/X11/fonts/sharefont/";
$fontPath .= "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,";
$fontPath .= "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID";

# I don't know what the default is, though.

# $colorPath should be the RGB file to be used by X. This can also be taken from#            XF86Config file if specified by $XFConfigPath
$colorPath = "/usr/lib/X11/rgb";

# User configuration
# ------------------
#
# This section contains entries that may change from user to user.

# $vncUserDir contains the filename for the log files directory of Xvnc
#             (the server) and the viewers that are connected to it.
#$vncUserDir = "$ENV{HOME}/.vnc";

# $vncPasswdFile contains the filename of the password file for Xvnc.
# $vncPasswdFile = $vncUserDir . "/passwd";

# $vncStartup points to a script that will be started at the very beginning.
$vncStartup = "/usr/bin/startxfce4";

# $xauthorityFile should be the path to the authority file that should be used
#                 by your vnc X server.
# $xauthorityFile = "$ENV{HOME}/.Xauthority";

# $defaultDesktopName should be set to the default name of the desktop.
#                     This can be changed at the command line with -name.
# $defaultDesktopName = "X";

# $geometry sets framebuffer width & height. Default will be calculated if
#           server is started from within a running X servers. Can be changed at#           the commandline (-geometry). A fixed default will be used if
#           vncserver is not invoked in a running X session.
# Example:  $geometry ="640x480";

# $depth       sets the framebuffer color depth. Must be between 8 and 32.
# $pixelformat sets the default pixelformat.
#              The default will be calculated if none of both is specified
#              and when vncserver is called from within a running X servers.
#              Can be changed at the command line with option -depth.
#              A fixed default value will be used if vncserver is not
#              invoked in a running X session.
# Example:  $depth = "16";
#           $pixelformat = "rgb565";

# $getDefaultFrom sets the display from which you can query the default of
#                 the above three options, if you don't want to start vncserver
#                 from within a running X server. It will be added to the call
#                 of xdpyinfo.
#                 It is useful to get the default from the X server you will
#                 run xvncviewer in.
# Example:  $getDefaultFrom = "-display localhost:0"

# $rfbwait sets the maximum time in msec to wait for vnc client viewer.
# $rfbwait = "120000";

```

Can you think of anything that would be causing me these silly problems?

Peace, love, ubuntu,

jdmpike

---

### Post by jdmpike on 2006-07-27
After more searching... it looks like it might have even been a filed bug for the AMD64 architecture!

[http://bugs.donarmstrong.com/cgi-bin/bugreport.cgi?bug=335849](http://bugs.donarmstrong.com/cgi-bin/bugreport.cgi?bug=335849)

If so, this really bums me out. I have a 64-bit server and need *something* that runs on AMD64 so I can manage my headless server a little easier.

Thanks in advance,

jdmpike

---

### Post by jdmpike on 2006-07-27
Does no one use TightVNC to remotely manage their 64-bit ubuntu install?

I would like to hear what people do have working if no one can offer assistance with my problem. I only picked tightVNC because I could find tutorials for what I wanted to do, i.e. vnc through an ssh tunnel.

Thanks,

jdmpike

---

### Post by incubus on 2006-07-28
jdmpike,

I haven't been following the forums, so I'm sorry for a late reply to our post.  When I got my 64bit machine (which I had to return), TightVNC was one of the first things I tried to install -- unsuccessfully as well.

As I recall, the problem is not in the 64 bit platform, but in TightVNC itself (some deprecated dependencies).  Unfortunately, the developers are not very willing to port it so soon.

Because of that, I decided to use a different VNC server.  I can't recall which one, exactly, but you can choose yourself:
$ apt-cache search vncserver

I was pretty satisfied with the other one.  If you don't use dial-up, I don't think you will notice any difference.  With high speed internet, we don't need to be that "aggressive" about compression anymore. Over a LAN, you may even bring down the compression level, to save your CPU from some stress.

Hope it helps,
incubus

PS: I think I was using vnc4server.  I heard there are even some cool things you can do with it, which you can find in the forums.

PPS: And in case you wonder, TightVNC can connect to it as well.

---

### Post by jehosephat on 2006-11-09
I've been wrestling with this ever since upgrading from FC4 ... FC5 & 6 are both susceptible to this bug.  There's a bugzilla report of this and I don't know enough to find out if it's been fixed.  My problem is that any of the vnc servers I try to install (including tightvnc and the vnc4server in Dapper Drake repositories) result in a crash when starting vncserver ("X error: blah blah ... BadLength .. blah blah ... Major opcode: 134 ... blah blah ... serial # of failed request: 65").  I can avoid this if I download the vnc4 .deb packages that have apparently been "fixed" for amd64 (see [this]("http://www.ubuntuforums.org/showthread.php?t=122402") HOWTO) ... but even then, when I connect over VNC and try to start anything more complicated than a terminal on the virtual desktop, I run into segmentation faults.  I think I've also seen this reported with respect to the amd64 bug, so maybe the "fixed" vnc4 packages aren't really fixed??

I'd love to hear of anyone who knows of a solid workaround for VNC tunneling through SSH for amd64 ... it seems to be a problem with FC5&6 and Ubuntu 6.06 and 6.10 at least ...

---

