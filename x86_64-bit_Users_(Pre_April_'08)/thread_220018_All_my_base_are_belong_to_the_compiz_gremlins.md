---
title: "All my base are belong to the compiz gremlins"
date: 2006-07-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by Beamerboy on 2006-07-20
OK So I have managed to completely hose my X environment by trying to install compiz + xgl.

My system is now close to unuseable despite having followed the HOWTO to the letter.

I have XGL and Compiz running and I even have gnome-window-decorator running, but stuff just isn't working well at all.

Lets start from the top:

I can no longer restart X with ctrl+alt+backspace.  If I try this, I can no longer in to any session, I get an "incorrect username/password" error.  I have to manually open a console and do /ect/init.d/gdm restart in order to get back into X.

Secondly, I had to manually edit ~/.gnome2/session and add anything I wanted to load on startup there.  Namely xchat and gnome-terminal so I can get help from the irc channels and I have a temrinal to launch other applications from.  Before I did this, I was greeted by a completely blank desktop with no mouse menus, no panel.  I can launch gnome-panel from the terminal which then gives me access to the menus and launchers.

Gnome-panel icon bar no longer works, none of my open windows appear on there at all.

None of my applications have any window decoration neither do they respond to <ALT><Click> to move them.  My only option for moving them is to use wmctrl from the command line (although I haven't even tried this yet so that might not even work).

I have used gconf-editor to added the plugins for compiz, made no difference.

Incidentally I have all the latest dependencies and packages and I am running the nvidia official drivers.

If anyone at all can help me sort out thismess, I would be truly grateful.  This has turned into an unmitigated disaster.

Beamerboy

PS - I forgot to mention that my keyboard loads some funky lanuage when X starts up instead of the UK keyboard.

---

### Post by falcon15500 on 2006-07-23
What compiz plugins do you have configured in gconf?  The fact that you have no window decorations proves that compiz is running - but the decoration plugin has to be configured for use.

falc

---

### Post by mkw87 on 2006-07-25
Similar thing happened to me last night, I headed to IRC to get it solved, we got Xgl working, but not compiz, I experienced the 'black screen bug', so I gave up and undid everything.

One tip, to get your window bars back (to be able to move stuff around, etc), type "metacity --replace &" in a console and that will replace compiz with metacity and let you be able to do other things to try to fix it, or uninstall =/  I had it working before, but reformatted because I am just trying to convert now and want to get a clean as possible system going, even though I can see now I'm going to have to reformat ~a bazillion times :P  Oh well, that part of it is no different from windows.

---

