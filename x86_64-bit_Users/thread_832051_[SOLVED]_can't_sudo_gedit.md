---
title: "[SOLVED] can't sudo gedit"
date: 2008-06-17
forum: x86 64-bit Users
---

### Post by mistlur1 on 2008-06-17
Hi

My system has been behaving strange lately and there are several unresolved issued that i'm trying to figure out. But to do so it would help to be able to run gedit as root (yes i can do sudo nano, but I want to fix this issue). It seems to be the only app that I can't run with sudo.

when I run ```
sudo gedit
``` nothing happens. The same with gksudo.
No process is killed by ```
sudo killall gedit
``` so it's not running in the backgound. If I let the "sudo gedit" command sit for a few minutes the error ```
 The application 'gedit' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.

``` appears.
I would be grateful for any help with this problem, don't know where to start. I've googled around awhile, but similar instances by other users seem all unresolved...

/mistlur

---

### Post by aysiu on 2008-06-17
I ran your error message through [this Google search](http://www.google.com/search?hl=en&q=The+application+lost+its+connection+to+the+display+%3A0.0%3B+most+likely+the+X+server+was+shut+down+or+you+killed%2Fdestroyed+the+application.&btnG=Google+Search) (without the *'gedit'* part) and found all sorts of weird situations (Fedora, Mandriva, Nvidia, i810, *gnome-panel*, *iceweasel*). Didn't find too many solutions in the first few links, though.

You may want to explore further yourself, but it seems it has something to do with the /etc/X11/xorg.conf file.

---

### Post by nsindian on 2008-06-17
> **aysiu said:**
> I ran your error message through [this Google search](http://www.google.com/search?hl=en&q=The+application+lost+its+connection+to+the+display+%3A0.0%3B+most+likely+the+X+server+was+shut+down+or+you+killed%2Fdestroyed+the+application.&btnG=Google+Search) (without the *'gedit'* part) and found all sorts of weird situations (Fedora, Mandriva, Nvidia, i810, *gnome-panel*, *iceweasel*). Didn't find too many solutions in the first few links, though.

You may want to explore further yourself, but it seems it has something to do with the /etc/X11/xorg.conf file.
You may want to try and insert the name of a file you want to edit after the "gedit" command. e.g. sudo gedit smb.conf

---

### Post by aysiu on 2008-06-17
> **nsindian said:**
> You may want to try and insert the name of a file you want to edit after the "gedit" command. e.g. sudo gedit smb.conf
Except that it really should be ```
gksudo gedit smb.conf
``` not that it makes a difference in this particular case, since the OP can't do either.

---

### Post by mistlur1 on 2008-06-17
Thanks for the replies!

By chance, I found the source, but I'm dumbfounded.
Since I move to a new apartment soon I've got no internet connection except my SE k800i which I use to stay connected. Apparently when I have it plugged in i cant 'sudo gedit', but if I disconnect it i can...

It's quite bizarre really.

/mistlur

---

