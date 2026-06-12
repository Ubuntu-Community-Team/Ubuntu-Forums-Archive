---
title: "Hardy Heron Gnome Panel (odd icon behaviour - large icons)"
date: 2008-05-05
forum: x86 64-bit Users
---

### Post by Thene on 2008-05-05
I've upgraded to Hardy Heron and I have an unusual problem.

The Applications menu icon and the logout icon bigger than the any other icons on the panel. Also because the logout icon is bigger it appears to affect the time and date format - forcing it to display in 2 lines date on top and time below. (I know some people would like that format - but I prefer one line).

I'm using the black-white icon set from [http://www.gnome-look.org/content/show.php/black-white?content=70299](http://www.gnome-look.org/content/show.php/black-white?content=70299)

This is the icon set that I was using when I upgraded from Gusty to Hardy. Which of course was displaying properly previous to that.

I have tried:
- Removing & reinstalling the panel
- Changing icon themes - which strangely enough, none of the other icon themes exhibit the same behaviour, even icons from the same group
- Reinstalling the icons/downloading and reinstalling the icons
- Using 'Add to Panel' I've removed and re-added the Menu Bar

I've also noticed that if I select add to panel I have an option of the Gnome Main Menu which _shows the same icon at the correct size_ - but it's only the icon (Applications/Places/System - only shows as sub menus and are not visible on the panel)

However I'm using the 'Menu Bar' which is a custom menu bar?

If anyone could shed some light on how to correct this I'd be grateful.

Thanks :)

I've added attachments to demonstrate. First shows the larger icons & the second shows the smaller - you may only be able to tell by the logout buttons.

Lastly - could be related to these:
[http://ubuntuforums.org/showthread.php?p=4647609](http://ubuntuforums.org/showthread.php?p=4647609)
[https://bugs.launchpad.net/ubuntu/+source/ubuntulooks/+bug/199109](https://bugs.launchpad.net/ubuntu/+source/ubuntulooks/+bug/199109)
[https://bugs.launchpad.net/ubuntu/+source/ubuntulooks/+bug/131974](https://bugs.launchpad.net/ubuntu/+source/ubuntulooks/+bug/131974)

---

### Post by Thene on 2008-07-19
I can actually confirm that this happens on my laptop as well, which is 32bit but running the same theme.

Here are some more related links to the bug:
[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/223075](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/223075)
[http://ubuntuforums.org/showthread.php?t=758957](http://ubuntuforums.org/showthread.php?t=758957)
(The link below also has an image the demonstrates the same problem.)
[http://bugzilla.gnome.org/show_bug.cgi?id=537661](http://bugzilla.gnome.org/show_bug.cgi?id=537661)

It appears to be a bug in the Gnome Main Menu - using the Gnome Main Menu forces the menu bar to enlarge.

However in my case - in my "Add To Panel" box it's not the Gnome Main Menu but the Custom Main Menu that does it. Strangely enough the Gnome Main Menu is an "icon only" menu and the Custom Main Menu is the menu with the "Applications Places & System" menus.

The difference I have noticed is that, changing the icons to a different icon set returns the size back to normal. It appears to only act this way with the icon set I was using during the upgrade to Hardy Heron.

I've compared the gtk-2.0 files to other icon sets and it's the same - so it's got me absolutely stumped as to what may have happened. 

(I'm going to post these notes at Gnome's bugzilla.)

---

