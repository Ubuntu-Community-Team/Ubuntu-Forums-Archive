---
title: "Compiz and Wine"
date: 2008-05-08
forum: Wine
---

### Post by ant2ne on 2008-05-08
I'm suspecting wine programs are crashing due to compiz. Has anyone else experienced this? Any advice?

---

### Post by pissedoffdude on 2008-05-08
Really not too sure if there's a fix for it, but your best bet is to disable compiz before running windows applications.

---

### Post by cogadh on 2008-05-08
Wine and Compiz generally don't get along well together. From the [Wine FAQ](http://wiki.winehq.org/FAQ):
> [SIZE="4"][B]I'm using Beryl/XGL/Compiz and get poor performance/odd messages/broken applications
[/B][/SIZE]
Using composite display managers in Linux tends to cripple OpenGL performance or break OpenGL entirely which is why we recommend that you disable them and remove composite from XOrg entirely before trying to use Wine. If you are using one and experiencing slow performance then DO NOT FILE BUGS as this is not a Wine bug. Just because TuxRacer runs fine doesn't mean it is Wine's fault, Windows games normally require a little more umph than basic Linux native games. Also to make sure, run glxinfo and make sure that it says "Direct Rendering : Yes".

---

