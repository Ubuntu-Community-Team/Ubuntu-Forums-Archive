---
title: "Fatal Error Could not load module 'bin/vgui2.dll&quot; (Steam/WIne Error need help)"
date: 2007-03-20
forum: Wine
---

### Post by CDiablo on 2007-03-20
I've been trying (forever) to get steam to run in its own x window as I the framerate drop is really a pain when playing Counter Strike. Does anyone have any fix for this error?

Does anyone know of a easy and effective way to get steam to run in its own X window?

I can get steam to work on my desktop but I feel that it is slowing it down. I am using Edgy and have a GEforce 6800gt with the most recent Nvidia drivers. Thanks all.

---

### Post by deepwave on 2007-03-25
Hmm... had a similar problem after upgrading to Feisty yesterday.  Running winecfg seemed to fix the problem.

---

### Post by Astenorh on 2007-04-11
delete ClientRegistry.blob file, wait, and it should work. It works for me

---

### Post by snerge on 2007-04-11
> **Astenorh said:**
> delete ClientRegistry.blob file, wait, and it should work. It works for me

I attest that this solution worked fine on feisty.

---

### Post by skattyadz on 2007-09-02
EDIT: Dont worry I fixed it by running from the terminal.

---

### Post by rakan21 on 2008-05-23
how do you run it from terminal and what do you run from terminal?

---

### Post by [z]er0 HP on 2008-09-25
a bit of a late response but i stumbled on this when i am having my own steam issues, To run from terminal you need to type

```

wine "c:\program files\steam\steam.exe"

```

---

### Post by |{urse on 2008-12-03
I don't know if anyone else is still having this problem but zero hp's solution should not and will not work.

If you are getting this error you need to create a small bash script like this
> cd Desktop
> touch steam
> gedit steam

Paste the following into gedit

```
#!/bin/bash
cd ~/.wine/drive_c/Program\ Files/Steam/
wine steam.exe
```

now press Ctrl + S to save and close gedit

back in the terminal
make your script executable

> chmod +x steam

now you can double click your script to launch steam correctly. ;)

---

### Post by Inoki on 2010-10-10
that doesn't help. any ideas? i've tried all of the above.

---

### Post by duxxyuk on 2010-11-05
Apologies that you've had to wait 3 weeks for someone to respond.
I too had this problem.. Tried the above but like Anathaen, no dice.

I simply went mad and wiped off my entire .wine directory. Worked like a treat afterwards:

rm ~/.wine -Rf 

Regards,

D.

---

### Post by Quadgnim on 2010-12-02
I've discovered that installing crypt32 generated this error.  I had installed it using "winetricks  crypt32".  I didn't know how to uninstall it so I had to blow away my .wine folder and reinstall everything.  Moral of the story, stay away from crypt32 if you can.

---

### Post by Essence on 2011-01-06
I just had this problem as well, and thank you for the reply. I figured out a quicker way to remove the crypt32 however. 

Run
1) winecfg
2) Go to the 'Libraries' Tab
3) Select Crypt32 from the existing overrides tab
4) Click remove

---

