---
title: "Lost Firefox in one profile"
date: 2008-04-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by tbzep on 2008-04-19
After upgrading to Hardy Beta, and  Firefox 3.0b5, I've lost the ability to launch Firefox in one of my kid's profiles.  The old FF2 icons are still on the panel and in the accessories menu. 

 I tried making a new launch icon using "which firefox" to browse to the location. It came up as /usr/bin/firefox, so I put that in the command box.

I also tried using "firefox %u" in the command box, which is what is in the command box on all the other working profiles. 

After that I tried using terminal and typed in "firefox".  It didn't load, but it does load it in all other profiles using terminal.

I've checked the folder in the offending profile and .mozilla is there.  I went as far as replacing it with one from my working profile and still have no luck.

---

### Post by edward4130 on 2008-04-19
Possible ways to narrow this down. you could duplicate the profile of a working user and then modify it for the Kid.  That should do it it is something in the profile that is causing the problem.

If it is permissions, you should be getting an error when in terminal and attempting to launch.  If so you need to put the user on the group that can use Firefox.

That should get you a start, I have yet to do multiple profiles for desktop environments on linux only for servers.

---

### Post by tbzep on 2008-04-19
Thanks.  I made an extra profile back when I was trying to track down problems with program associations, so I understand what you are talking about.  

I'm not getting errors.  The launch icons, both old and the one's I've made, just do nothing.  When using terminal and typing in "firefox", I hit enter and it just goes back to the command prompt.  Nothing is displayed at all.

---

