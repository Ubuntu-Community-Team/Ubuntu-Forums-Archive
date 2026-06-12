---
title: "Removing Microsoft Office in WINE"
date: 2015-04-10
forum: Wine
---

### Post by llmunro on 2015-04-10
Hi Forum,

I tried recently to install MS Office via WINE on Ubuntu 14.04.  I think I probably should have done this through PlayOnLinux, as although the install went fine, certain vital feature (Save, etc.) won't work.  I'd like to uninstall it, but I'm having trouble.  When I open Uninstall Wine Software, I see a list of the programs its running, including MS Office.  I highlight it, click remove, and verify that I do indeed wish to remove it.  I then get a message from MS Office that the program could not be uninstalled completely.  What's the solution here?

Thanks so much.

Best,
Lisa

---

### Post by user_of_gnomes on 2015-04-12
Can't you manually remove the files belonging to Microsoft Office from C:\program files?

You should consider [using prefixes]("http://www.wine-wiki.org/index.php/WINEPREFIX") when installing Wine programs, it'll make keeping your Wine installation clean easier and safer in my opinion.

---

### Post by llmunro on 2015-04-24
Hi,

Sorry for my late reply--I somehow didn't see your message! Thank you for the help!

Just to clarify: is removing the C:\ program files the same as deleting the Microsoft Office folder in .wine?  

How does one use a prefix when  installing WINE programs? 

Thanks so much-apologies for not having responded sooner.

Best,
Lisa

---

### Post by user_of_gnomes on 2015-04-25
> **llmunro said:**
> Hi,
Just to clarify: is removing the C:\ program files the same as deleting the Microsoft Office folder in .wine?  


Don't delete C:\program files! 
I meant the folder C:\program files\**Microsoft Office**

It isn't entirely the same as removing the program through the uninstaller as several registry entries such as file association and start-up entries remain. You could delete those manually if you wanted (and know how) by running [regedit]("http://wiki.winehq.org/regedit").
You will most likely also need to delete the Microsoft Office related-contents of C:\users\*user_name*\application data

> **llmunro said:**
> Hi,
How does one use a prefix when installing WINE programs? 


I hope this still applies, I haven't used Wine since 1.4 or 1.5.

If you were to install Microsoft Office 32-bit creating a prefix would look like this (I am going to assume you have basic knowledge of the terminal): 

env WINEARCH=wine32 WINEPREFIX=$HOME/.mso wine wincfg

That will create the hidden folder mso in your home directory and configure a 32-bit wine prefix (permanent environment).

Quit the winecfg program and use the terminal to navigate to the folder (or device) where the setup program for MSO is located. (e.g. **cd ~/Downloads/mso2007/**
(I am not sure what the setup executable for MSO is called but I am going to assume it is setup.exe)

Type env WINEPREFIX=$HOME/.mso wine setup.exe 

Proceed as usual by following the setup program instructions.

Now everytime you want to launch a program you'll have to type (keep in mind, Linux is case sensitive so use tab to autocomplete)

 cd ~/.mso/drive_c/"program files"/microsoft office/
env WINEPREFIX=$HOME/.mso wine winword.exe 
(or excel.exe, pp.exe, et cetera)

Alternatively, you could create a shortcut. [I once wrote a guide ]("https://gamefixes.wordpress.com/category/developer/paradox-development-studio/hearts-of-iron-iii/")on how to get a videogame to work in Wine. You can roughly apply the same instructions to Microsoft Office. Step 7 instructs you on how to create a shortcut. Make sure you replace the variables there with the relevant lines for MSO, of course.

The thing is that when you create a prefix, you can just toss out the prefix when you want to get rid of the program (or think the prefix might be infected by Windows malware) and your other programs (assuming they are in seperate prefixes) will remain unharmed ... Might seem complex but if you work with Wine a lot, it is something you should absolutely get to know.

If something isn't clear, let me know and I'll try to help but it has been a while for me!

---

