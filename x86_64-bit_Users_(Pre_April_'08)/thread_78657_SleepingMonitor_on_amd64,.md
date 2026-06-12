---
title: "Sleeping/Monitor on amd64,"
date: 2005-10-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by berlinbrown on 2005-10-18
I am on AMD64 ubuntu 5.10, I have a question. I am trying to setup a
server that also has some GUI. It seems to go to sleep when the monitor
deactivates or the harddrive? When I try to hit the server from a
remote location it seems dead. I have to manually mouse-out?

Is there a way to prevent this and keep the screen/harddrive calm
downs?

I want everything including the ability to hit my server. Only thing I
can think of is some cron job or something to hit the filesystem? or
possibly activate after 3 hours or so? 

Somebody mentioned that this may be an AMD64 issue?  Can I use x86 OS on the AMD64?

---

### Post by RAOF on 2005-10-19
Mmm, odd.  My Breezy64 at home is quite happy for me to ssh in, & I've not done anything special to it.  I assume you've done the obvious stuff, like actually installing ssh & whatever services you want running... Breezy by default runs (practically) nothing that listens to the network.

When you say "it seems dead" what exactly are we talking about?  You can't ping it?  You can't ssh into it?  How remote (ie: how many network components away) is the remote location?

Oh, and you can happily run 32-bit Breezy on an athlon64.

---

### Post by berlinbrown on 2005-10-19
Yep, once that screen goes dark the machine seems dead to the world.  I cant ping it or ssh or anything, and when I mouse over the screen and it looks alive, I can get into the machine remotely(through the internet). 

I think that when it sleeps(monitor or drive?), it must drop the outbound connection or something.  I am using a DSL modem, might be something there.

---

### Post by RAOF on 2005-10-19
Ok, that's totally weird.  I don't suppose that your dsl modem is set to disconnect after a certain period of inactivity?  That's really the only reason I can think of.

---

