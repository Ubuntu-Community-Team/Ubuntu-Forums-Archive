---
title: "Compiz Problems"
date: 2006-09-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by coldsoul on 2006-09-11
Hi all!
Two days ago i installed xgl/compiz/cgwd on my dapper amd64 machine. after 2 days struggling with it it seems to work now. but the strange thing is: i still don't have title bars and minimize/maximise etc. buttons on my windows. Also i can't switch themes with cgwd. can someone give tipps or so? Thanks!

---

### Post by sethmahoney on 2006-09-11
What method did you use to install it?

---

### Post by coldsoul on 2006-09-11
I installed all of it with synapsis. It's a little messy i tryed different ways of installing it since none seemed to work well.. but i got now all effects & stuff but still no title bars. i don't know what to do..

---

### Post by sethmahoney on 2006-09-11
> **coldsoul said:**
> I installed all of it with synapsis. It's a little messy i tryed different ways of installing it since none seemed to work well.. but i got now all effects & stuff but still no title bars. i don't know what to do..

What was the last method you used (I'm assuming you followed a guide somewhere)?

---

### Post by hanzomon4 on 2006-09-11
Install the following, and follow the directions.. It should get you setup 

1.compiz
2.compiz-core
3.compiz-plugins
4.compiz-manager
5.csm
6.cgwd

To start compiz issue this command, you can also add it to your startup session. 
```
compiz-manager
```
To edit your settings click on the compiz-manager icon , which should be in your task bar, and select compiz-settings-manager.
If you find that your settings are not being saved issue this command. 
```
chmod 777 ~/.compiz
```

---

### Post by coldsoul on 2006-09-11
i installed all those things... still no frames. can't find such options in csm.. all things work except title bars and such.. pretty confusing...

---

### Post by city-17 on 2006-09-11
I recently install Xgl/Compiz succesfully on Dapper 64 bits, i followed this guides: [http://help.ubuntu.com/community/CompositeManager/Xgl]("http://help.ubuntu.com/community/CompositeManager/Xgl")
[http://help.ubuntu.com/community/CompositeManager/InstallingCompiz]("http://help.ubuntu.com/community/CompositeManager/InstallingCompiz")

The extra step for 64 bit users is adding this special repositories
```
deb http://ubuntu.systemadministrator.org dapper eyecandy
deb-src http://ubuntu.systemadministrator.org dapper eyecandy
```
Then you have to get the key for the repositories
```
wget http://ubuntu.systemadministrator.org/2F306651.gpg -O- | sudo apt-key add -
sudo apt-get update
```
This extra repositories ensures that you are using the latest Xgl/Compiz stuff for Dapper 64 bits. That worked for me using the script method to add a Xgl session.

---

### Post by hanzomon4 on 2006-09-11
Opps!Didn't know I was responding to 64bit users... My bad

---

### Post by coldsoul on 2006-09-12
[http://help.ubuntu.com/community/CompositeManager/Xgl]("http://help.ubuntu.com/community/CompositeManager/Xgl")
[http://help.ubuntu.com/community/CompositeManager/InstallingCompiz]("http://help.ubuntu.com/community/CompositeManager/InstallingCompiz")

I did exactly the same.. my repositories include this one also.. today i got even updates on everything but still no title bars & stuff und mit cgwd kann ich die themen nicht ändern...

---

### Post by John.Michael.Kane on 2006-09-12
This guide may help you.
[Xgl and Compiz for Dapper]("http://www.tectonic.co.za/view.php?src=rss&id=1153")

---

### Post by coldsoul on 2006-09-12
no... it didn't help. i did all but still the same

---

### Post by kislo_metal on 2006-09-13
I had same problems..
Did you find what to do with this?
and what repositories do you use during compiz-manager install, becose i can`t find it?
My repositories ^:

deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main
deb-src [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) dapper main
deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) dapper main
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main main-amd64
deb [http://ubuntu.systemadministrator.org](http://ubuntu.systemadministrator.org) dapper eyecandy
deb-src [http://ubuntu.systemadministrator.org](http://ubuntu.systemadministrator.org) dapper eyecandy
deb [http://koti.mbnet.fi/xopher/](http://koti.mbnet.fi/xopher/) dapper main-amd64

---

### Post by coldsoul on 2006-09-13
I use the same repositories but i have installed compiz-manager after i visited the [http://koti.mbnet.fi/xopher/](http://koti.mbnet.fi/xopher/) site and downloadet from there the debian package. But even after the update today i still got no title bars and stuff. and when i try to play a video file everything crashes and i am being thrown to login screen...

---

### Post by kislo_metal on 2006-09-13
do you gat some errors from compiz-manager log?(i run it in terminal window)
i had get such errors^
** (cgwd:5295): WARNING **: Cannot open pixmap: unabove
Window manager warning: Fatal IO error 104 (Connection reset by peer) on display ':1.0'.
compiz: No GLXFBConfig for depth 32
.....
X connection to :1.0 broken (explicit kill or server shutdown).
compiz: No GLXFBConfig for depth 32
.......
*** glibc detected *** free(): invalid pointer: 0x00000000005a53b8 ***

** (compiz-manager:5244): WARNING **: Compiz caught deadly signal 6

** (compiz-manager:5244): WARNING **: Couldn't find a Selection Owner, perhaps no WM running? Otherwise, manually kill your wm, and report the bug to the developers, it doesn't follow the standards.
Window manager warning: Lost connection to the display ':1.0';
most likely the X server was shut down or you killed/destroyed
the window manager.
compiz: No GLXFBConfig for depth 32
------------------------------------------------------
during this i try to change to cgwd Theme and reloa window manadger/decorator
any ideas?

---

### Post by coldsoul on 2006-09-13
i get only this one:compiz: No GLXFBConfig for depth 32 and no no ideas...

---

### Post by kislo_metal on 2006-09-13
And when you run compiz theme manager you can`t make any change to your current theme? which was left from standart gnome theme, aren't you?
do you try another way to install compiz ...not as session?
---](*,)

---

### Post by kislo_metal on 2006-09-13
Had you try to install compiz not just like session&
Try to use automatix//

---

### Post by coldsoul on 2006-09-13
i run now compiz not as a session. i start it after logging in with the compiz manager. but i still don't have any titlebars

---

### Post by brendo on 2006-09-13
I have installed all of the compiz packages and have glx running on my computer correctly. However, when I try to start compiz with

```

compiz-start

```

I read the following from nohup.out:

```

The application 'cgwd' lost its connection to the display :1.0; most likely the X server was shut down or you killed/destroyed the application.

```

and if I start the compiz-manager, I can try to select compiz as the window manager, but when I select it the windows disappear and reappear, but metacity is still selected and running.

How can I fix this? I have been combing through the forums for hours and I can't find the answer...](*,)

---

### Post by kislo_metal on 2006-09-13
I try to run compiz --replace $1 gconf 
it mast replase gnome|| compiz config....
dosen`t help...
i will try to find somfing else...
besides, i had hard problems with fglrx- such as driver crash after xserver restart and strange grind on display when terminal run, and some other application... but it is not the problem of what we ty to find..

---

### Post by hanzomon4 on 2006-09-14
I found something on the compiz forums, it seems to the problem you folks have: [No title bars ]("http://www.compiz.net/topic-4375-title-bars-with-ati-x800")

---

### Post by kislo_metal on 2006-09-14
had it help you?

---

### Post by hanzomon4 on 2006-09-14
No, I don't have this problem. Also the latest updates should have the patch, updates just released today.

---

### Post by DomaZ on 2006-09-14
I have very good news for you :)

check 5 and 15 posts at that address [http://www.compiz.net/topic-4375-title-bars-with-ati-x800](http://www.compiz.net/topic-4375-title-bars-with-ati-x800)


Good luck

---

### Post by hanzomon4 on 2006-09-14
check this out


[quote=QuinnStorm]0.50/0.25 (core/plugins) will have the patch...if too many bugs come from it I'll revert in 51/26[/quote]
[quote=domaz]Hello agen. Quinn, I just wanted to notice that everything
is working so perfect atm, i was paching compiz like 4 months,
so its wery avesome when you type command apt-get install...
and everything works.
   I am running Acer Aspire 5024WlMi  amd64  ati x700 mobility,
fglrx 8.28.8, on Edgy... without any problems...

   I still have some problems with gnome, gnome-panel...etc..
if i will solve that...will be awesome.....

Thanks again quinn... see you later..[/quote]

---

