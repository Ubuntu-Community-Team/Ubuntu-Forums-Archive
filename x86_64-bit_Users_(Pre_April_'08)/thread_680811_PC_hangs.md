---
title: "PC hangs"
date: 2008-01-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by ger_macaco on 2008-01-28
Hi. I've got an AMD X2 PC with Kubuntu Gutsy Gibbon running.

I don't know why it keeps freezing. This seems to be completely random. Sometimes happens when using firefox, sometimes when PC is downloading torrents but not being used.

It freezes the screen and keyboard lights start blinking.

Anyone knows where I could get more information about this? I mean, is there a log I could check so I can be more specific?

Many thanks in advance.

---

### Post by jeffus_il on 2008-01-28
The logs are in a folder called /var/log.
dmesg is a command which gives you a kernel log.
```
dmesg | less
``` to page comfortably thru it.
At boot you can run the memtest option to test you memory.

---

### Post by ger_macaco on 2008-01-28
I did a full memtest and got no errors.
I cannot find the error in the log doing dmesg. Any ideas?

---

### Post by jeffus_il on 2008-01-29
> Basically that means the kernel panic()'ed.  What caused it is probably too
late to diagnose now 

Could be a kernel bug, could be a hardware problem.The internet is full stuff about keyboard lights flashing/blinking, I found nothing really convincing except the repeated possibility of "kernel panic" and "hardware problem", will keep looking, have a good look at your hardware in the meantime.

Also try to run lm_sensors and a gui like xsensors or a kde/gnome equivalent, with these tools, you can watch CPU temperature, voltages and fan speeds, I would pay particular attention to CPU temperature.

---

### Post by ger_macaco on 2008-01-29
Many Thanks. Also, I'd add that firefox usually closes itself without giving any error message. It just disappears. Don't know if it has something to do with the issue.
Did an overnight memtest. Run 11 tests without any errors.

lm-sensors is now installed and running. Will leave the PC downloading torrents (as usual when it freezes) and see if I can find out something with this.

I would also like to test the hard drive. What would you advice to do this?

---

### Post by jeffus_il on 2008-01-29
> **ger_macaco said:**
> Many Thanks. Also, I'd add that firefox usually closes itself without giving any error message. It just disappears. Don't know if it has something to do with the issue.

Would like to test the hard drive. What would you advice to do this?

fsck is a program that tests the file system, and I would assume that if you disk was problematic, it would show up as an error in fsck.

You could also see if "smart" is enabled on your hard disk. It is the disks internal method of checking itself and logging, status and errors, You could install a package called "smartmontools" to keep track of your hard disk.

---

### Post by ger_macaco on 2008-01-29
I did test the disk with smartmontools (SMART enabled). Performed 3 different tests and all of them returned no errors.
Also checked CPU temperature with lm-sensors. I think everything is fine as uptime is almost 6 hs and both cores are below 25 °C.

As kbluetooth was crashing at startup and neither the bluetooth dongle nor the pen drive where recognized if they where pluged at boot, I unplugged them.

Also yesterday got an update from adept (KDE libs).

After all this, computer is not freezing anymore. At least until now. Instead, ktorrent crashed once.

Wouldn't really know if crashes were due to kde libs, ktorrent, usb dongle or pen drive or what.

Is there a solution for the USB issue?

Many thanks again for all your help. I really appreciate it.

---

### Post by ger_macaco on 2008-01-29
Finally, it did freeze again.

It happened when I stopped using it. It stayed idle downloading with ktorrent. Also ksensora was open. I saw the cpu monitor was showing 0.0 on every indicator (idle, sys, user..)

This time keyboard LEDs did not blink.

---

### Post by Yellow Pasque on 2008-01-29
In my experience, random freezes like this are often caused by RAM or expansion cards not being pushed into the slot far enough. I would take the time to reinsert those items and rule it out as a possible cause. Press hard and make sure the retention clip (on RAM and some PCIe slots) locks into place from the force of the insertion. There's no need for a hammer, but don't be too gentle either.

---

### Post by ger_macaco on 2008-01-29
Checked RAM slots and are OK.

I can now say that I'm sure it only happens when idle.
No more than 5 minutes before it freezes.

---

### Post by jeffus_il on 2008-01-30
Check your screensaver settings, cancel the screensaver and see what happens. Sometimes this happens when one of the savers uses graphics functionality that your adaptor does not support.

---

### Post by ger_macaco on 2008-01-30
> **jeffus_il said:**
> Check your screensaver settings, cancel the screensaver and see what happens. Sometimes this happens when one of the savers uses graphics functionality that your adaptor does not support.

Screensaver is not enabled.

---

### Post by jeffus_il on 2008-01-30
Can you post the output of ```
ps -ef
```

---

### Post by ger_macaco on 2008-01-30
```
UID        PID  PPID  C STIME TTY          TIME CMD
root         1     0  0 09:31 ?        00:00:01 /sbin/init
root         2     0  0 09:31 ?        00:00:00 [kthreadd]
root         3     2  0 09:31 ?        00:00:00 [migration/0]
root         4     2  0 09:31 ?        00:00:00 [ksoftirqd/0]
root         5     2  0 09:31 ?        00:00:00 [watchdog/0]
root         6     2  0 09:31 ?        00:00:00 [migration/1]
root         7     2  0 09:31 ?        00:00:00 [ksoftirqd/1]
root         8     2  0 09:31 ?        00:00:00 [watchdog/1]
root         9     2  0 09:31 ?        00:00:00 [events/0]
root        10     2  0 09:31 ?        00:00:00 [events/1]
root        11     2  0 09:31 ?        00:00:00 [khelper]
root        30     2  0 09:31 ?        00:00:00 [kblockd/0]
root        31     2  0 09:31 ?        00:00:00 [kblockd/1]
root        32     2  0 09:31 ?        00:00:00 [kacpid]
root        33     2  0 09:31 ?        00:00:00 [kacpi_notify]
root       148     2  0 09:31 ?        00:00:00 [kseriod]
root       183     2  0 09:31 ?        00:00:00 [pdflush]
root       184     2  0 09:31 ?        00:00:00 [pdflush]
root       185     2  0 09:31 ?        00:00:00 [kswapd0]
root       238     2  0 09:31 ?        00:00:00 [aio/0]
root       239     2  0 09:31 ?        00:00:00 [aio/1]
root      2131     2  0 09:31 ?        00:00:00 [ksuspend_usbd]
root      2139     2  0 09:31 ?        00:00:00 [khubd]
root      2144     2  0 09:31 ?        00:00:00 [ata/0]
root      2145     2  0 09:31 ?        00:00:00 [ata/1]
root      2146     2  0 09:31 ?        00:00:00 [ata_aux]
root      2286     2  0 09:31 ?        00:00:00 [scsi_eh_0]
root      2287     2  0 09:31 ?        00:00:00 [scsi_eh_1]
root      2495     2  0 09:31 ?        00:00:00 [kjournald]
root      2695     1  0 09:31 ?        00:00:00 /sbin/udevd --daemon
root      3724     2  0 09:31 ?        00:00:00 [kpsmoused]
root      4167     1  0 09:31 ?        00:00:02 /sbin/mount.ntfs /dev/sda1 /media/sda1 -o rw,umask=007,gid=46
root      4424     1  0 09:31 tty4     00:00:00 /sbin/getty 38400 tty4
root      4425     1  0 09:31 tty5     00:00:00 /sbin/getty 38400 tty5
root      4427     1  0 09:31 tty2     00:00:00 /sbin/getty 38400 tty2
root      4430     1  0 09:31 tty3     00:00:00 /sbin/getty 38400 tty3
root      4431     1  0 09:31 tty1     00:00:00 /sbin/getty 38400 tty1
root      4432     1  0 09:31 tty6     00:00:00 /sbin/getty 38400 tty6
root      4618     1  0 09:31 ?        00:00:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
root      4673     2  0 09:31 ?        00:00:00 [kondemand/0]
root      4674     2  0 09:31 ?        00:00:00 [kondemand/1]
syslog    4739     1  0 09:31 ?        00:00:00 /sbin/syslogd -u syslog
root      4797     1  0 09:31 ?        00:00:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog      4799     1  0 09:31 ?        00:00:00 /sbin/klogd -P /var/run/klogd/kmsg
105       4820     1  0 09:31 ?        00:00:00 /usr/bin/dbus-daemon --system
root      4836     1  0 09:31 ?        00:00:00 /usr/sbin/NetworkManager --pid-file /var/run/NetworkManager/NetworkMa
root      4850     1  0 09:31 ?        00:00:00 /usr/sbin/NetworkManagerDispatcher --pid-file /var/run/NetworkManager
107       4869     1  0 09:31 ?        00:00:00 /usr/sbin/hald
root      4870  4869  0 09:31 ?        00:00:00 hald-runner
107       4915  4870  0 09:31 ?        00:00:00 hald-addon-keyboard: listening on /dev/input/event1
107       4921  4870  0 09:31 ?        00:00:00 hald-addon-keyboard: listening on /dev/input/event4
107       4922  4870  0 09:31 ?        00:00:00 hald-addon-keyboard: listening on /dev/input/event5
107       4940  4870  0 09:31 ?        00:00:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
107       4949  4870  0 09:31 ?        00:00:00 hald-addon-storage: polling /dev/hda (every 2 sec)
root      5019     1  0 09:31 ?        00:00:00 /usr/bin/kdm -config /var/run/kdm/kdmrc
root      5027  5019  1 09:31 tty7     00:00:50 /usr/bin/X -br -nolisten tcp :0 vt7 -auth /var/run/xauth/A:0-1SK2G0
root      5063     1  0 09:31 ?        00:00:00 /usr/sbin/cupsd
root      5091  5019  0 09:31 ?        00:00:00 -:0
root      5162     1  0 09:31 ?        00:00:00 /usr/sbin/hddtemp -d -l 127.0.0.1 -p 7634 -s | /dev/sda
root      5312     1  0 09:31 ?        00:00:00 /usr/sbin/nmbd -D
root      5313  5312  0 09:31 ?        00:00:00 /usr/sbin/nmbd -D
root      5331     1  0 09:31 ?        00:00:00 /usr/sbin/smbd -D
root      5354  5331  0 09:31 ?        00:00:00 /usr/sbin/smbd -D
root      5355     1  0 09:31 ?        00:00:00 /usr/sbin/sensord -f daemon
root      5412     1  0 09:31 ?        00:00:00 /usr/sbin/xinetd -pidfile /var/run/xinetd.pid -stayalive
avahi     5438     1  0 09:31 ?        00:00:00 avahi-daemon: running [pc-gerardo.local]
avahi     5439  5438  0 09:31 ?        00:00:00 avahi-daemon: chroot helper
root      5453     1  0 09:31 ?        00:00:00 /usr/sbin/dhcdbd --system
root      5473     1  0 09:31 ?        00:00:00 /usr/sbin/hcid -x -s
root      5488  5473  0 09:31 ?        00:00:00 /usr/lib/bluetooth/bluetoothd-service-audio
root      5491  5473  0 09:31 ?        00:00:00 /usr/lib/bluetooth/bluetoothd-service-input
root      5496     2  0 09:31 ?        00:00:00 [krfcommd]
daemon    5531     1  0 09:31 ?        00:00:00 /usr/sbin/atd
root      5545     1  0 09:31 ?        00:00:00 /usr/sbin/cron
root      5591     1  0 09:31 ?        00:00:00 /usr/bin/vmnet-bridge -d /var/run/vmnet-bridge-0.pid /dev/vmnet0 eth0
root      5610     1  0 09:31 ?        00:00:00 /usr/sbin/vmware-serverd -s -d
dhcp      5684  5453  0 09:31 ?        00:00:00 /sbin/dhclient -1 -lf /var/lib/dhcp3/dhclient.eth0.leases -pf /var/ru
gerardo   5770  5091  0 09:31 ?        00:00:00 /bin/sh /usr/bin/x-session-manager
gerardo   5813  5770  0 09:31 ?        00:00:00 /usr/bin/ssh-agent x-session-manager
root      5846     1  0 09:31 ?        00:00:00 start_kdeinit --new-startup +kcminit_startup
gerardo   5847     1  0 09:31 ?        00:00:00 kdeinit Running...
gerardo   5850     1  0 09:31 ?        00:00:00 dcopserver [kdeinit] --nosid
gerardo   5853  5847  0 09:31 ?        00:00:00 klauncher [kdeinit] --new-startup
gerardo   5855     1  0 09:31 ?        00:00:00 kded [kdeinit] --new-startup
gerardo   5860  5770  0 09:31 ?        00:00:00 kwrapper ksmserver
gerardo   5862     1  0 09:31 ?        00:00:00 ksmserver [kdeinit]
gerardo   5863  5847  0 09:31 ?        00:00:02 kwin [kdeinit] -session 101391448ed90001199824067000000604
gerardo   5865     1  0 09:31 ?        00:00:05 kdesktop [kdeinit]
gerardo   5868     1  0 09:31 ?        00:00:00 kicker [kdeinit]
gerardo   5877     1  0 09:31 ?        00:00:00 kio_uiserver [kdeinit]
gerardo   5903  5847  0 09:32 ?        00:00:01 /usr/bin/artsd -F 10 -S 4096 -s 60 -m artsmessage -c drkonqi -l 3 -f
gerardo   5927     1  0 09:32 ?        00:00:00 kmix [kdeinit] -session 10d8cecf96000111065458100000063760
gerardo   5928  5847  0 09:32 ?        00:00:00 katapult -session 10d9d39668000112680660600000081280032_1201665198_28
gerardo   5929  5847  0 09:32 ?        00:00:21 amarokapp -session 101391448ed9000119999287300000060230019_1201665198
gerardo   5968  5928  0 09:32 ?        00:00:00 aspell -a -S -C -d es -Tutf8 --encoding=utf-8
gerardo   5971     1  0 09:32 ?        00:00:00 ksensors -session 101391448ed9000120163994600000058610019_1201665198_
gerardo   5972  5847  0 09:32 ?        00:00:01 pidgin --session 101391448ed9000120110601900000060730038
gerardo   5981     1  0 09:32 ?        00:00:00 dbus-launch --autolaunch 8749bb1441ccfa6b1c20a7004783ba00 --binary-sy
gerardo   5982     1  0 09:32 ?        00:00:00 /usr/bin/dbus-daemon --fork --print-pid 7 --print-address 9 --session
gerardo   5991     1  3 09:32 ?        00:01:51 ktorrent -session 101391448ed9000120166136600000058580042_1201665198_
gerardo   5992  5847  0 09:32 ?        00:00:00 konqueror [kdeinit] --preload
gerardo   5997     1  0 09:32 ?        00:00:00 knotify [kdeinit]
gerardo   6005     1  0 09:32 ?        00:00:00 klipper [kdeinit]
gerardo   6009     1  0 09:32 ?        00:00:00 knetworkmanager [kdeinit]
gerardo   6010  5847  0 09:32 ?        00:00:00 konqueror [kdeinit] --preload
gerardo   6011  5847  0 09:32 ?        00:00:00 /usr/bin/python /usr/bin/kblueplugd
gerardo   6013     1  0 09:32 ?        00:00:02 adept_notifier
gerardo   6025  5847  0 09:32 ?        00:00:00 kio_file [kdeinit] file /tmp/ksocket-gerardo/klauncher6ZLu
gerardo   6056  5929  0 09:32 ?        00:00:00 ruby /usr/share/apps/amarok/scripts/score_default/score_default.rb
gerardo   6057  5929  0 09:32 ?        00:00:00 ruby /usr/share/apps/amarok/scripts/lyrics_lyrc/lyrics_lyrc.rb
gerardo   7264  5847  0 10:25 ?        00:00:00 /bin/sh /usr/bin/firefox
gerardo   7276  7264  0 10:25 ?        00:00:00 /bin/sh /usr/lib/firefox/run-mozilla.sh /usr/lib/firefox/firefox-bin
gerardo   7280  7276 19 10:25 ?        00:00:07 /usr/lib/firefox/firefox-bin
gerardo   7288     1  0 10:25 ?        00:00:00 /usr/lib/libgconf2-4/gconfd-2 18
gerardo   7317  7280  0 10:25 ?        00:00:00 /usr/lib/nspluginwrapper/i386/linux/npviewer.bin --plugin /usr/lib/mo
gerardo   7333  5847  3 10:26 ?        00:00:00 konsole [kdeinit]
gerardo   7334  7333  1 10:26 pts/1    00:00:00 /bin/bash
gerardo   7353  7334  0 10:26 pts/1    00:00:00 ps -ef

```

Hope this helps. Thanks!

---

### Post by jeffus_il on 2008-01-30
Nothing strange there, have you looked at /var/log/messages? See if you can see a message that looks like an error or is out of place. It's a bit big to post, Maybe you can post errors or the last bit.

---

### Post by ger_macaco on 2008-01-31
Nothing seems to be wrong in /var/log/messages.

Anyway, I managed to leave the PC idle without any freezings by blocking the session.

---

