---
title: "Wine, uTorrent, and a GUI-less server"
date: 2008-09-20
forum: Wine
---

### Post by djbon2112 on 2008-09-20
Is this at all possible? I have a server set up, but no GUI (I use SSH and Webmin to manage it). Can one install wine and uTorrent, then use uTorrent only with the WebUI? Basically, what I'm asking is if there's a way for WINE to fake a GUI for uTorrent.

---

### Post by pytheas22 on 2008-09-20
I don't think it's possible to run utorrent without X running.  But there are other (native Linux) torrent clients that will run just from the command-line.  [This article]("http://polishlinux.org/apps/p2p/rtorrent-console-p2p/") would help you set that up.  You should be able to set it up over the ssh connection with no problem.

---

### Post by Bakon Jarser on 2008-09-20
I see the article recommends rTorrent.  Bittornado also use command line.

---

### Post by asdfoo on 2008-09-21
You can install xvfb [http://en.wikipedia.org/wiki/Xvfb](http://en.wikipedia.org/wiki/Xvfb)

---

### Post by djbon2112 on 2008-09-21
> **asdfoo said:**
> You can install xvfb [http://en.wikipedia.org/wiki/Xvfb](http://en.wikipedia.org/wiki/Xvfb)

I think that might be the best solution for me. None of the Linux bittorrent apps have all the features I need, and I'm going to be using the Web interface of uTorrent anyways.

---

### Post by rascalli on 2008-12-13
Heya , did you get this to work ?

If so can you give me some pointers of what you did.

Tx

---

### Post by djbon2112 on 2008-12-15
I never did get it working... I just virtualized Windows Server 2003 and used that for uTorrent, however I'm about to migrate to rtorrent/wtorrent so I get a native, web-based torrent app. I'll let you know how it goes.

---

### Post by djbon2112 on 2008-12-19
Well, for starters, don't use rtorrent/wtorrent. Frankly they do not work well, the wtorrent interface isn't intuitive, and it just isn't nearly as good as uTorrent.

That said, I'm going to try setting up Xvfb again, maybe I'll have success this time.

---

### Post by djchester on 2009-01-07
I want to achieve the same thing here on my soon to be built NAS server running Ubuntu. uTorrent has labels which is extremely useful and the WebGUI works great when I tested it on Ubuntu Desktop with wine. But of course I want it all running without running the machine in init 5. 

I'm mainly used to RHEL since I work with it and have not played with Ubuntu in init 3. Is it any harder than RHEL? 

My backup plan is to let the the NAS run as an Ubuntu desktop but it hurts to waste resources on that. Someone has probably already done this I'm sure of it. Don't be shy, please come forward and share! ;)

Edit1: Found this thread: [http://ubuntuforums.org/showthread.php?p=6510057#post6510057](http://ubuntuforums.org/showthread.php?p=6510057#post6510057) were samuelt claims that it will work without X.

---

### Post by iBurger on 2009-08-21
Because it took me so much time to get this all to work, I'd like to add some pointers.

First, you can get uTorrent to work without x11. However, the auto-load torrent feature does not work. This makes uTorrent a pretty bad client, if you intend to do some heavy torrenting. (that is; you'll need to upload all the torrent files throught the webgui). Further I noticed that uTorrent is quite unstable when you run it without x11. 

My solution is this;
- headless debian box
- install x11
- install vncserver
- copy over uTorrent settings.dat
- launch the vncserver, wich launches utorrent.

---

### Post by iBurger on 2009-08-21
```
#! /bin/sh
### BEGIN INIT INFO
# Provides:          uTorrent/VNC
# Required-Start:    $local_fs $remote_fs
# Required-Stop:     $local_fs $remote_fs
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: uTorrent/VNC daemon
#                   
### END INIT INFO

# Author: iBurger <phatg33k@gmail.com> 

# Do NOT "set -e"

# PATH should only include /usr/* if it runs after the mountnfs.sh script
# changed: NAME, DAEMON, DESC, USER

PATH=/sbin:/usr/sbin:/bin:/usr/bin
DESC="uTorrent/VNC daemon"
NAME=vncserver
DAEMON=/usr/bin/$NAME
SCRIPTNAME=/etc/init.d/utorrent
TITLE=x11_uTorrent
PID=`ps -ef | grep $TITLE | grep -v grep | awk '{print $2}'`
USER=michael

# Exit if the package is not installed
[ -x "$DAEMON" ] || exit 0

# Read configuration variable file if it is present
[ -r /etc/default/$NAME ] && . /etc/default/$NAME

# Load the VERBOSE setting and other rcS variables
. /lib/init/vars.sh

# Define LSB log_* functions.
# Depend on lsb-base (>= 3.0-6) to ensure that this file is present.
. /lib/lsb/init-functions

#
# Function that starts the daemon/service
#

do_start()
{
	echo "Starting uTorrent/VNC daemon..."
	su $USER -c "$NAME -name $TITLE :125"
}

#
# Function that stops the daemon/service
#
do_stop()
{
	echo "Killing uTorrent/VNC daemon with sig 15..."
	su $USER -c "$NAME -kill :125"
}

#
# Function that sends a SIGHUP to the daemon/service
#
do_reload() {
	echo "Reloading uTorrent/VNC daemon..."
	kill -15 $PID
	su $USER -c "$NAME -name $TITLE :125"
}

case "$1" in
  start)
	[ "$VERBOSE" != no ] && log_daemon_msg "Starting $DESC" "$NAME"
	do_start
	case "$?" in
		0|1) [ "$VERBOSE" != no ] && log_end_msg 0 ;;
		2) [ "$VERBOSE" != no ] && log_end_msg 1 ;;
	esac
	;;
  stop)
	[ "$VERBOSE" != no ] && log_daemon_msg "Stopping $DESC" "$NAME"
	do_stop
	case "$?" in
		0|1) [ "$VERBOSE" != no ] && log_end_msg 0 ;;
		2) [ "$VERBOSE" != no ] && log_end_msg 1 ;;
	esac
	;;
  #reload|force-reload)
	#
	# If do_reload() is not implemented then leave this commented out
	# and leave 'force-reload' as an alias for 'restart'.
	#
	#log_daemon_msg "Reloading $DESC... " "$NAME"
	#do_reload
	#log_end_msg $?
	#;;
  restart|force-reload)
	#
	# If the "reload" option is implemented then remove the
	# 'force-reload' alias
	#
	log_daemon_msg "Restarting $DESC"
	do_stop
	case "$?" in
	  0|1)
		do_start
		case "$?" in
			0) log_end_msg 0 ;;
			1) log_end_msg 1 ;; # Old process is still running
			*) log_end_msg 1 ;; # Failed to start
		esac
		;;
	  *)
	  	# Failed to stop
		log_end_msg 1
		;;
	esac
	;;
  *)
	#echo "Usage: $SCRIPTNAME {start|stop|restart|reload|force-reload}" >&2
	echo "Usage: $SCRIPTNAME {start|stop|restart|force-reload}" >&2
	exit 3
	;;
esac

:
```

---

### Post by iBurger on 2009-08-21
This file actually lauches uTorrent. its located in your home directory, under **/HOME/user/.vnc/xstartup**

```
#!/bin/sh

# Uncomment the following two lines for normal desktop:
# unset SESSION_MANAGER
# exec /etc/X11/xinit/xinitrc

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
x-window-manager & x-window-manager & wine /opt/uTorrent/utorrent.exe

```

---

### Post by rascalli on 2009-08-21
very good solution for this : 

Rtorrent with rutorrent (gui)

very very nice , has some nice plugins & looks like utorrent webui

[img]http://img21.imageshack.us/img21/9974/scr1big.jpg[/img]

[img]http://img12.imageshack.us/img12/2846/scr2big.jpg[/img]

[img]http://img21.imageshack.us/img21/9635/scr3big.jpg[/img]


rutorrent : [http://code.google.com/p/rutorrent/](http://code.google.com/p/rutorrent/)
rtorrent : [http://libtorrent.rakshasa.no/](http://libtorrent.rakshasa.no/)

---

### Post by grimd34th on 2009-08-22
or torrent flux would be good just install python and mysql

---

### Post by iBurger on 2009-08-26
uTorrent has been very stable. In the screen-shot it has been running for a month or so; currently with 246 torrents loaded. The Webgui gets unresponsive when you delete a big torrent file though. 


[IMG]http://i25.tinypic.com/aljdqr.jpg[/IMG]

---

### Post by PDG1 on 2010-10-11
can't remember when it came out but utorrent has a linux server alpha available now on their site :P

---

### Post by onemyndseye on 2010-10-14
yes and dont overlook qBittorrent as well.  Its nearly a clone of Utorrent and has a headless version with WebUI :)

---

