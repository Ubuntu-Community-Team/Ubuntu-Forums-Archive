---
title: "Ventrilo Audio"
date: 2008-07-03
forum: Wine
---

### Post by FLCL on 2008-07-03
I've installed ventrilo using the tut found here:
[http://appdb.winehq.org/appview.php?iVersionId=3936](http://appdb.winehq.org/appview.php?iVersionId=3936)

the problem im having is with the input, nobody can hear me, i can hear them fine. I can't set my mux, or line settings just blank in the drop downs, only mixer. VIA 8235 is the only option i can fill in for my mixer and then i get this error when i press ok: "VoiceCommMixerStart: Invalid voice mux selection. (-1)"

Does anyone know how to fix this? =(

---

### Post by bananamunch on 2008-09-20
Sorry i do not have an answer for you, but i have noticed it has been a few months since you posted this and haven't received a response. I, too, am having this same problem and this is the only site i have been able to find that has any hope of an answer. Any help would be appreciated. thanx

---

### Post by nzadLithium on 2008-10-11
I'm not sure if you guys are still looking for an answer but here it is anyway.

Open vent.
Goto Setup
Make sure your in the voice tab
On right hand side roughly centre is a group of settings labelled "Hardware input mixer (Optional)"
Set mixer to none, clear all the other settings (in that box).

This appears to have worked for me although I haven't tested that people can still hear me :p But i used the test function on vent and it seems its working.

If any of you guys want to use push to talk in normal linux programs (not just ones in wine), there is a key hack available, i think it was mentioned on the wine website, its called ventriloctrl. Theres a post about getting it going here: [http://ubuntuforums.org/showpost.php?p=2662867&postcount=83](http://ubuntuforums.org/showpost.php?p=2662867&postcount=83)
(wish i had've seen this thread while I was trying to make it go, took me ages to figure it out :S ).

One thing the person in that thread seems to have missed, to find out what device your keyboard is (without guess and check) do: cat /proc/bus/input/devices (in a terminal). It tells you in there, look for your keyboard, and its "handlers" line. It will say event(a number here) that'll be the event number you want in that thread hopefully :D

---

### Post by gurra94 on 2010-03-14
I got the same problem and error message but this didnt work for me
I got all other options correct, pls help

---

### Post by cb951303 on 2010-03-14
maybe this would help [http://www.mangler.org/](http://www.mangler.org/)

---

### Post by Tweak42 on 2010-03-16
THANK YOU!

I've spent the hours ](*,) trying to get vent running on wine not knowing there's was compatible linux client. It's a shame googling "ventrilo linux" should bring mangler as the top hit, which is why I missed it. :-(

> **cb951303 said:**
> maybe this would help [http://www.mangler.org/](http://www.mangler.org/)

---

