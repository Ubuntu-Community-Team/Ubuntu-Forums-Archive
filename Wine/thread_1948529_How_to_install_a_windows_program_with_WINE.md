---
title: "How to install a windows program with WINE?"
date: 2012-03-28
forum: Wine
---

### Post by Carnivorum on 2012-03-28
I just installed WINE, and now when I put a disc with a windows program in the CD player, I don't get it installed. 

Any tips for this one?

---

### Post by philinux on 2012-03-28
Moved to wine forum.

---

### Post by EzioAuditore on 2012-03-28
Right click the exe setup file and select 'open with wine' or similar option. 
Be sure to check [appdb.winehq.org/](appdb.winehq.org/) for a list of application compatibility.

---

### Post by TeoBigusGeekus on 2012-03-28
Browse to the cd via terminal and do something like
```
wine installer.exe
```
or
```
wine setup.exe
```
etc.

---

### Post by Carnivorum on 2012-03-28
> **EzioAuditore said:**
> Right click the exe setup file and select 'open with wine' or similar option. 
Be sure to check [appdb.winehq.org/](appdb.winehq.org/) for a list of application compatibility.

When I do as you say, I get this message:  

The file '/media/BIBLE/SETUP.EXE' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.

---

### Post by Carnivorum on 2012-03-28
> **Carnivorum said:**
> When I do as you say, I get this message:  

The file '/media/BIBLE/SETUP.EXE' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.

This same message I get with another program which I had working just fine with Ubuntu 9.04

---

### Post by Carnivorum on 2012-03-28
> **TeoBigusGeekus said:**
> Browse to the cd via terminal and do something like
```
wine installer.exe
```

When I do that I get: 

wine: cannot find L"C:\\windows\\system32\\installer.exe"

> 
or
```
wine setup.exe
```
etc.

---

### Post by jerome1232 on 2012-03-28
type wine into your terminal, press space, then drag and drop the setup executable into your terminal.

---

### Post by Carnivorum on 2012-03-28
> **jerome1232 said:**
> type wine into your terminal, press space, then drag and drop the setup executable into your terminal.

And what is the "setup executable"?

---

### Post by jerome1232 on 2012-03-28
The installer on the cd, probably setup.exe, browse into the cd and look. The same file you said gave you a permission error earlier when you tried to run it.

---

### Post by Carnivorum on 2012-03-28
> **Carnivorum said:**
> And what is the "setup executable"?

I figured it out.  I dragged the icon of the CD with EXE on it into the terminal, and I got both windows programs working now. 

Thanks for the help.

---

### Post by Carnivorum on 2012-05-01
Bs'd

I upgraded to 12.04, got some windows programs working just fine, but one, who worked OK under 9.04 and 10.04, doesn't work now.  

I install it with WINE, and when I click on the desktop icon to start it, i get the message:  "To use Library you must have installed the following fonts with Fonts Control Panel.  One or more of them is missing: 
Drogulin
Arial

What can I do about that?   Didn't get that message in previous Ubuntu distro's, it worked there without a hitch.

---

### Post by Carnivorum on 2012-05-13
Bs'd

Does anybody know where I can find that "fonts control panel"?

---

### Post by Carnivorum on 2012-05-13
Bs'd

Does anybody know how to install the fonts Drogulin and Arial?

---

### Post by dino99 on 2012-05-13
Arial can be installed via winetricks
Drogulin is provided by : [http://opensiddur.org/2010/07/unicode-compliant-and-open-source-licensed-hebrew-fonts/](http://opensiddur.org/2010/07/unicode-compliant-and-open-source-licensed-hebrew-fonts/)

[http://wiki.jswindle.com/index.php/Fonts](http://wiki.jswindle.com/index.php/Fonts)
[http://wiki.jswindle.com/index.php/Winetricks](http://wiki.jswindle.com/index.php/Winetricks)

---

### Post by Carnivorum on 2012-05-16
> **dino99 said:**
> Arial can be installed via winetricks
Drogulin is provided by : [http://opensiddur.org/2010/07/unicode-compliant-and-open-source-licensed-hebrew-fonts/](http://opensiddur.org/2010/07/unicode-compliant-and-open-source-licensed-hebrew-fonts/)

[http://wiki.jswindle.com/index.php/Fonts](http://wiki.jswindle.com/index.php/Fonts)
[http://wiki.jswindle.com/index.php/Winetricks](http://wiki.jswindle.com/index.php/Winetricks)

Bs'd

I just installed Arial, and I got my Judaic Classics Library working. 

Thanks a lot for the help.

---

### Post by Carnivorum on 2013-01-30
> **dino99 said:**
> Arial can be installed via winetricks
Drogulin is provided by : [http://opensiddur.org/2010/07/unicode-compliant-and-open-source-licensed-hebrew-fonts/](http://opensiddur.org/2010/07/unicode-compliant-and-open-source-licensed-hebrew-fonts/)

[http://wiki.jswindle.com/index.php/Fonts](http://wiki.jswindle.com/index.php/Fonts)
[http://wiki.jswindle.com/index.php/Winetricks](http://wiki.jswindle.com/index.php/Winetricks)

Bs'd

Got myself a new comp, installed 12.04 LTS on it.  

Have now the same problem with the same program, I need to install Hebrew fonts. 

The above solutions don't work anymore for me.   

Anybody any ideas?

---

### Post by lekevinio on 2013-02-02
Right click the .exe file and choose Properties.
Go to Permissions and in the bottom you should see something like Unlock file.
If that doesn't work then also check the check box to make it an Executable file. That should do the trick.

---

### Post by Carnivorum on 2013-02-08
> **lekevinio said:**
> Right click the .exe file and choose Properties.
Go to Permissions and in the bottom you should see something like Unlock file.
If that doesn't work then also check the check box to make it an Executable file. That should do the trick.

Bs'd

If I try to check a box, he won't let me.  He says then:  "Sorry, could not change the permissions of "INSTMSIW.EXE": Error setting permissions: Read-only file system"

Also, there is nothing like: "Unlock file".

---

### Post by Carnivorum on 2013-02-08
> **dino99 said:**
> Arial can be installed via winetricks
Drogulin is provided by : [http://opensiddur.org/2010/07/unicode-compliant-and-open-source-licensed-hebrew-fonts/](http://opensiddur.org/2010/07/unicode-compliant-and-open-source-licensed-hebrew-fonts/)

[http://wiki.jswindle.com/index.php/Fonts](http://wiki.jswindle.com/index.php/Fonts)
[http://wiki.jswindle.com/index.php/Winetricks](http://wiki.jswindle.com/index.php/Winetricks)

Bs'd

Before, I installed Arial, I think with one of the above pages.

But now, when I go to these pages: 

[http://wiki.jswindle.com/index.php/Fonts](http://wiki.jswindle.com/index.php/Fonts)
[http://wiki.jswindle.com/index.php/Winetricks](http://wiki.jswindle.com/index.php/Winetricks)

I only see white, nothing else.   

Is that the case with everyone who looks at that page, or is my filtered internet acting up?

---

