---
title: "Running MOHAA with Wine Issues"
date: 2007-05-31
forum: Wine
---

### Post by dj3019 on 2007-05-31
Okay.  Wine installed and running perfectly.  Installed MOHAA using wine and it installed perfectly.  Game opens and runs fine and even connects to online servers.  The problem is with the mouse.  For some reason the mouse pointer will not lock to the application regardless of checking the "Let DirectX Apps prevent the mouse from leaving the window".  Its like the pointer doesn't overlay the one for the OS.  It is like have two different pointers.  What's strange is that Jedi Knight 2 - Jedi Outcast runs perfectly if not better on Ubuntu than it did with windows.  And surprise surprise no mouse issues.  Jedi Knight loads the same as MOHAA and may even use the same pre-loader environment but I'm still confused as to this problem.  If you've got the fix let me know!

Steps I've taken:
1. Get all updates and upgrades by using (sudo apt-get update | sudo apt-get upgrade)
2. Installed WineCVS by compiling the developer package using the walkthrough here in the forums
3. I've configured Wine (winecfg) and checked the DirectX Apps Checkbox at the top
4. (Your step goes here) ^_^

---

### Post by hikaricore on 2007-05-31
Was it necessary to make another wine thread about the same game(s)?

---

### Post by dj3019 on 2007-05-31
Actually yes.  I am really desperate to get back into playing my game online and the forum seems to have died off on this particular issue.  I do apologize for the multiple posts into the forums about this and I will gladly remove them all when it is resolved and then post a step-by-step tutorial about how to install and configure wine to run this particular game as it seems to differ from the rest.  So, in actuality this isn't just about me and my many posts but rather for the community.  What linux was made for us to do.  Share the open source and make a better way to use the computer. So my apologies once again about the many posts.

---

### Post by noerrorsfound on 2007-06-01
Why run it with Wine when there's a native Linux version available?
[http://liflg.org/?catid=6&gameid=8](http://liflg.org/?catid=6&gameid=8)

---

### Post by rcatman on 2007-07-02
i'm happy for this thread. 

it was the first result in my google search and exactly what i was looking for. Thank you :)

---

### Post by fairyliquidizer on 2007-08-12
has anyone got the Loki installer working on 64 bit?

I keep getting the following error:

"/home/russ/.setup12116: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory"

Thanks,
Fairy:guitar:

---

### Post by cogadh on 2007-08-12
It looks like you need to install the libgtk package. Search Synaptic for it.

---

### Post by khristian on 2007-09-03
> **dj3019 said:**
> Okay.  Wine installed and running perfectly.  Installed MOHAA using wine and it installed perfectly.  Game opens and runs fine and even connects to online servers.  The problem is with the mouse.  For some reason the mouse pointer will not lock to the application regardless of checking the "Let DirectX Apps prevent the mouse from leaving the window".  Its like the pointer doesn't overlay the one for the OS.  It is like have two different pointers.  What's strange is that Jedi Knight 2 - Jedi Outcast runs perfectly if not better on Ubuntu than it did with windows.  And surprise surprise no mouse issues.  Jedi Knight loads the same as MOHAA and may even use the same pre-loader environment but I'm still confused as to this problem.  If you've got the fix let me know!

Steps I've taken:
1. Get all updates and upgrades by using (sudo apt-get update | sudo apt-get upgrade)
2. Installed WineCVS by compiling the developer package using the walkthrough here in the forums
3. I've configured Wine (winecfg) and checked the DirectX Apps Checkbox at the top
4. (Your step goes here) ^_^

I installed MOHAA in windows and copied the instalation to my linux partition. it runs perfectly in Ubuntu, except for one thing: i can't rotate more than 270 degrees.
Any clues on solving this weird issue?

---

### Post by cogadh on 2007-09-03
It is a problem with Direct Input in Wine, many games suffer from it. If the game has the option to disable Direct Input events for the mouse in either its options or a config file, then that can sometimes correct the problem.

---

