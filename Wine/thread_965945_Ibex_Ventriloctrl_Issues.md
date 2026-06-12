---
title: "Ibex Ventriloctrl Issues"
date: 2008-10-31
forum: Wine
---

### Post by ubuser76 on 2008-10-31
I've been using Ubuntu for a while now and have had lots of success, so I tried upgrading to Intrepid and most everything has gone well except for one pesky problem. Ventriloctrl (v0.5) no longer seems to work under Ibex.

I have installed Wine and Ventrilo successfully and, after disabling pulseaudio, gotten Ventrilo to listen for the PTT key. The problem now is when I compile Ventriloctrl and run the command (./ventriloctrl /dev/input/event1) to get the keypress number Ventriloctrl does not appear to be listening/recognizing the keypress. It simply echos back the key key I pressed without returning the associated ID. Has anyone else run in to this? I think it might be related to how Ibex reads inputs now instead of from xorg.conf but I'm not sure how to fix this. 

Any help would be greatly appreciated. Thanks.

---

### Post by Limited on 2008-11-01
Yeah having similar issues, the key press finder part of it no longer seems to function. I've tried all the event devices just in-case it was something strange, but it appears it can't detect any key presses anymore :(

Same for vent as well, even if the window is activated I cannot get it to recognize I am pressing the relevant key during test mode. Also seem to be having issues with Ventrilo sound and Wine at the moment.

---

### Post by ubuser76 on 2008-11-03
Getting Ventrilo to listen for the keypress when focused is easy to remedy. I found the solution in another post, can't remember which thread though. The problem is pulseaudio prevents vent from listening for the keypress. The solution is to kill the pulseaudio process (sudo killall pulseaudio).

I also removed PA from the startup as well so I don't have to kill the process every time.

Unfortunately this doesn't fix the problem with Ventriloctrl not recognizing keypresses, as far as I know anyway. I still haven't been able to fix that problem.

---

### Post by Limited on 2008-11-03
I'm not sure if this has always been like this, but if im running another Wine application (in my case this is WoW), ventrilo will recognise my keypresses from there. So I don't need to run VentriloCtrl unless the active focussed program isnt being run through Wine again.

---

### Post by AryanAngel on 2008-12-29
Thanks a LOT for that last post Limited you've saved me a bit of searching for a bit. :)

---

