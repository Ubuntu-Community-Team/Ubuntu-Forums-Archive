---
title: "Trying Ubuntu coming from FC4 - a question"
date: 2005-07-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by linuxted on 2005-07-04
Well I bit the bullet and changed my computer from Fedora Core 4 (AMD_64) to Ubuntu 5.04 AMD_64.  It is different but with a little bit of reading (mostly on these forums and the user's guide) I am fairly impressed.

Here's my first foray into asking questions in this venue:

I was able to add k3b via apt-get on the command line but it doesn't show up on the list of applications on the gnome pulldown.  What do I have to do to make this happen?  (when I do a which k3b I get /usr/bin/k3b)


Thanks,
linuxted

---

### Post by tread on 2005-07-04
Install smeg .. thats a menu editor. Then you can add whatever you want to the menu.

Before that though, try a 
killall -9 gnome-panel 

That should restart gnome-panel, loading any new launchers if available.

Oops: this is AMD64. I don't know if smeg has been backported to amd64 .. I don't even know if that matters.

---

### Post by linuxted on 2005-07-04
[QUOTE=tread]Install smeg .. thats a menu editor. Then you can add whatever you want to the menu.

Before that though, try a 
killall -9 gnome-panel 

That should restart gnome-panel, loading any new launchers if available.

Oops: this is AMD64. I don't know if smeg has been backported to amd64 .. I don't even know if that matters.[/QUOTE]
 Doesn't look like smeg is available :(

Thanks for the suggestion though

---

### Post by DancingSun on 2005-07-05
[QUOTE=linuxted]Doesn't look like smeg is available :(

Thanks for the suggestion though[/QUOTE]

Smeg is available for AMD64!  I have it installed!  Directions are available on the [Unofficial Ubuntu 5.04 Starter Guide for AMD64](http://amd64.ubuntuguide.org/#menu-editor).

I don't know if the program is 64-bit or not, but it works!

---

### Post by Big Venus on 2005-07-05
[QUOTE=linuxted]Well I bit the bullet and changed my computer from Fedora Core 4 (AMD_64) to Ubuntu 5.04 AMD_64.  It is different but with a little bit of reading (mostly on these forums and the user's guide) I am fairly impressed.

Here's my first foray into asking questions in this venue:

I was able to add k3b via apt-get on the command line but it doesn't show up on the list of applications on the gnome pulldown.  What do I have to do to make this happen?  (when I do a which k3b I get /usr/bin/k3b)


Thanks,
linuxted[/QUOTE]
if the killall gnome-panel command didn't work then that is because you need to be using KDE desktop...

And look through the different type of forums for support and there is one for smeg and it contains a script in it that would help as well.

---

### Post by DancingSun on 2005-07-05
[QUOTE=Big Venus]if the killall gnome-panel command didn't work then that is because you need to be using KDE desktop...[/QUOTE]

You meant GNOME Desktop right?  I have the GNOME Desktop and "killall gnome-panel" works fine....

---

### Post by joekr on 2005-07-05
```
ls /usr/share/applications
```

Look for k3b.desktop or similar...

```
cd /usr/share/applications
sudo gedit k3b.desktop
```
Open up the file and paste it's contents into here... It'll be a synch to fix that up... unfortunatly I don't have kde or k3b installed so I'm not sure as to their paths.

---

### Post by Big Venus on 2005-07-05
[QUOTE=DancingSun]You meant GNOME Desktop right?  I have the GNOME Desktop and "killall gnome-panel" works fine....[/QUOTE]
Killall while you are in GNOME, yes. But somethings don't work in GNOME so well that are designed for KDE so it would just be their in KDE.

---

### Post by Jet2k5 on 2005-07-06
Great guide, have been waiting quite long for this.

For the updates you should include some of the stuff [here](http://digital-conquest.ath.cx/wiki/index.php/Ubuntu#How_to_install_Cedega_on_AMD64) 

That's how to install cedega in 64-bit.  Also I didn't see that on the guide just link to transgaming.com or w/e.  Also how to set up a chroot environment.  Which to tell you the truth looks more freaking complicated than I thought.

*EDIT* Posted this is the wrong topic.  Can a mod move this post to the " ubuntu 64-bit guide " somewhere in here?

---

