---
title: "Use wine to start a program, without a GUI?"
date: 2008-07-15
forum: Wine
---

### Post by djbon2112 on 2008-07-15
To put it simply, I have a fileserver on which I want to have uTorrent running. The problem, that under normal usage I want it to just start, and that includes uTorrent, without a user logging on. However, if I try simply to add "wine /path/to/utorrent" into a startup script, it fails because it can't create any windows, etc. Is there a way around this? I use the WebUI to manage it exclusively so I just need the application to start without a window manager basically.

---

### Post by dfreer on 2008-07-16
> **djbon2112 said:**
> To put it simply, I have a fileserver on which I want to have uTorrent running. The problem, that under normal usage I want it to just start, and that includes uTorrent, without a user logging on. However, if I try simply to add "wine /path/to/utorrent" into a startup script, it fails because it can't create any windows, etc. Is there a way around this? I use the WebUI to manage it exclusively so I just need the application to start without a window manager basically.

Hmmm... sounds like to me you need to either install a WM/Xorg or you need to use a GUI-less bittorrent client, there's quite a few good ones available. For example, for my headless server I actually use a bittorrent web client, torrentflux and torrentflux-b4rt.

---

