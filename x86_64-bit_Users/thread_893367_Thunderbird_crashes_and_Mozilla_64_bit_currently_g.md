---
title: "Thunderbird crashes and Mozilla 64 bit currently gives wrong output."
date: 2008-08-18
forum: x86 64-bit Users
---

### Post by thomman on 2008-08-18
I have installed 32 bit firefox as follows

[http://ubuntuforums.org/showthread.php?t=202537&highlight=chroot](http://ubuntuforums.org/showthread.php?t=202537&highlight=chroot)

As explained on by my replies in those posts the navigation icons on firefox32 dont seem to be there. Also when i try to access anything on the 64 bit firefox the results are l garbled. 

I did some tinkering to get Windows fonts on my computer

[http://ubuntuforums.org/archive/index.php/t-106957.html](http://ubuntuforums.org/archive/index.php/t-106957.html). could this have caused this.


Today when I tried to open thunderbird. It opens and then closes immediately. To find out what was wrong I did the following on the terminal

:~$ thunderbird -safe-mode -jsconsole

I got the following error. I am using the default theme.

(gecko:6844): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'Segoe UI 9.75'

At one point I got it to load but the moment I pressed one of the mails to read it closed. I just shifted the day before yesterday to Ubuntu from Windows and mail is my priority its kind of giving me the creeps when something like mail acts up this way.

---

### Post by Ehtetur on 2008-08-22
Hi thomman - Try evolution as your email client...

For firefox, you probably want to rule out its config as the problem.. Try renaming your .mozilla directory and then start firefox. not sure why you got 32 bit & 64 bit firefox-3.0 versions installed, but I would uninstall the 32bit version...
> mv ~/.mozilla ~/_mozilla

---

### Post by thomman on 2008-08-24
Hi I reinstalled Ubuntu I needed flash on Ubuntu and I thought I couldnt have flash on Firfox 64 bit well I guess i found you could reinstalled and now everything works like a dream I use thunderbird formail as Evolution doesnt allow me to share mail folder with Windows Thunderbird as I sometimes use Windows too

---

### Post by Yellow Pasque on 2008-08-24
I see you solved the problem, but for anyone who digs up this thread in a search, I would suggest trying Swiftweasel/Swiftdove, as I believe they don't use Pango for fonts. [http://sourceforge.net/project/showfiles.php?group_id=195473](http://sourceforge.net/project/showfiles.php?group_id=195473)

---

### Post by Ehtetur on 2008-08-24
thomman - I'm glad you got firefox & thunderbird working again...

Now as for this other problem of yours: :twisted:
> **thomman said:**
> ...as I sometimes use Windows too

We'll just take things slow for now and leave it for another time, eh?

---

### Post by starkmaper on 2008-12-15
> **thomman said:**
> 
Today when I tried to open thunderbird. It opens and then closes immediately. To find out what was wrong I did the following on the terminal

:~$ thunderbird -safe-mode -jsconsole

I got the following error. I am using the default theme.

(gecko:6844): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'Segoe UI 9.75'

I did some tinkering to get Windows fonts on my computer

[http://ubuntuforums.org/archive/index.php/t-106957.html](http://ubuntuforums.org/archive/index.php/t-106957.html). could this have caused this.
Funny thing... Copying the windows fonts to linux COULD have caused this!
I'm running Gentoo 64-bits and recently copyd my windows fonts since OpenOffice.org3 now understands docx files but doesn't have the new default font for Word2007 (Kalibri).
This is when this error came up. Somehow Thunderbird starts using this font an crashes. Solution would be to tell Thunderbird not to use it.
However, the KDE4.1 font installer application crashes as well so i'm going to find the font file and delete it. 
I'll post here with results.

---

### Post by starkmaper on 2008-12-15
Well... Feeling mighty stupid now...
Copyd the windows fonts as root. Permissions to fonts were 700.
Hashing the fontdir using "xset fd rehash" as root creates a hashlist which contains unreadable fonts...
There you go!
Greetz,
Stark

---

