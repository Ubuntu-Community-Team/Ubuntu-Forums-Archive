---
title: "Computer &quot;hard-locks&quot; when i click 'audio' tab in winecfg"
date: 2008-09-13
forum: Wine
---

### Post by AFarris01 on 2008-09-13
I've got an odd problem with my brother's computer that im not really sure how to fix.  

we installed linux and WINE a little while back, fresh ubuntu 8.04 install, after his windows install got invaded by millions of spywares.  So far it has seemed to work fine just running applications, (mainly diablo 2 and fallout 2), but he's got no sound in WINE whatsoever.  on top of that, we cannot configure the sound settings in winecfg, because if you click the 'audio' tab it causes the whole system to hard-lock.

there's no command line output to post, because as i said before, the system hard-locks whenever you click the audio tab, and i've already tried reinstalling WINE.  so far, i haven't found any other info online about this issue except for the line in one of this forum's stickys that says 'upgrade to a newer ubuntu,' which cant happen for at least another month or so...

basically...is there any way for me to discover the actual problem, so i can fix it?  or is there possibly a way to configure WINE's sound settings without using winecfg?

thanks for the help!

---

### Post by lakersforce on 2008-09-14
Are you sure it "hard-locks"?

This is normal. It's not really locked, it's just looking for information. This only happens the first time you click the tab and takes about 30 secs to complete.

---

### Post by AFarris01 on 2008-09-14
positive that it hard locks.

I've let it sit for hours before, and nothing happens.  in addition, the mouse cant move, and theres no response from the keyboard, and the system monitor app on the panel stops moving.  

at that point, it wont let me ctrl+alt+backspace to restart x, nor can i switch to one of the tty terminals, it just stays there, and i have to to a hard reset.

also, i tried re-installing ubuntu today to see if the issue would fix, but i ended up with an even wierd-er problem.  now, when the 'audio' tab is clicked, the computer doesn't freeze, and the audio options come up, so we can select an alternate configuration, but the sound still doesn't work, and when the audio tab is clicked, the computer begins lagging out horridly, which doesn't end when winecfg is closed.  in addition, i can't launch any other applets, and any attempt to do so results in gnome spitting out a general input/output error.  

again during these events, the keyboard does not respond to input, so i cant ctrl+alt+backspace, switch to a tty terminal, or run any commands via alt+F2.  the only thing that actually works is the 'quit' applet, but all the icons are gone, and the only way to fix the issue is to restart the computer.

my brother is currently using the computer for something else, but i'll run winecfg from the terminal in a little while, and post back if there's any erroneous output.

---

