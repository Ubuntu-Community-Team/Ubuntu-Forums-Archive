---
title: "nvidia-xconfig"
date: 2008-11-25
forum: x86 64-bit Users
---

### Post by jus71n742 on 2008-11-25
I need to figure out how to force nvidia-xconfig to save so that it will restart x and use the second monitor and later 3rd....It will say that Unable to remove old X config backup file '/etc/X11/xorg.conf.backup'.

any suggestions?

---

### Post by vandorjw on 2008-11-25
I think I know how to help you.
But first I want to know what version of Ubuntu you have because in 8.10, they changed the way X-server worked.

Because of your error, I will assume that you have 8.04.1, because that is what I had, when I had that error.

I cannot remember exactly where the xorg.conf file is (or if that was even the correct name)

I remember it was something like this
/etc/X11/xorg.conf 

Anyways, open this file, and make a back-up.

(save it under a different name in your home directory?) [save as]


Then, there is a way to display the code that the "Nvidia x Server Settings" application wants overwrite to that file that you just backed up.

basically, when someone tells you the file that you are looking for (I know for sure it ended in .config, and in the file path there was X11),

go like this in the terminal.

sudo gedit /etc/X11/xorg.conf

then paste the nvidia code there and save the file.

hit, "alt-cntr- backspace" to restart.

hope that was useful, and if that made no sense to you, just say so and i'll try and explain better.

Cheers - cc7

---

### Post by ericreed on 2008-11-26
It sounds like it's a permissions problem.  You aren't allowed to write to the root directory without root privileges.  Launch the nvidia utilities from the terminal with 'sudo'.

sudo nvidia-xconfig

sudo nvidia-settings

---

### Post by bodhi.zazen on 2008-11-26
> **ericreed said:**
> It sounds like it's a permissions problem.  You aren't allowed to write to the root directory without root privileges.  Launch the nvidia utilities from the terminal with 'sudo'.

sudo nvidia-xconfig

sudo nvidia-settings

Please use sudo for terminal apps

```
sudo nvidia-xconfig
```

And gksu for X apps

```
gksu nvidia-settings
```

When saving your settings, un-tic (remove the check mark) from the "merge settings" dialog box just before you save.

---

### Post by inobe on 2008-11-26
> **bodhi.zazen said:**
> Please use sudo for terminal apps

```
sudo nvidia-xconfig
```

And gksu for X apps

```
gksu nvidia-settings
```

When saving your settings, un-tic (remove the check mark) from the "merge settings" dialog box just before you save.

please include "why" its better to use **gksu**

---

### Post by TimothyLuke on 2008-11-26
Duplicate post error

---

### Post by TimothyLuke on 2008-11-26
Laymans answer:

sudo is a command line app for running a command with elevated priviledges.

gksu  (I thought it was gksudo but cant check as I'm at work on a doze pc) allows the user to run a Gnome app/X-Windows app with elevated priviledges within the users X session.  I use it to run gedit for editing stuff in /etc as I prefer it over vim or emacs and I find that method easier to copy/paste into.  The app also inherits the current running X config which may make the execution of nvidia-settings more useful.

---

### Post by bodhi.zazen on 2008-11-26
gkksu is a symbolic link to gksudo and is easier to type :twisted:

For additional information please see :

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by jus71n742 on 2008-11-27
WOOOW I feel like an idiot....I remember accessing everything through a terminal last time....thanks for pointing out the obvious mistake...lol got to pay closer attention to detail.

---

### Post by inobe on 2008-11-27
> **bodhi.zazen said:**
> gkksu is a symbolic link to gksudo and is easier to type :twisted:

For additional information please see :

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

figured if one says not to do something' that person should offer an explanation with regards to the topic starter.

---

### Post by caladan1810 on 2008-11-28
> **ericreed said:**
> It sounds like it's a permissions problem.  You aren't allowed to write to the root directory without root privileges.  Launch the nvidia utilities from the terminal with 'sudo'.

sudo nvidia-xconfig

sudo nvidia-settings


thank you so much I was racking my brains wondering why it wouldn't save my settings. You have restored my sanity!

Thank you

---

