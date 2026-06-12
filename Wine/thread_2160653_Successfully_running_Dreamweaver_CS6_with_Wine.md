---
title: "Successfully running Dreamweaver CS6 with Wine"
date: 2013-07-06
forum: Wine
---

### Post by Mairu on 2013-07-06
Successfully running **Dreamweaver CS6** with Wine this evening, after piecing together information from the following pages:[INDENT=2][B][I][URL="http://appdb.winehq.org/objectManager.php?sClass=version&iId=20236&iTestingId=53581"]
http://appdb.winehq.org/objectManager.php?sClass=version&iId=20236&iTestingId=53581[/URL]
[http://www.thetechrepo.com/id=567](http://www.thetechrepo.com/id=567)
[http://blog.int3ractive.com/2010/08/how-to-run-flash-cs5-on-ubuntu-with.html](http://blog.int3ractive.com/2010/08/how-to-run-flash-cs5-on-ubuntu-with.html)[/I][/B]
[/INDENT]

I'm currently running **Ubuntu 10.04 (Lucid)**, but will try upgrading to 12.04.2 next.

I copied _***EVERYTHING***_ Adobe from a Windows 7 machine into the relevant location(s) in the **.wine/drive_c/** folder:[INDENT=2]
**C:/Program Files (386)/Adobe/     **[COLOR=#ff0000]*See note[/COLOR][B]
C:/Program Files (386)/Common Files/Adobe[/B]**/     **[COLOR=#ff0000]*See note[/COLOR][B]C:/Users/Andy/AppData/Local/Adobe/
C:/Users/Andy/AppData/LocalLow/Adobe/
C:/Users/Andy/AppData/Roaming/Adobe/[/B]


[/INDENT]
[COLOR=#ff0000]_***Note:**_[/COLOR] I had to rename the "***Program Files (386)***" folder to "***Program Files***" for a 32bit only installation of Ubuntu. I can't comment on 64bit versions, only that to make sure you get the directory names and structure correct.

Then I exported everything Adobe from the registry:[INDENT=2]
[B]HKEY_LOCAL_MACHINE/SOFTWARE/Adobe
HKEY_CURRENT_USER/SOFTWARE/Adobe
HKEY_USERS/S-1-5-21-xxxxxxxx-xxxxxxx-xxxxxxx/Software/Adobe[/B]
[/INDENT]

I'm not sure if ***ALL*** those registry entries are needed, but I thought better safe than sorry, and left nothing to chance! I renamed the exported .REG files to ***adobe1.reg***, ***adobe2.reg***, and ***adobe3.reg*** for simplicity, and put them in the **/home/** folder, then ran the following commands in Terminal:[INDENT=2] 
[SIZE=3][FONT=arial][B]wine regedit adobe1.reg
wine regedit adobe2.reg
wine regedit adobe3.reg[/B][/FONT][/SIZE]
[/INDENT]

Open Winetricks and choose "**Select the default wineprefix**" and click ***next***. Then "**Install a Windows DLL or component**". I installed the following (again, probably overkill!):[INDENT=2]
[B]atmlib
gdiplus
msxml3
vcrun2005
vcrun2008
vcrun2010[/B]
[/INDENT]

Next go back to the selection screen, and choose "***install fonts***":[INDENT=2]
[B]corefonts
tahoma
lucinda
uff[/B]
[/INDENT]

With all that done, I simply went to the Dreamweaver installation folder, right-clicked on ***Dreamweaver.exe*** and chose "**Open with Wine Windows Program Loader**", and it fired right up!

Hope this helps someone.

Incidentally, I also copied all the files for Photoshop CS6 and Illustrator CS6 at the same time, but neither worked. They crash whilst initialising.

Andy.

---

### Post by PhilGil on 2013-07-06
Some good suggestions already. I've been intending to try out [CK Editor]("http://ckeditor.com"), but haven't had a chance yet (I very rarely do web work). It looks pretty impressive, though, especially if you're looking for a WYSIWYG editor.

---

### Post by Mairu on 2013-07-07
Isn't CK Editor *just** a website "plug-in" to convert [plain] text boxes in a web form into rich text? I don't think it can be used as a standalone editor, but feel free to correct me on this.

At the end of the day though, there's nothing out there as full-featured and capable as Dreamweaver, for those who want a WYSIWYG editor.

I've been evaluating my installation of DW CS6 all day today, between the tennis and F1, and it's been stable and reliable. Now I need to get Photoshop CS6 and Illustrator CS6 working, and I'll be a happy chappy! :D

Andy.


[SIZE=1] *Not to take anything away from CK Editor... I've used it on the admin side of several online stores to make sending rich text mailshots out to customers and editing product descriptions easy for HTML-challenged store owners. It's a great addition to e-commerce packages, amongst other things.[/SIZE]

---

### Post by Bucky Ball on 2013-07-07
*Thread moved to **Wine**.*

Welcome to the forums.

Please do not hijack threads (especially old ones). Your post has nothing to do with the title of or the thread it was originally posted on. The OP was looking for an alternative to Dreamweaver, not wanting to know how to install it using Wine. You have basically posted a tutorial on how to do that. ;)

This might sound odd, but if you want to run all this high-end non-native software, why are you fiddling around using Ubuntu and Wine? Why not just dual-boot?

Anyhow, as this seems solved could you please mark it that way by following the link in my signature. Thanks and good luck. ;)

PS: There is not a lot of point posting a tutorial for a release that has reached end-of-life but some of it might be relevant to newer releases. Why don't you try it on 12.04 LTS then tweak what you have already got here?

---

### Post by Mairu on 2013-07-07
Because I'm new, and was trying to be helpful! (Hence adding that I would try an upgrade to 12.04 too.)

I'd been looking for an answer to this myself, and kept running into the same "non-answers". The OP was probably [possibly] looking for an alternative as there's nothing open source that can compare to DW, as was pointed out by other posters. I thought giving an insight how I managed to get it working may be useful, in context.

Andy.

---

