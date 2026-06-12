---
title: "Wine Keeps Putting Stuff on my Windows Desktop. Halp?"
date: 2007-12-14
forum: Wine
---

### Post by DM was on fire! on 2007-12-14
My original problem's been fixed, but now I have another.
Wine is now broked. XD Whenever I try to run a program, I get no response, and when I enter winecfg in terminal, I get this:

"X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  1 (X_CreateWindow)
  Resource id in failed request:  0x4c
  Serial number of failed request:  13
  Current serial number in output stream:  15"

Sounds like X is going mad, but I don't know how to fix it. :\

---

### Post by cogadh on 2007-12-14
It sound like you just need to change the default paths in Konquerer and Epihany to your actual Desktop path.

---

### Post by DM was on fire! on 2007-12-14
> **cogadh said:**
> It sound like you just need to change the default paths in Konquerer and Epihany to your actual Desktop path.

That's the strange thing, though. According to Konqueror, that's where I'm saving, and same for Epiphany.
And when I drag the file from the /home/ashleigh1992/.wine/drive_c/windows/profiles/ashleigh1992/Desktop folder to /home/ashleigh1992/Desktop/, I get a dialog telling me there's already a file with that name, and asking if I want to replace it. When I click replace I get this error:

"Error "File not found" while moving "FILEHERE".
Would you like to continue?"

And when you click retry, you get the same message.
Clicking cancel closes out the dialog, and then makes the file go bye bye. :\

I've got it worked out for now, it's just hard to get used to.

EDIT - I restarted and when my computer came back on, one of the files I had accidentally saved to my desktop was now there. Weird.

---

### Post by DM was on fire! on 2007-12-14
*pokes thread up*
Any help with my new problem? :\

EDIT - Never mind. It fixed itself.
Yay.

---

