---
title: "Menu won't show games added by Alacarte"
date: 2008-09-16
forum: x86 64-bit Users
---

### Post by Gerafin on 2008-09-16
I just installed Hardy Heron Ubuntu x86 AMD 64, and everything's been going great so far. However, I've run into a problem regarding Alacarte. I installed Sauerbraten and Battlestar Galactica: Beyond the Red Line, and they both run fine from the terminal. However, I wanted to add them to the Applications -> Game menu. So I ran sudo alacarte, and the Alacarte menu editor popped up. I highlighted "Games" in the left hand drop-down menu, and hit the "New Item" button. I filled in the information correctly, making sure that it was directed to the right script. Then I hit "OK" and "Close." However, neither game shows up in the Applications -> Game menu. I restarted, looked in different parts of the menu to see if I misplaced it, and retried at least three times... however, I still can't see them.

I have a feeling this is just a matter of me doing something wrong, because I've browsed the forums and it seems that nobody else has had this problem. If you have any ideas, I'd be very grateful.

The information I entered was this, if it helps:

Type: Application
Name: Sauerbraten
Command: sh /home/mike/Games/sauerbraten-launch.sh  (this is the right path, i've double-checked)

---

### Post by DrMega on 2008-09-16
A daft question I know, but is the 'Show' tick box ticked next to the missing item?

---

### Post by Gerafin on 2008-09-16
Whups! I looked further and discovered about six shortcuts in the "Other" menu. So, I guess it *was* adding them after all! So, a different question: none of them show up in the Alacarte editor, only in the menu itself. Any way to move these from "other" to "games"?

---

### Post by Gerafin on 2008-09-16
> **DrMega said:**
> A daft question I know, but is the 'Show' tick box ticked next to the missing item?

They now show up in the menu, but not in Alacarte... so they're "Showing" all right, just not in Alacarte. This means that I can't actually tick any boxes :(

---

