---
title: "Freeze on GNOME search director window"
date: 2005-11-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by Antithesis on 2005-11-14
Hi,

We've just upgraded to Ubuntu Breezy, and are having the following problem:
Whenever using a dialog which is used to select a directory (examples below), upon selection, the program freezes and never responds again - Must force quit.
However, if instead of using the dialog, I type in the directory I want to use, everything works fine. We didn't have this problem before upgrading to breezy.

Examples:
In Anjuta, Import project, select directory window, use browse, select a directory with the mouse.
In Meld, Press File->New. Use browse to select a file or a directory. I get a freeze.

I'm not sure if this is a library conflict of some sort, or a known bug.

I would appreciate any help or input you may have - Thanks!

---

### Post by Mentalbug on 2006-01-10
Hi there, I'm getting the same freeze problems here, found this post by Googling "Anjuta freeze" ;)

Though im not an "AMD 64 user".  Using Anjuta version 1.2.4 gotten from Ubuntu Breezy's apt-get.
I'll try to put more info later on the specs of my machine.

Though, have you had any advancement in your problem since you posted this message?  I'd be very glad to hear it :]

---

### Post by Antithesis on 2006-01-11
MentalBug, not much progress since I've posted this.

I have posted a bug in gnome ([http://bugzilla.ubuntu.com/show_bug.cgi?id=19777)](http://bugzilla.ubuntu.com/show_bug.cgi?id=19777)), to try to get them to fix it, as I found that it was not isolated to Anjuta (Also happened with Glade on that machine)

The machine where this happened is not at home, and I don't have access to it right now, so I can't really keep supplying the info requested by those guys - if you wanna pick up the slack I would appreciate it, though I'm trying to see if I can get someone who does have access to the machine where it happened to me to help them out with that stuff (we'll see).

One workaround I did find (as I posted in the bug) is that if I type in the addrees instead of using the GUI, I have no problem - and that is what I've done since then.

---

### Post by sammal on 2006-01-12
I'm running breezy on amd 64 laptop and get exactly the same behaviour. First I thought it's just random app crashing, but later realised it's probably something to do with the file chooser cause apps crash randomly (and pretty much only) when pressing "Browse" or similar which one'd expect to bring up the file chooser.

-Lasse

---

### Post by grugnog on 2006-03-14
Just a quick heads up for anyone who has external links (ftp, sftp etc) in their gnome Places bookmarks menu and experiencing a slowdown (or [hang]("https://launchpad.net/products/gnome-panel/+bug/32873")) in the search box appearing or the file chooser. You can prevent this by running Applications/System/Configuration Editor and changing /desktop/gnome/interface/file_chooser_backend
 from 'gnome_vfs' to 'gtk+'.

---

### Post by Mentalbug on 2006-03-14
Thanks for the tip but... well... didn't make it for me.  At least not in anjuta ;)
I also removed the only remote link i had in "Gnome places", (it was samba link to a windows computer), but with no more luck.

The hang (I haven't noticed any slow down, only that hanging) still only occurs while selecting a directory (say, like an "include" directory in an anjuta project) and validating the choice.

---

