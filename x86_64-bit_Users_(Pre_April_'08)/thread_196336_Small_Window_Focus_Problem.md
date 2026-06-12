---
title: "Small Window Focus Problem"
date: 2006-06-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by Lothlómendil on 2006-06-14
Firstly, I should state that I'm not the most advanced Linux user, but I can follow directions pretty well ;) I also searched for other reports of this problem but didn't find any.

My problem isn't very major but it is pretty annoying. Since I updated to Dapper last week or so I've been having problems when trying to change focus to another window. I click on a window other than the one currently in focus, because I want to look at it, and it won't come back into focus. Clicking repeatedly on the unfocused window to get it back into focus doesn't seem to do the trick, I have to click on a different window then re-click on the one I want to see before it will come into focus. Sometimes it takes several tries. It doesn't matter which programs I am trying to switch between, it does it to them all. It doesn't seem to be a mouse problem because the problems only happen when changing windows, not while browsing the internet or anything else that requires lots of clicking.

Does anyone have an idea about what might be causing this, and / or how to fix it? It's not urgent, but it is semi-frequent and getting old; focusing on a new window shouldn't be complicated. Some minor computer specs are in my signature, if you need more, ask.

---

### Post by henriquemaia on 2006-06-14
I have read that on some upgrades the older configurations don't work so well. 

Run **gconf-editor **and go to **apps** > **metacity** > **general** and play with the various configurations there to see if your reported behaviour changes.

---

### Post by Lothlómendil on 2006-06-14
Thank you for the assistance :)

I have looked around in **apps > metacity > general** but all of the related options seem to be set correctly. Below are some of the options and their values:

**Raise on click** - true (checked)
**Focus Mode** - click
**Focus New Windows** - smart
**Application Based** - false (unchecked)

Does anyone have any more tips or suggestions? I should maybe also note that all of these should be at their default settings, I've never messed with these options before or after upgrading.

[edit]
I realized I may be miswording a little. The window actually does seem to "come into focus" but it doesn't raise to where I can see it. If I have two windows open, one behind the other and out of sight, when I click on the back window to look at it the color of the title bars do change like they should when changing focus, but the back window doesn't raise from behind the forewindow so that I can see it... if that isn't too confusing...

---

### Post by henriquemaia on 2006-06-14
[quote=Lothlómendil]Thank you for the assistance :)

I have looked around in **apps > metacity > general** but all of the related options seem to be set correctly. Below are some of the options and their values:

**Raise on click** - true (checked)
**Focus Mode** - click
**Focus New Windows** - smart
**Application Based** - false (unchecked)

Does anyone have anymore tips or suggestions? I should maybe also note that all of these should be at their default settings, I've never messed with these options before or after upgrading.

[edit]
I realized I may be miswording a little. The window actually does seem to "come into focus" but it doesn't raise to where I can see it. If I have two windows open, one behind the other and out of sight, when I click on the back window to look at it the color of the title bars do change like they should when changing focus, but the back window doesn't raise from behind the forewindow so that I can see it... if that isn't too confusing...[/quote] 
As pointed out here on this post:

