---
title: "Multiple issues: From Blank Tan Screen to Distorted Desktop"
date: 2009-04-26
forum: x86 64-bit Users
---

### Post by cindyrella on 2009-04-26
A few weeks ago, I accidentally installed several items (which I can no longer remember) using Synaptic Package Manager. My computer shut down by itself. When I rebooted, the desktop items (menu bars and background color) was in its prepatory loading stage, but it got stuck on a blank, beige/tan screen.

The blank screen re-appeared after several attempts at rebooting.

After a few searches, I tried going into the console, logged in with my username and password, and reconfigured my x with

```
sudo dpkg-reconfigure xserver-xorg
```

After booting up again, I see that the login and desktop screen's dimensions are altered (compressed width). Additionally, it won't connect to my wireless network and I get an error when I try to access my external hard drive. It doesn't recognize my burner (this was always a problem). Now I can't back anything up.

Also, I tried logging into a KDE session, but have the same problems, ie, can't access wireless or external devices -- although I was able to access KDE's desktop when I got the blank screen in gnome.

Any next-step suggestions?

TIA,
Cindy

---

