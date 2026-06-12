---
title: "reboot / halt / shutdown command fails"
date: 2009-03-27
forum: x86 64-bit Users
---

### Post by will136 on 2009-03-27
Hi - I have two separate Ubuntu 7.10 VM's running on a CentOS host which have recently stopped responding to the following commands:
reboot now
shutdown -h now
halt

The systems will broadcast that they are shutting down but never do.

---

### Post by will136 on 2009-04-07
Quick update -  note that in the VMWare server console the command to reboot / shutdown etc does take effect and the process does start.  However here is the output from the console (which hangs)

Stopping VMware Tool services in the virtual machine:	Stopping
	Guest operating system daemin:-ne		done
	Guest filesystem driver:-ne			done

* Stopping Avahi mDNS/DNS-SD Daemon avahi-daemin	[ OK ]
Stopping VMware Tool services in the virtual machine:	done
	Guest operating system daemin:-ne		done
	Guest filesystem driver:-ne			done
* Stopping Avahi mDNS/DNS-SD Daemon avahi-daemin	[ OK ]

I've seen discussions about reboot being unpredictable - especially in a VM environment but nothing re. shutdown.  Any comments?

Thanks

---

### Post by mhgsys on 2009-04-07
try :
```

sudo shutdown -h -P now

```

the -P stands for power off

---

### Post by silky05 on 2009-04-09
I have a PC that would not reboot/restart with any Ubuntu based linux distribution. I found out that the ALSA-utils module in the directory /etc/init.d needed to be edited as root (using your favorite text editor) and add the two following lines immediately after the STOP statement (ln# 354 AND 355):

stop)
     ifconfig wlan0 down
     ifconfig eth0 down
    
That line should look like this:

stop)
        ifconfig wlan0 down 
        ifconfig eth0 down
	EXITSTATUS=0

Save the alsa-utils after adding the above two lines and see attempt the reboot/restart/shutdown now works.

If it still doesn't work, disable these Two services **acpi** and **apm** under System | Administration | Services. (must have root access to disable these services).

You should be able to do proper shutdowns/restarts/reboots. A least it worked for me.

---

