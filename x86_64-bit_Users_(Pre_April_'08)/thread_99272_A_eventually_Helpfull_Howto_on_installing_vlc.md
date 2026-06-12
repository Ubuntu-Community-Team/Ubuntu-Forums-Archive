---
title: "A eventually Helpfull Howto on installing vlc"
date: 2005-12-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by sousuke1987 on 2005-12-05
[B][I]Agreement:

This "How To" install vlc in ubuntu has been created by Sander Bosch. I cannot guartantee that this installation will be 100% safe. USE AT OWN RISK. Though it may have worked with my Slotloading G3 IMAC, I cannot guarantee full functionality or compatibility with other PPC  systems of any kind, including mine. Hereby I cannot being held responsible for any kind of hardware damage or data loss or consequences of the stress it made by trying to install!

Sander Bosch

a linux noob with a stong will[/I][/B]


Installing vlc
-> add applications (synoptic package manager)
-> file
-> settings
-> repositories
-> add repositories
-> custom

Type in the apt line (without quotes): " deb [http://ftp.debian.org](http://ftp.debian.org) sarge main"

-> ok
->place v in the boxes in front of the universe repositrories which are community maintained and in front of the debian repository.

There are now eventually two ways to install vlc:

1 : ->synoptic package manager
-> audio/video
-> more audio/video
-> select vlc for gnome (if you are using gnome, otherwise you can use +gtk for kde, but I am not shure)
The installation now will be fully automatical

2: ->press alt+f2
->type(withou quotes) xterm
->type behind the -$ or #(always without quotes from now on until said differntly ): sudo apt-get install vlc
The install process should finish automatically to.

Now open vlc and enjoy! :D

If error? Proceed next steps

Open a terminal (->alt+f2  -> xterm )
-$ vlc -vvv --color
open a video and see if the following lines are red or yellow.
If not? please care if the output device/driver in vlc is the same as in ubuntu (mostly X11 video will work)
If yes, open a terminal
-$ sudo apt-get build-dep vlc
Warning! an 200 mb of additional harddrivespace is needed. A fast internetconnection would come in very handy!
After the install, reboot.
Enjoy VLC :D


Note: It may be wise to restaure the repositories to system defaults!

---

### Post by ssam on 2005-12-05
is there a reason not to use the version in the ubuntu universe repo
[http://packages.ubuntu.com/breezy/graphics/vlc](http://packages.ubuntu.com/breezy/graphics/vlc)

---

### Post by muchmusic on 2005-12-05
For new world machines the output of video that works safely is XWindows (X11/XShm/Xv) which can be selected in VLC as well as the Multimedia Systems Selector (VLC is not aware of that setting).

I do not know of a reason to ignore the VLC in Ubuntu Universe repositories.

It is a good writeup and the process does work, though.

---

