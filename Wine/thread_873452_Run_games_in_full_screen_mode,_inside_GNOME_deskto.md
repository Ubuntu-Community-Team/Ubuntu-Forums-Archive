---
title: "Run games in full screen mode, inside GNOME desktop"
date: 2008-07-29
forum: Wine
---

### Post by BoneSmash on 2008-07-29
I was wondering if it was possible to have games run full screen inside of the GNOME desktop, sort of like what's shown in this picture:
[IMG]http://farm4.static.flickr.com/3176/2375868831_cc2c0705fc.jpg[/IMG]

The one problem with the setup shown there is that the toolbars on the top and bottom cut some of the game off.  Is there a way to force it to a certain resolution, and make it not get overlapped?  If all this would be possible then this could fix alot of my problems with gaming on Linux, mainly the fact that Gfire in Pidgin doesn't support in-game chat.

Thanks

---

### Post by oedipuss on 2008-07-29
In certain cases you can run a game windowed in a resolution similar to the one you're using, only with less height. 1280x900 for instance, in a 1280x1024 desktop. Then there are utilities such as devilspie than can undecorate the window, or force it to a certain position. It pretty much simulates what that screenshot shows. If the game allows for arbitrary window resolution even better, you can match it exactly.

---

### Post by Felson on 2008-07-29
Check out wmctrl also look at [wmctrl GUI]("http://www.myte.ca/cgi/myte/members/main.pl/other.html#wmctrl_gui") on my website.
It does full screen a bit different. The trick is to set the game to the same rez as your screen, and you should be golden.

Also take a look at "Wine Xwindow" on my site. I used to do what you are trying to do, but switched to this method. If you have dual screens it may not be a great answer for you though, as you will loose access to your other screen. If this idea interests you, look at [this]("http://ubuntuforums.org/showthread.php?t=854354") thread to see how to use it.

---

