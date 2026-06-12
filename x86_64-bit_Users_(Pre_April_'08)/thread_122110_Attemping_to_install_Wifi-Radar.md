---
title: "Attemping to install Wifi-Radar"
date: 2006-01-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by javaTard on 2006-01-26
I have moved python scripts to where I was told in the help file
Integrating with gnome 
  by Flipp Bunts <flipp.bunts@gmail.com>:
	how to get wifi-radar custom launcher to use pam authentication in gnome
        1. get wifi-radar and untar
        2. put wifi-radar.svg in /usr/share/pixmaps
        3. put wifi-radar.py in /usr/local/bin
        4. ln -s /usr/bin/consolehelper /usr/local/bin/wifi-radar
        5. vi /etc/security/console.apps/wifi-radar
                USER=root
                PROGRAM=/usr/local/bin/wifi-radar.py
                SESSION=true
        6. vi /etc/pam.d/wifi-radar
                #%PAM-1.0
                auth       sufficient   pam_rootok.so
                auth       sufficient   pam_timestamp.so
                auth       required     pam_stack.so service=system-auth
                session    required     pam_permit.so
                session    optional     pam_xauth.so
                session    optional     pam_timestamp.so
                account    required     pam_permit.so
        7. check the permissions
                sh-3.00# ls -lh /etc/security/console.apps/wifi-radar /etc/pam.d/wifi-radar
                -rw-r--r--  1 root root  /etc/pam.d/wifi-radar
                -rw-r--r--  1 root root  /etc/security/console.apps/wifi-radar
        8. add launcher
                a. right click on panel
                b. select 'add to panel'
                c. click on 'custom application luncher'
                d. options for 'create launcher'
                name : wifi-radar
                command : /usr/local/bin/wifi-radar
                icon : /usr/share/pixmap/wifi-radar.svg
        9. click on the icon, enter the root password, away you 

I wasnt able to do libe 7, which I am sure why it wont launch. But I can't get ubuntu to let me open or edit what is in line 7. Anyone have some advice for a noob?

---

### Post by slavik on 2006-01-26
which one exactly is line 7?

if it's program=... did you try 'sudo ' before that command?

---

### Post by javaTard on 2006-01-26
7. check the permissions
sh-3.00# ls -lh /etc/security/console.apps/wifi-radar /etc/pam.d/wifi-radar
-rw-r--r-- 1 root root /etc/pam.d/wifi-radar
-rw-r--r-- 1 root root /etc/security/console.apps/wifi-radar

I can't get the ls -lh /etc  thing

---

