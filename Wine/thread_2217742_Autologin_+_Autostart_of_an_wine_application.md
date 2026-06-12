---
title: "Autologin + Autostart of an wine application"
date: 2014-04-18
forum: Wine
---

### Post by sunshineh on 2014-04-18
Hi,

I have an Ubuntu 12.04 Server and want that my wine application is automatically starting after rebooting.
For that application I need my gui and network connection.

So I did the following steps:

1.Replacing the last line of the tty1.conf through
[COLOR=#0000ff][FONT=Arial]exec /bin/login -f USERNAME < /dev/tty1 > /dev/tty1 2>&1[/FONT][/COLOR]

2.Creating a ~/.bashrc File
[COLOR=#0000ff][FONT=Arial]if [ $(tty) == "/dev/tty1" ]; then[/FONT][/COLOR]
[COLOR=#0000ff][FONT=Arial]sudo start-network
sudo startx
sudo wicd-client[/FONT][/COLOR]

[COLOR=#0000ff][FONT=Arial]wine /home/testuser/.wine/drive_c/Program Files (x86)/application.exe[/FONT][/COLOR]

[COLOR=#0000ff][FONT=Arial]fi[/FONT][/COLOR]

But it isn't working. My application is starting after my login over x2go and not before.
In the auth.log are the following lines during the startup time:
pam_unix(login:session): session opened for user testserver by 
testserver(uid=0)
pam_unix(login:session): session closed for user testserver
pam_unix(login:session): session opened for user testserver by 
testserver(uid=0)
usw. (always opening and clossing the session!)

---

### Post by sunshineh on 2014-04-19
I found the error, why my session was always opening and closing. 
I had an error in my command and it has to look like that:
wine "/home/testuser/.wine/drive_c/Program Files (x86)/application.exe"

But even now it isn't working. So how can I really see, if ubuntu is autostarting my testuser with ttf1.conf and if my xserver is running??

Is there any example in the world wide web, how I can start a wine-Application which needs a gui and internet, automatically after reboot?!!!

---

### Post by Nistegmos on 2014-07-03
Use the Ubuntu Menu-->Settings-->Session & StartUp-->Application AutoStart

---

