---
title: "[Help]Upgrade from 7.10 server x64 to LTS 8.04"
date: 2008-05-06
forum: x86 64-bit Users
---

### Post by bigbro on 2008-05-06
Hello!

I have problems after upgrading from 7.10 server x64 (with installed xubuntu-desktop) to LTS 8.04. All is running fine with little increased hdd activity, have no idea why... anyway.. after upgrading finished I restart machine. Before I have graphic xubuntu and it was easy for me to manage my servers. Now when new 8.04 starts ... I can't see old desktop graphics (taskbar, icons etc), only terminal. Well I manage to run my servers with terminal, but it will be much easy for me like before with graphics/desktop system like xubuntu. (I am not good with terminal and commands).

How to get things like taskbar etc back? Sorry for lame and stupid questions. Please help

---

### Post by inphektion on 2008-05-06
maybe 
sudo aptitude install xubuntu-desktop or 
sudo aptitude reinstall xubuntu-desktop
will fix something for you.
One of my apps was broke after an upgrade to hardy and doing a reinstall found a bunch of dependencies that were broken or had to be installed.  but it fixed it.

---

### Post by bigbro on 2008-05-06
> **inphektion said:**
> maybe 
sudo aptitude install xubuntu-desktop or 
sudo aptitude reinstall xubuntu-desktop
will fix something for you.
One of my apps was broke after an upgrade to hardy and doing a reinstall found a bunch of dependencies that were broken or had to be installed.  but it fixed it.

thanks. I will test this and will report. I didn't try to upgrade xubuntu...,but I think it should upgrade xubuntu when upgrading to 8.04...
I try 
sudo apt-get install xubuntu-desktop
and it said that xubuntu is already installed and nothing happend. :(

---

### Post by inphektion on 2008-05-06
try the reinstall.

---

### Post by bigbro on 2008-05-07
> **inphektion said:**
> try the reinstall.

I try 

sudo aptitude reinstall xubuntu-desktop

and it is reinstalled. Still no icons and that terminal. Now I can see desktop with some strange bird, no icons, no taskbar, only window with terminal. I can't move that terminal window. When I write 

xfce4-panel

I have taskbar, but no icons. I can open web browser, but can't manipulate that window.

I really have no idea what is happend :( Please help

---

### Post by bigbro on 2008-05-07
when I try to run xfce4-panel it is ok. It's running until reboot. After reboot I need to run it again.
When I try to run xfdesktop it is running until reboot. 
I got some criticals in terminal:

```

$ xfdesktop
xfce-mcs-manager-Message: Standard XSETTINGS manager already detected for screen 0

(xfce-mcs-manager:5976): libxfce4mcs-CRITICAL **: Unable to add channel "settings" to MCS manager

(xfce-mcs-manager:5976): libxfce4mcs-CRITICAL **: Unable to add channel "settings" to MCS manager
** Message: Querying XINPUT extension
** Message: XINPUT extension found
** Message: Querying Xkb extension
** Message: Xkb extension found

(xfce-mcs-manager:5976): libxfce4mcs-CRITICAL **: Unable to add channel "settings" to MCS manager
** Message: Querying XF86Misc extension
** Message: XF86Misc extension found
** Message: Querying Xkb extension
** Message: Xkb extension found

```

When I try to manipulate window manager from settings, I can't. It said that can't run window manager.
I was thinking to run xfdesktop, xfce4-panel and window manager with autorun script, but how to do that...

---