[http://ubuntuforums.org/showpost.php?p=1046861&postcount=24]("http://ubuntuforums.org/showpost.php?p=1046861&postcount=24")

try this command, to reset the metacity options on gconf-editor:

```
gconftool --recursive-unset /apps/metacity && killall metacity
``` 
or you can try to set up a new user and login as this new user to see if your configurations are messed up (I found a error on mine through the advice on this post:

[http://ubuntuforums.org/showpost.php?p=1044634&postcount=17]("http://ubuntuforums.org/showpost.php?p=1044634&postcount=17")

---

### Post by Lothlómendil on 2006-06-16
I have entered the command you provided, but alas, it hasn't corrected the problem. Though it does appear to possibly have lessened how often occurs, if that makes any sense. (I could be imagining it. :p)

I also appreciate the second suggestion, but I feel that creating a second user and investigating options that way is a bit impractical. I prefer not to use the second suggestion, I find too much unneeded messing to be not worth the time and effort.

A friend and I are still investigating the problem, but more suggestions would be very helpful, thank you. :)

---

### Post by steabert on 2006-06-16
can't you just delete your gconf dirs in your home?

---

### Post by Lothlómendil on 2006-06-16
I wouldn't think that would be the solution, as I would get rid of all of my settings done through GConf. I don't find that very desirable.

---

### Post by steabert on 2006-06-16
you can backup them and then try putting it back piece by piece.
anyway, it's worth a try, if it works, then i guess reconfiguring is annoying, but
will solve it.
if it doesn't help, you can just copy the whole stuff back.

---

### Post by henriquemaia on 2006-06-17
[quote=Lothlómendil]I have entered the command you provided, but alas, it hasn't corrected the problem. Though it does appear to possibly have lessened how often occurs, if that makes any sense. (I could be imagining it. :p)

I also appreciate the second suggestion, but I feel that creating a second user and investigating options that way is a bit impractical. I prefer not to use the second suggestion, I find too much unneeded messing to be not worth the time and effort.

A friend and I are still investigating the problem, but more suggestions would be very helpful, thank you. :)[/quote]

You can still find the second solution to be unpractical, but using it is as simple as:

Going to **System** > **Administration **> **Users and Groups** and create a new user.
Close that **Users and Groups** window, pressing the **Quit **button, choosing the **Switch User** option and login as your new user. It won't even log you out of your current session. After you're finished with the test, log out the new user session and you'll be taken back to your current session. Then you just have to go to **Users and Groups** and delete that new user newly created.

---

### Post by loko on 2006-08-13
i can confirm this problem, i have the same problem since a few days. i  have an x86-processor so i assume that it is not an architecture-related problem.

i don't know if it is related to the problem but i use a bluetooth-mouse, but if i am right there was no bluetooth-related updates the last days.

if i use the touchpad of the laptop, this problem does not happen.

but i have to say that sometimes the mouse works after boot-up the system for some time


edit:

on 06.08.2006 there was these updates:
```
Commit Log for Sun Aug  6 12:17:43 2006


Die folgenden Pakete wurden aktualisiert:
app-install-data-commercial (4) to 5
gstreamer0.10-alsa (0.10.7-0ubuntu4) to 0.10.7-0ubuntu5
gstreamer0.10-gnomevfs (0.10.7-0ubuntu4) to 0.10.7-0ubuntu5
gstreamer0.10-plugins-base (0.10.7-0ubuntu4) to 0.10.7-0ubuntu5
gstreamer0.10-plugins-base-apps (0.10.7-0ubuntu4) to 0.10.7-0ubuntu5
gstreamer0.10-x (0.10.7-0ubuntu4) to 0.10.7-0ubuntu5
libgstreamer-plugins-base0.10-0 (0.10.7-0ubuntu4) to 0.10.7-0ubuntu5
libgstreamer-plugins-base0.10-dev (0.10.7-0ubuntu4) to 0.10.7-0ubuntu5
libpango1.0-0 (1.12.3-0ubuntu1) to 1.12.3-0ubuntu3
libpango1.0-common (1.12.3-0ubuntu1) to 1.12.3-0ubuntu3
libpango1.0-dev (1.12.3-0ubuntu1) to 1.12.3-0ubuntu3
ubuntu-base (0.119) to 0.120
ubuntu-desktop (0.119) to 0.120
ubuntu-minimal (0.119) to 0.120
ubuntu-standard (0.119) to 0.120


```

and 

```
Commit Log for Thu Aug  3 10:57:51 2006


Die folgenden Pakete wurden aktualisiert:
eog (2.14.2-0ubuntu1) to 2.14.3-0ubuntu1
file-roller (2.14.3-0ubuntu1) to 2.14.4-0ubuntu1
firefox (1.5.dfsg+1.5.0.5-0ubuntu6.06) to 1.5.dfsg+1.5.0.5-0ubuntu6.06.1
firefox-gnome-support (1.5.dfsg+1.5.0.5-0ubuntu6.06) to 1.5.dfsg+1.5.0.5-0ubuntu6.06.1
gdm (2.14.9-0ubuntu1) to 2.14.10-0ubuntu1
gedit (2.14.3-0ubuntu1) to 2.14.4-0ubuntu1
gedit-common (2.14.3-0ubuntu1) to 2.14.4-0ubuntu1
gnome-about (2.14.2-0ubuntu1) to 2.14.3-0ubuntu1
gnome-accessibility-themes (2.14.2-0ubuntu1) to 2.14.3-0ubuntu1
gnome-applets (2.14.2-0ubuntu1) to 2.14.3-0ubuntu1
gnome-applets-data (2.14.2-0ubuntu1) to 2.14.3-0ubuntu1
gnome-desktop-data (2.14.2-0ubuntu1) to 2.14.3-0ubuntu1
gnome-games (1:2.14.2.1-0ubuntu1) to 1:2.14.3-0ubuntu1
gnome-games-data (1:2.14.2.1-0ubuntu1) to 1:2.14.3-0ubuntu1
gnome-menus (2.14.0-0ubuntu1) to 2.14.3-0ubuntu1
gnome-panel (2.14.2-0ubuntu1) to 2.14.3-0ubuntu1
gnome-panel-data (2.14.2-0ubuntu1) to 2.14.3-0ubuntu1
gnome-screensaver (2.14.2-0ubuntu1) to 2.14.3-0ubuntu1
gnome-session (2.14.2-0ubuntu1) to 2.14.3-0ubuntu1
gnome-themes (2.14.2-0ubuntu1) to 2.14.3-0ubuntu1
gtk2-engines-clearlooks (1:2.7.4.is.2.6.9-0ubuntu1) to 1:2.7.4.is.2.6.10-0ubuntu1
gtk2-engines-crux (1:2.7.4.is.2.6.9-0ubuntu1) to 1:2.7.4.is.2.6.10-0ubuntu1
gtk2-engines-highcontrast (1:2.7.4.is.2.6.9-0ubuntu1) to 1:2.7.4.is.2.6.10-0ubuntu1
gtk2-engines-industrial (1:2.7.4.is.2.6.9-0ubuntu1) to 1:2.7.4.is.2.6.10-0ubuntu1
gtk2-engines-lighthouseblue (1:2.7.4.is.2.6.9-0ubuntu1) to 1:2.7.4.is.2.6.10-0ubuntu1
gtk2-engines-mist (1:2.7.4.is.2.6.9-0ubuntu1) to 1:2.7.4.is.2.6.10-0ubuntu1
gtk2-engines-pixbuf (2.8.18-0ubuntu2) to 2.8.20-0ubuntu1
gtk2-engines-redmond95 (1:2.7.4.is.2.6.9-0ubuntu1) to 1:2.7.4.is.2.6.10-0ubuntu1
gtk2-engines-smooth (1:2.7.4.is.2.6.9-0ubuntu1) to 1:2.7.4.is.2.6.10-0ubuntu1
gtk2-engines-thinice (1:2.7.4.is.2.6.9-0ubuntu1) to 1:2.7.4.is.2.6.10-0ubuntu1
gtkhtml3.8 (3.10.2-0ubuntu1) to 3.10.3-0ubuntu1
language-pack-de (1:6.06+20060705) to 1:6.06+20060725
language-pack-de-base (1:6.06+20060529) to 1:6.06+20060725
language-pack-en (1:6.06+20060705) to 1:6.06+20060725
language-pack-en-base (1:6.06+20060529) to 1:6.06+20060725
language-pack-gnome-de (1:6.06+20060705) to 1:6.06+20060725
language-pack-gnome-de-base (1:6.06+20060529) to 1:6.06+20060725
language-pack-gnome-en (1:6.06+20060705) to 1:6.06+20060725
language-pack-gnome-en-base (1:6.06+20060529) to 1:6.06+20060725
libeel2-2 (2.14.1-0ubuntu2) to 2.14.3-0ubuntu1
libeel2-data (2.14.1-0ubuntu2) to 2.14.3-0ubuntu1
libgnome-desktop-2 (2.14.2-0ubuntu1) to 2.14.3-0ubuntu1
libgnome-menu2 (2.14.0-0ubuntu1) to 2.14.3-0ubuntu1
libgnomeui-0 (2.14.1-0ubuntu2) to 2.14.1-0ubuntu3
libgnomeui-common (2.14.1-0ubuntu2) to 2.14.1-0ubuntu3
libgnomeui-dev (2.14.1-0ubuntu2) to 2.14.1-0ubuntu3
libgtk2.0-0 (2.8.18-0ubuntu2) to 2.8.20-0ubuntu1
libgtk2.0-bin (2.8.18-0ubuntu2) to 2.8.20-0ubuntu1
libgtk2.0-common (2.8.18-0ubuntu2) to 2.8.20-0ubuntu1
libgtk2.0-dev (2.8.18-0ubuntu2) to 2.8.20-0ubuntu1
libgtkhtml3.8-15 (3.10.2-0ubuntu1) to 3.10.3-0ubuntu1
libgtksourceview-common (1.6.1-0ubuntu6) to 1.6.2-0ubuntu1
libgtksourceview1.0-0 (1.6.1-0ubuntu6) to 1.6.2-0ubuntu1
libnautilus-burn3 (2.14.2-0ubuntu1) to 2.14.3-0ubuntu1
libnautilus-extension1 (2.14.1-0ubuntu9) to 2.14.3-0ubuntu1
libnspr-dev (2:1.firefox1.5.dfsg+1.5.0.5-0ubuntu6.06) to 2:1.firefox1.5.dfsg+1.5.0.5-0ubuntu6.06.1
libnspr4 (2:1.firefox1.5.dfsg+1.5.0.5-0ubuntu6.06) to 2:1.firefox1.5.dfsg+1.5.0.5-0ubuntu6.06.1
libnss3 (2:1.firefox1.5.dfsg+1.5.0.5-0ubuntu6.06) to 2:1.firefox1.5.dfsg+1.5.0.5-0ubuntu6.06.1
libpanel-applet2-0 (2.14.2-0ubuntu1) to 2.14.3-0ubuntu1
libpanel-applet2-dev (2.14.2-0ubuntu1) to 2.14.3-0ubuntu1
libtiff4 (3.7.4-1ubuntu3.1) to 3.7.4-1ubuntu3.2
libtiff4-dev (3.7.4-1ubuntu3.1) to 3.7.4-1ubuntu3.2
libtiffxx0c2 (3.7.4-1ubuntu3.1) to 3.7.4-1ubuntu3.2
libtotem-plparser1 (1.4.1-0ubuntu4) to 1.4.3-0ubuntu1
linux-image-2.6.15-26-686 (2.6.15-26.45) to 2.6.15-26.46
nautilus (2.14.1-0ubuntu9) to 2.14.3-0ubuntu1
nautilus-cd-burner (2.14.2-0ubuntu1) to 2.14.3-0ubuntu1
nautilus-data (2.14.1-0ubuntu9) to 2.14.3-0ubuntu1
python-gmenu (2.14.0-0ubuntu1) to 2.14.3-0ubuntu1
totem (1.4.1-0ubuntu4) to 1.4.3-0ubuntu1
totem-gstreamer (1.4.1-0ubuntu4) to 1.4.3-0ubuntu1
yelp (2.14.2-0ubuntu1) to 2.14.3-0ubuntu1
zenity (2.14.2-0ubuntu1) to 2.14.3-0ubuntu1

```


maybe some of the ubuntu-packages is the problem

---

### Post by newren on 2006-09-09
From the description, it sounds like you may have been experiencing [http://bugzilla.gnome.org/show_bug.cgi?id=354422](http://bugzilla.gnome.org/show_bug.cgi?id=354422).  It is a bug that has affected all versions of metacity, but it was a really rare race condition so not everyone will be affected by it, and duplication of the bug may be spotty.  (There was a similar race condition in much older versions of metacity that I was only able to trigger on certain hardware.)  It turns out that a recent change made the race condition in gnome bug 354422 much easier to trigger, which means that many other people will likely experience it too.  Anyway, there is a patch in gnome bug 354422; if you could try it and report whether it fixes your problem, I'd appreciate it.

---

### Post by gcranston on 2006-09-12
I'd love to let you know if the patch works for me but I have no idea how to apply it.  A little help?

Also my post:  [http://ubuntuforums.org/showthread.php?p=1488450#post1488450](http://ubuntuforums.org/showthread.php?p=1488450#post1488450)

---

### Post by gcranston on 2006-09-12
Though it's not the greatest fix, enabling "mouse-over gives focus" and "raise agter interval" in "System">"Preferences">"Window" does give focus and raise windows.

---

### Post by newren on 2006-09-12
The patch is part of metacity 2.16.1, which is made it into edgy yesterday.  Unfortunately, there were a couple patches that were applied to metacity during the 2.15.x development cycle that required newer software (gtk+-2.10.x, intltool-0.35) so although metacity-2.16.x is basically nothing more than metacity-2.14.x with a few dozen fixes, you can't just install this version on dapper.

---

### Post by gcranston on 2006-09-14
upgrading to metacity 2.16 has not fixed the problem.  I still cannot click a window to give it focus.  Also, holding alt and click-dragging to move a window does not work.

Can anyone suggest another window manager that doesn't look as horrible as IceWM?  I can't think of any.  Dual head (nVidia TwinView) support is key.

Thanks 

=Graham

---

### Post by newren on 2006-09-14
Any chance you could provide the exact version of metacity you tried?  (The fix was not in metacity 2.16.0)  Also, does clicking on the titlebar (temporarily) fix the problem?  If not, it sounds like you have a different bug than I think the others are having.

As for other WMs, you could try Xfwm (the window manager used by XFCE by default), Sawfish, openbox, KWin, blackbox, fluxbox, Window Maker, or any of a number of others.  The wikipedia entry for Window_manager has quite a long list.  :)

---

### Post by gcranston on 2006-09-14
2.16.1

---

### Post by gcranston on 2006-09-20
after the latest update 2006/09/19 for edgy, the problem is resolved for me.

On an unrelated note, watch out for mplayer and keep it locked to the version currently in dapper for at least a week or two, until version yadayada_Ubuntu5 comes out.  It has a linking error: [https://launchpad.net/distros/ubuntu/+source/mplayer/+bug/61222](https://launchpad.net/distros/ubuntu/+source/mplayer/+bug/61222)

---

### Post by shockEnterprise on 2006-11-10
I was faced with this problem out of the blue today... after finding no applicable answer... I decided to just try reinstalling the Ubuntu metacity package found here:

[http://packages.ubuntulinux.org/edgy/x11/metacity]("http://packages.ubuntulinux.org/edgy/x11/metacity")

It seems to work as expected now.  :D

---

