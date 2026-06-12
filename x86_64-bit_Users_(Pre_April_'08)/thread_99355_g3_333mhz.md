---
title: "g3 333mhz"
date: 2005-12-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by iomicifikko on 2005-12-05
hi all, i just installed ubuntu on an old imac g3 333mhz, install process was fine but when i start an ubuntu session, gnome doesnt seem to load. i'm not sure about what i say anyway here are a few things about my situation:

- graphical session loads (where it asks for username and password)
- if i use the default session, just the default background appears (no bars)
- if i start a session with an xterm console window,  and then i try to load for example firefox, both xterm and firefox appears but without borders, i mean without the graphical gtk interface on the edges of the windows

any ideas?

thanks all!

---

### Post by kalin on 2005-12-05
I've seen this happen on another old iMac. At the time I noticed it's clock was reset (I guess staying disconnected from power sources has simply drained the internal battery), so I changed the date using the terminal (you can reach a terminal by pressing Ctrl+F1 at the login screen, Ctrl+F7 to go back).

Type "date --help" to see the options of the "date" command. E.g. setting the date/time to 5th Dec 2005, 19:10 would be something like this:

```

sudo date 120520051910

```

Then I did reboot, if I remember correctly, just to make sure all file stamps are correct.

You can reboot from the terminal using "reboot":

```

sudo reboot

```

I'm still wondering how exactly would the wrong date/time cause such behaviour, but fixing it helped in my case, and it didn't happen anymore. Hope it works out for you too.

---

### Post by Ptero-4 on 2005-12-05
IIRC, the wrong clock setting only affects gnome itself. That explains why when choosing a xterm session xterm and whatever you launch trough it appears fine. Now the reason they appear borderless is b/c the window borders are handled by a program called a windowmanager. Gnome uses metacity as it's windowmanager, but there are lots of other windowmanagers. the xterm session don't launch a windowmanager and that's why program windows appear borderless. to fix that you can type metacity & as soon as the xterm session starts and b4 launching anything else, that will start metacity up giving you the "gtk" border appearance you're used to.

---

### Post by iomicifikko on 2005-12-06
thanks both of u guyz, i will check your suggestions at home, and ill let u nkow the results.  thanks again!. bye

---

