---
title: "Avahi-daemon failed on startup -"
date: 2008-06-26
forum: x86 64-bit Users
---

### Post by paul sanz on 2008-06-26
Hi  ](*,)

Avahi-daemon has failed to start due to dbus comunucation fault see syslog and causing numerous problems when trying to login and GUI.

Is there a quick solution to this problem or do i have to reinstall everything :(


syslog:
Jun 26 15:18:48 gamco6 avahi-daemon[5859]: dbus_bus_get_private(): Did not receive a reply. Possible causes include: the application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or thrk connection was broken.
Jun 26 15:18:48 gamco6 avahi-daemon[5859]: WARNING: Failed to contact D-Bus daemon.
Jun 26 15:21:14 gamco6 avahi-daemon[5837]: Found user 'avahi' (UID 109) and group 'avahi' (GID 120).
Jun 26 15:21:14 gamco6 avahi-daemon[5837]: Successfully dropped root privileges.
Jun 26 15:21:14 gamco6 avahi-daemon[5837]: avahi-daemon 0.6.22 starting up.
Jun 26 15:21:14 gamco6 avahi-daemon[5837]: dbus_bus_get_private(): Did not receive a reply. Possible causes include: the application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or thrk connection was broken.
Jun 26 15:21:14 gamco6 avahi-daemon[5837]: WARNING: Failed to contact D-Bus daemon.

---

### Post by Dixon Bainbridge on 2008-06-27
Try disabling it:

sudo gedit /etc/default/avahi-daemon

then

cat /etc/default/avahi-daemon 
# 0 = don't start, 1 = start
AVAHI_DAEMON_START=0

save file and restart

---

