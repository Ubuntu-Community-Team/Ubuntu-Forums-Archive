---
title: "Issues with WINE after Ubuntu update"
date: 2012-06-29
forum: Wine
---

### Post by Dadof4 on 2012-06-29
Hi everyone! I'm using Play On Linux/WINE to run my steam games. Everything was running fine after I upgraded to Ubuntu 12.04 but a short time ago there was an Ubuntu update released and now I cannot run any of of my Steam based games. The games start but the audio is awful. I know this is an issue with Pulse Audio and when I disable it from the terminal prior to running a game everything is fine. 

 I found the thread in the WINE Wiki but from reading it it sounds like things change with different Ubuntu releases and they don't have anything for 12.04. My question is, how do I disable pulse audio from being the default sound driver in 12.04 when I start a Steam Based game?

Any help is appreciated!

---

### Post by Dlambert on 2012-06-30
If you are using Ubuntu +1, there are usually regressions. If  in POL(playonlinux)  select Configure then hit the WINE box, the go to audio. If on non POL WINE go to terminal and type ```
winecfg
``` Hopefully that is what you are looking for.

---

### Post by Dadof4 on 2012-06-30
What do I don once I get there? I cannot find anywhere to disable it.

---

