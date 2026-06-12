---
title: "WINE - Programs doesn't uninstall"
date: 2009-10-19
forum: x86 64-bit Users
---

### Post by Gosport on 2009-10-19
I have Wine installed and I tried to run Itunes (Not a good Idea.  Screen go black etc.) because the wife bought an 5th gen Ipod Nano.  After much frustration I just want to uninstall the program but it wont leave!  I used the options to uninstall and then when it is finished the last window informs me that I have just installed the program!  (I have also tried to install an older version of Itunes, after the uninstall, and I am informed that a newer version is already installed.  Point being that not only does is still look installed to me the computer thinks it is too)

Why wont this just go away?  I'm starting to hate Apple for making this hard, and getting frustrated with Wine for not considering the removal of programs.  (Are you sure they don't call it Whine?)

Also, Gtkpod doesn't support the 5th generation Nano.  Should I return the thing or just wait six months?

---

### Post by Gosport on 2009-10-20
Does anyone have a good link that explains how to remove/clean up programs that run under Wine?

---

### Post by Gosport on 2009-10-21
bump

---

### Post by Rizlaw on 2009-10-24
You can try installing "ccleaner" in Wine to try and clean up any residual registry data from your unsuccessful uninstall. It works for me in Wine. Ccleaner can uninstall Windows programs and perform modest registry cleaning. It can be found at [www.majorgeeks.com](www.majorgeeks.com). I suggest you download the "slim" version without the Yahoo toolbar.

You might also consider "Revo Uninstaller", although I haven't tested it myself in Wine, it appears to be more heavy duty. [http://www.revouninstaller.com/](http://www.revouninstaller.com/)

If all else fails you can remove Wine completely, including all config files, etc., using Synaptic Package Manager or from the command line: 

```
sudo aptitude purge wine
```

Then reinstall Wine and any Windows programs you need.

PS: Wine currently can't remove the Windows program entry from the Ubuntu "APPLICATIONS > WINE > PROGRAMS > "app name" after a successful uninstall. To do that you must manually delete the entry by editing the Ubuntu Main Menu. Go to PREFERENCES > MAIN MENU > WINE > PROGRAMS. Then click/highlight the program entry you want to remove and click the "Delete" button to remove the entry.

---

### Post by Gosport on 2009-10-26
Thank you Rizlaw for your complete and well informed answer!

---

### Post by mikejonesey on 2009-10-26
iv'e used ccleaner before on wine and it works well but sometimes if iv'e totaly broke it i just remove the .wine folder (this does not remove wine just all installed apps), you will have to install all programs again but wine remains same as b4.

---

### Post by Gosport on 2009-10-26
> **mikejonesey said:**
> iv'e used ccleaner before on wine and it works well but sometimes if iv'e totaly broke it i just remove the .wine folder (this does not remove wine just all installed apps), you will have to install all programs again but wine remains same as b4.

One issue that I have had is the fact that I was running Picasa 3.5's facial recognition software.  I had been running the thing for days!  I'd like to know where Picasa stores the name information so that I can restore that portion after I wipe everything out and start fresh.

---

### Post by Rizlaw on 2009-10-26
> **Gosport said:**
> One issue that I have had is the fact that I was running Picasa 3.5's facial recognition software.  I had been running the thing for days!  I'd like to know where Picasa stores the name information so that I can restore that portion after I wipe everything out and start fresh.

Gosport,

Have you tried opening Nautilus in your "home" folder and typing "Ctl + H" keys? This will unhide your hidden "." folders, which will include ".wine" and probably something like ".picasa". I don't use Picasa but I'm guessing you have a .picasa folder with the info you seek inside.

You can look in:

/home/username

or

/home/username/.wine/drive_c/Program Files

for your Picasa folder.

---

### Post by Gosport on 2009-10-26
Yes, and just replacing the Picasa file doesn't seem to do the trick.  They seem to be hidden someplace else.

---

### Post by mikejonesey on 2009-10-26
never used piasa but have you tried the reg?

---

### Post by Gosport on 2009-10-27
> **mikejonesey said:**
> never used piasa but have you tried the reg?


What is "the reg"?

---

### Post by Slim Odds on 2009-10-27
> **Gosport said:**
> What is "the reg"?

The registry

---

