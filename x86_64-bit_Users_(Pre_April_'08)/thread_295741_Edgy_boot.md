---
title: "Edgy boot"
date: 2006-11-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by beni10 on 2006-11-08
hello,

is it posible to have the same output as in /var/log/boot file on boot console during Edgy startup? What aplication control output massages from daemons on console during boot process in Edgy?:-k Is there connection with 
new upstart service?

thanx

---

### Post by kuja on 2006-11-08
To get these messages showing again, you need to edit your /boot/grub/menu.lst file. Open it with root privileges with your favorite editor, (ie: kdesu kate /boot/grub/menu.lst) and then look for a section of lines like this:

> ## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

Remove the word quiet, and save the file.

Afterwards, in a terminal, type this:
```
sudo update-grub
```

From now on it will display those messages while you're booting up.

---

### Post by beni10 on 2006-11-09
Thanx for the help, but this is not complete solution for me. I still don't have full output from services. For egzample, during dapper booting time, after starting slmodemd service the output was: * Starting SmartLink modem driver, symbolic link /dev/ttySL0--> /dev/pts0 created; modem modem:1 created. TTY is /dev/pts0. On edgy i only have * Starting Smartlink modem driver... with no aditional output.

---

### Post by kuja on 2006-11-09
Try turning off usplash as well then. It can be done in the same manner as turning off quiet described above. Perhaps that will give you full output, and as an added bonus you'll boot about 2 seconds faster :)

---

### Post by beni10 on 2006-11-09
I did this already but it didn't help. I think that there are some structural 
changes in booting procedures by Edgy release in comparing with Dapper but can't figure out what.

---

### Post by kuja on 2006-11-09
That, or perhaps the related init script has been changed. Take a look if you want to, it would be stored in /etc/init.d/

---

### Post by beni10 on 2006-11-09
Init scripts are practical the same and also the /lib/lsb/init-functions file. Already tried to change these files with no result. I also noticed that there is no inittab file in Edgy, which is replaced with upstart service in etc/event.d. I'm running out of ideas and probably will stick by Dapper.

---

### Post by beni10 on 2006-11-09
... and the funny part is that in /var/log/boot file i have the full output from services on specific run level.

---

### Post by kuja on 2006-11-09
I noticed the lack of the inittab file too, a while ago... though now I forget what I wanted to do with it. 

Mind posting the init script... I'd like to look at it just to see something.

---

### Post by beni10 on 2006-11-10
the code:

#!/bin/sh
#

. /lib/lsb/init-functions

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DAEMON=/usr/sbin/slmodemd
NAME=slmodemd
PIDFILE=/var/run/$NAME.pid
MODULI="snd-intel8x0m snd-via82xx-modem snd-atiixp-modem"
UKLONI="snd-intel8x0m snd-via82xx-modem snd-atiixp-modem"
DESC="SmartLink modem daemon"

test -x $DAEMON || exit 0

# Source configuration
CONFIG=/etc/default/$NAME
if [ -f $CONFIG ]; then
        . $CONFIG
fi

start() {
    log_action_begin_msg "Starting SmartLink Modem driver:"
    if grep -i "\[Modem   " -i /proc/asound/cards ; then
           # already loaded, just pick up the device there
           kernmodul;
           modem;
    fi
    sleep 1
    RETVAL=$?
}

stop() {
    log_action_begin_msg "Shutting down SmartLink Modem driver normally"
    RETVAL=0
    if [ "`pidof $NAME`" ] ; then 
        if start-stop-daemon --stop --verbose --pidfile $PIDFILE --exec $DAEMON --retry 1 ; then
            echo .
        else
            echo " probably failed."
            echo "Trying it the hard way (send SIGKILL all $NAME processes): " 
            killall -KILL $NAME || RETVAL=1
        fi
    else
        echo " ... no $NAME daemon running."
    fi
    test "$RETVAL" -ne 0 || rm -f "$PIDFILE"
    echo -n "Unloading modem driver from kernel ... " 
    msg="none found."
    for x in $UKLONI ; do 
        if grep -l -q "^$x " /proc/modules ; then
            $modprobe -r $x 2>/dev/null && msg="$x." || msg="failed."
        fi
    done
    echo $msg
}

status() {
    echo -n "Status of $DESC: "
    if [ ! -r "$PIDFILE" ]; then
        echo "$NAME is not running."
        exit 3
    fi
    if read pid < "$PIDFILE" && ps -p "$pid" > /dev/null 2>&1; then
        echo "$NAME is running."
        exit 0
    else
        echo "$NAME is not running but $PIDFILE exists."
        exit 1
    fi
}

kernmodul() {

unset line;

    # first check to not do unneccessary modprobe calls. Some people even put
    # it into the kernel image

    if ! line=$(grep -i "\[Modem   " /proc/asound/cards 2>/dev/null) ; then
        for x in $MODULI ; do $modprobe $x 2>/dev/null ; done

        for start_reps in `seq 100` ; do
            test -e /proc/asound/cards && line=$(grep -i "\[Modem   " -i /proc/asound/cards) && break
            sleep 0.1
        done
    fi

    if test "$line" ; then
        # ALSA driver is loaded, use it

        set $line
        return 0
    fi

    return 1
}

modem() {
    start-stop-daemon --start --verbose --pidfile $PIDFILE --exec $DAEMON -- $OPTS $SLMODEMD_COUNTRY    # tried >/dev/null output too.
    sleep 1
    RETVAL=$?
}


# See how we were called. Consider udev action too.
case "$1$ACTION" in
    
    start)
    start
    ;;

    stop|remove)
    stop
    ;;
    
    restart|reload|force-reload)
    stop
    start
    ;;
    
    status)
    status
    ;;

    *)
    echo "Usage: /etc/init.d/$NAME {start|stop|restart|status}"
    exit 1

esac

the code run with output in Dapper, but not in Edgy.

---

