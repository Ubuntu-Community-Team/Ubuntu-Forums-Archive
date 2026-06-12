---
title: "Ubuntu thinks Sonic CD is an audio cd"
date: 2008-01-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by mycoplasma on 2008-01-08
I want to use wine to run the PC version of Sonic CD, which doesn't work with newer versions of Windows.  However, I can't explore the cd and find the setup program.  For some reason, Ubuntu thinks it's an audio cd.  if I use nautilus to look at the cd's contents, it says there are no files.  Can anyone please help me?

Also, (I'm not sure if this is important or not) I can listen to the game's music using rythmbox.  In the track listing, there is a track at the beginning called [data track] that I suspect is probably the game.

thanks in advance for all your help

---

### Post by Kilz on 2008-01-09
> **mycoplasma said:**
> I want to use wine to run the PC version of Sonic CD, which doesn't work with newer versions of Windows.  However, I can't explore the cd and find the setup program.  For some reason, Ubuntu thinks it's an audio cd.  if I use nautilus to look at the cd's contents, it says there are no files.  Can anyone please help me?

Also, (I'm not sure if this is important or not) I can listen to the game's music using rythmbox.  In the track listing, there is a track at the beginning called [data track] that I suspect is probably the game.

thanks in advance for all your help

I took a look for that title on the [wine application database]("http://appdb.winehq.org") but could not find that exact title. Perhaps you can use the search feature there and find more information.

---

### Post by Dr Eigen on 2008-01-09
I just tried this with a mixed audio/data CD here.  It wasn't mounted, as such.  A simple 'mount /dev/cdrom' mounted it.  Nothing appeared on the desktop, but I could then navigate to /media/cdrom from any File Browser window.

---

