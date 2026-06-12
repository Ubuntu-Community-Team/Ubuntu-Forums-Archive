---
title: "Boot up issue after Automatix2 update"
date: 2007-06-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by gimmy_bond on 2007-06-03
I updated my feisty 7.04 system with Automatix2 (the first time). After which the PC does boot up. However, it ends up with a command line display on the upper left corner with the first line:
myUserName@pc-name:$. 
The command line will reply with "command not found" to any attempt to login or other commands. Except for "Automatix2" which takes me back to the automatix for install or uninstalls.
 
When I type "exit". the system displays the login display.(in KDM). However, even after I login, in takes me back to the same command line.

what do I need to do to get me back to normal operation. 
I am very newbie to Ubuntu

thanks

---

### Post by arnieboy on 2007-06-03
> **gimmy_bond said:**
> I updated my feisty 7.04 system with Automatix2 (the first time). After which the PC does boot up. However, it ends up with a command line display on the upper left corner with the first line:
myUserName@pc-name:$. 
The command line will reply with "command not found" to any attempt to login or other commands. Except for "Automatix2" which takes me back to the automatix for install or uninstalls.
 
When I type "exit". the system displays the login display.(in KDM). However, even after I login, in takes me back to the same command line.

what do I need to do to get me back to normal operation. 
I am very newbie to Ubuntu

thanks

This has nothing to do with automatix.. upgrades from Ubuntu broke your KDM. 
Did you install the nvidia drivers from automatix (and do you have an nvidia card?)?

---

### Post by gimmy_bond on 2007-06-03
No I don't have an NVidia card. Anyway it refused to install it . How do I restore the KDM. Unbutu does not seem to have a provision (like Fedora and others) an option to restore / update the the system to fix the problem

---

### Post by arnieboy on 2007-06-03
> **gimmy_bond said:**
> No I don't have an NVidia card. Anyway it refused to install it . How do I restore the KDM. Unbutu does not seem to have a provision (like Fedora and others) an option to restore / update the the system to fix the problem
paste the results of the following command:
```
cat ~/.xsession-errors
```

---

### Post by gimmy_bond on 2007-06-04
arnie,
I am sorry, but I am clumsy with CLI commands. I will need more guidance. would you be more specific. 
If you mean to type on the CLI, (with the original boot up). So far every command I gave it it replied with "can not be found".
I have the system boot up with liveCD. after which I can display the file system using GNOME. It would be easier if you could tell me in which directory these errors could be found. so I could locate and post them for you.

thanks

---

### Post by arnieboy on 2007-06-04
> **gimmy_bond said:**
> arnie,
I am sorry, but I am clumsy with CLI commands. I will need more guidance. would you be more specific. 
If you mean to type on the CLI, (with the original boot up). So far every command I gave it it replied with "can not be found".
I have the system boot up with liveCD. after which I can display the file system using GNOME. It would be easier if you could tell me in which directory these errors could be found. so I could locate and post them for you.

thanks
hey its a "hidden" file called **.xsession-errors** (yes with a leading period) in your home directory (/home/**your_user_name**)

---

### Post by gimmy_bond on 2007-06-04
Arnieboy. Here is the content

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "ubuntu"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/ubuntu:/tmp/.ICE-unix/11022
Initializing gnome-mount extension
evolution-alarm-notify-Message: Setting timeout for 81699 1181088000 1181006301
evolution-alarm-notify-Message:  Wed Jun  6 00:00:00 2007

evolution-alarm-notify-Message:  Tue Jun  5 01:18:21 2007


(gnome-panel:11313): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -1 and height 24
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)

---

### Post by arnieboy on 2007-06-04
> **gimmy_bond said:**
> Arnieboy. Here is the content

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "ubuntu"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/ubuntu:/tmp/.ICE-unix/11022
Initializing gnome-mount extension
evolution-alarm-notify-Message: Setting timeout for 81699 1181088000 1181006301
evolution-alarm-notify-Message:  Wed Jun  6 00:00:00 2007

evolution-alarm-notify-Message:  Tue Jun  5 01:18:21 2007


(gnome-panel:11313): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -1 and height 24
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)

This is the .xsession-errors from your Live CD's temporarily mounted partition.. We need the one from your real Ubuntu partition's /home/user_name .. so when you boot with the live CD.. you would first need to mount that partition... (if it already isnt auto-mounted)

hey if you dont mind resetting your KDE customizations just to be able to boot into KDE.. you can do this (from your real ubuntu partition):
```
mv -f ~/.kde ~/.kde_backup
```
and then try logging in.

---

### Post by gimmy_bond on 2007-06-04
I do log in KDE. and it is on auto login. However it is the CLI which pop up after the kde is loads, and before other guis are displaed on the screen.  When I type "exit" it takes me to the KDM login. after which it takes me back to the CLI.

I did manage to go into the /.xsession-errors in my hard drive. It is empty.

what should do now. Do you still want me to execute the command which you had mosted. My system is called meir-linux

If I boot up w/o the CD  the system will not boot up all the way and I won't be able to copy and paste the tables or other info from my browser.
I don't mind to rest my kde all together. no big deal. Please show me how

thanks

---

### Post by gimmy_bond on 2007-06-04
arnie,
inside the "Home" directory, I have my personal files named "meir". Scanning the files with Nautilus. I see that the "group" and "owner"  are labeled as 1000.  Permission is set to "drwxr-xr-x.

Hope it will help.

---

### Post by gimmy_bond on 2007-06-05
Deleted kdm file and reboot.
sudo apt-get remove kdm

Thanks Arnieboy for the initial guidance,

(For some reason I found problems with kde and kdm after using automatix2.). Maybe it is only me.

---

