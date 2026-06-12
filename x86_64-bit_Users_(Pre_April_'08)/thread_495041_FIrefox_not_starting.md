---
title: "FIrefox not starting"
date: 2007-07-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by sra136 on 2007-07-07
Hi,
I just removed residual config packages from Synaptic.  However, when trying to start Firefox, the "Starting Firefox Web Browser" is seen by Firefox doesn't start.  At the moment I am using the Firefox shell script I copied onto the desktop from /usr/lib/firefox.  

When I start firefox from the terminal, I get this error:

/opt/firefox/firefox-bin: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory

I tried reinstalling but that did not work.  Any suggestions.

---

### Post by dmfield on 2007-07-10
Got this from [URL="https://answers.launchpad.net/ubuntu/+question/9266"]https://answers.launchpad.net/ubuntu/+question/9266
[/URL]

> Please try the following:
 sudo mv /opt/firefox /opt/firefix.tmp
 Then try to start firefox by clicking on the icon in the menu. If it does not show up, make a right click on the top menu button (in the task bar) and chose "edit menus". Navigate to the firerox entry and make shure it says "firefox %u".
 No open a console again and type
 ls -l /usr/bin/firefox
 It should show you that this is a symlink. It should look very similar to this:
 lrwxrwxrwx 1 root root 22 2007-06-03 10:43 /usr/bin/firefox -> ../lib/firefox/firefox
 If it looks different, type:
 sudo mv /usr/bin/firefox /usr/bin/firefox.tmp
sudo ln -s /usr/lib/firefox/firefox /usr/bin/firefox
 And then please tell us everything is fine again :)


Might help?

---

