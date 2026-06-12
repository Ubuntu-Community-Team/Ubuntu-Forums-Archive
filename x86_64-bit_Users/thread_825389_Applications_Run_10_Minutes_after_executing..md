---
title: "Applications Run 10 Minutes after executing."
date: 2008-06-10
forum: x86 64-bit Users
---

### Post by onering on 2008-06-10
I just installed 8.04 64bit.  I installed several programs through the package manager including Frozen Bubbles 2. They all seem to work fine except for when I run Frozen Bubbles 2.  After executing the program nothing happens for about 10 minutes, then all of a sudden the program starts running.

Is there any way to tell why it is doing this?  It's like there is a 10 minute lag somewhere in the program or OS.

Thanks.

---

### Post by cubeist on 2008-06-11
> **onering said:**
> I just installed 8.04 64bit.  I installed several programs through the package manager including Frozen Bubbles 2. They all seem to work fine except for when I run Frozen Bubbles 2.  After executing the program nothing happens for about 10 minutes, then all of a sudden the program starts running.

Is there any way to tell why it is doing this?  It's like there is a 10 minute lag somewhere in the program or OS.

Thanks.

That's really strange! Have you been starting the programs with the *at* command, or some special cron job?  That's all I can think that might do it.

Nevertheless, try starting FB from the terminal and see if there is an error displayed...

---

### Post by nikgare on 2008-06-11
It maym be something wrong with you networking - this has caused delays for me before.
I can't really give any more help than to check /etc/hosts and make sure that all the local stuff is correctly configured.
Nik

---

### Post by onering on 2008-06-11
When I run Frozen-Bubbles from the command line this is what I get.  It seems just hand there doing the same thing as when I run it from the pull down menu.  After about 10 minutes it just starts to run!  VERY STRANGE!!


/usr/games$ frozen-bubble
        [[ Frozen-Bubble-2.1.0 ]]

  [http://www.frozen-bubble.org/](http://www.frozen-bubble.org/)

  Copyright (c) 2000-2006 The Frozen-Bubble Team.
 
    Artwork: Alexis Younes
             Amaury Amblard-Ladurantie
    Soundtrack: Matthias Le Bidan
    Design & Programming: Guillaume Cottenceau
    Level Editor: Kim and David Joham

  Originally sponsored by Mandriva <http://www.mandriva.com/>

  This program is free software; you can redistribute it and/or modify
  it under the terms of the GNU General Public License version 2, as
  published by the Free Software Foundation.

[SDL Init] 





> **cubeist said:**
> That's really strange! Have you been starting the programs with the *at* command, or some special cron job?  That's all I can think that might do it.

Nevertheless, try starting FB from the terminal and see if there is an error displayed...

---

