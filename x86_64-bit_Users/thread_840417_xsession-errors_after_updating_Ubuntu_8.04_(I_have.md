---
title: "xsession-errors after updating Ubuntu 8.04 (I have no name!@Ubuntu:/$ )"
date: 2008-06-25
forum: x86 64-bit Users
---

### Post by paul sanz on 2008-06-25
Hi how is everyone doing? ):P

I'm writing to inform others of my problem after updating my kernel from 2.6.24.14 to 2.6.24.19 Ubuntu 8.04. 
   After doing so I've got some weird xsession-error messages when trying to login via GUI, [COLOR="Blue"]see appendix A[/COLOR], [COLOR="Red"]orbit-somebody-a8688878 is not the current user[/COLOR]. As far as I can see its recognizing usernames other than root?? and give me [COLOR="SeaGreen"]permission errors as of sessionmanager[/COLOR] error and [COLOR="Magenta"]creates sombody&gconfd tmp files[/COLOR]. But I am able to login via console but with I have no name!@Ubuntu:/$ ?? /etc/passwd is all in order and UID 1000 exists. Any ideas of what happened and how to resolve the naming problem so i can login and if anyone knows what the tmp orbit files are for and whay are they causing me so much trouble.

Thanks in advance and hope to read sombody soon.


-rw------- 1 0 root 51 2008-06-24 16:53 atievntX.jePKQq
prw------- 1 0 root 0 2008-06-25 11:48 AtiXUEvent000013e3_005382b0
drwx------ 2 0 root 4096 2008-06-24 17:40 gconfd-root
drwx------ 2 1000 psanz 4096 2008-06-25 11:49 [COLOR="Magenta"]gconfd-somebody[/COLOR]
srwxr-xr-x 1 1001 aalonso 0 2008-06-25 15:45 gnome-system-monitor.somebody.2406222895
drwxr-xr-x 2 0 root 4096 2008-06-24 16:49 hsperfdata_root
drwxrwxrwt 2 0 root 4096 2008-06-25 11:45 .ICE-unix
drwxr-xr-x 3 0 root 4096 2008-06-24 16:48 .matlab
drwx------ 2 0 root 4096 2008-06-24 17:40 orbit-root
drwx------ 2 1000 psanz 4096 2008-06-25 11:49 [COLOR="Magenta"]orbit-somebody[/COLOR]
drwx------ 2 1001 aalonso 4096 2008-06-25 15:45 [COLOR="Magenta"]orbit-somebody-a8688878[/COLOR]
drwx------ 2 1000 psanz 4096 2008-06-23 16:07 seahorse-5Oygjc
drwx------ 2 1000 psanz 4096 2008-06-23 16:05 seahorse-SStRfe
drwx------ 2 1000 psanz 4096 2008-06-25 11:45 seahorse-WlhmGL
-rw------- 1 0 root 0 2008-06-24 16:53 tmp.mXKSD10422
-r--r--r-- 1 0 root 11 2008-06-25 11:48 .X0-lock
drwxrwxrwt 2 0 root 4096 2008-06-25 11:48 .X11-unix
-rw------- 1 1000 psanz 555 2008-06-23 17:37 xses-psanz.DzGPLN

[COLOR="Navy"][COLOR="Navy"]**Apendix A // .xsession-errors**[/COLOR]

No tengo nombre!@gamco6:/$ cat /home/psanz/.xsession-errors
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=es_ES.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.

(seahorse-agent:4977): GLib-WARNING **: getpwuid_r(): failed due to: Permission denied.

** (seahorse-agent:4977): WARNING **: Owner of [COLOR="Red"]/tmp/orbit-somebody-a8688878 is not the current user[/COLOR]


(process:4977): GLib-WARNING **: getpwuid_r(): failed due to: Permission denied.

(gconf-sanity-check-2:5035): GLib-WARNING **: getpwuid_r(): failed due to: Permiso denegado.

** (gconf-sanity-check-2:5035): [COLOR="Red"]WARNING **: Owner of /tmp/orbit-somebody-a8688878 is not the currentuser[/COLOR]


** (x-session-manager:4977): [COLOR="Red"]WARNING **: Owner of /tmp/orbit-somebody-a8688878 is not the current user[/COLOR]

[COLOR="Green"]SESSION_MANAGER=local/gamco6:/tmp/.ICE-unix/4977
Could not get password database information for UID of current process: User "???" unknown or no memory to allocate password entry[/COLOR]

Failed to start message bus: Memory allocation failure in message bus
dbus-daemon exited unexpectedly
**
** ERRORgsm-dbus.c:118):gsm_dbus_daemon_start: assertion failed: (dbus_daemon_pid != 0)
¡No tengo nombre!@gamco6:/$ cat /home/psanz/.xsession-errors[/COLOR]

---------------------------------------------------------------------------
Linux (UBUNTU) 2.6.24-19 #1 x86_64 GNU/Linux
---------------------------------------------------------------------------

---

