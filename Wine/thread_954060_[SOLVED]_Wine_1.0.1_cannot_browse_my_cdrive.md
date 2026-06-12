---
title: "[SOLVED] Wine 1.0.1 cannot browse my c:drive"
date: 2008-10-20
forum: Wine
---

### Post by famous3warriors on 2008-10-20
went to applications-wine-browse c:\drive to install my mfc42.dll to load age of mythology and it would not let me. I just installed intrepid on my fairly new notebook and It will not work. Please help.  Thanks allot for you help.

---

### Post by hikaricore on 2008-10-21
err try running:

> nautilus ~/.wine/drive_c

If I understand what you mean correctly, otherwise please describe the problem in further detail.

---

### Post by famous3warriors on 2008-10-21
Thanks a lot hikaricore I really do appreciate it.  Is this going to be the norm for now on.  I will mark this as solved.

---

### Post by YokoZar on 2008-10-22
Could you describe the behavior again please?

Are you clicking Browse C:\ Drive and nothing is happening?

---

### Post by cmonopoly72 on 2008-10-22
Clicking on the Menu item "Browse C:\ Drive" doesn't work for me either. Using Nautilus itself and traveling to the folder or using the command does work, though.

edit:   Looking in .xsession-errors shows the following:
                  Error showing url: Error stating file '/home/cmonopoly72/$HOME/.wine/dosdevices/c:': No such file or directory

---

### Post by YokoZar on 2008-10-26
Ok, I've confirmed the bug...one fix is to replace $HOME/.wine with just .wine

But I'm a bit confused as to why this happens.  It seems like the launcher is assuming things will be in the home directory already, or no longer understands that $HOME is an absolute path.

---

### Post by kvk on 2008-10-26
Where are you modifying "$HOME/.wine into simply .wine?

I've got 1.01 running on Ibex with similar issues, and maybe they are all stemming from this same issue:


1. No browsing of c:/
2. No MS equation editor extension in Word
3. Attempting to add MathType to Word usually freezes, requiring Force Quit, and when it does function, Word will no longer Save.


```
arctos@arctos:~/Desktop$ wine MTW6.0c.exe
fixme:ole:CoInitializeSecurity (0x413ea8,-1,(nil),(nil),1,3,(nil),72,(nil)) - stub!
err:ole:CoGetClassObject class {24e669e1-e90f-4595-a012-b0fd3ccc5c5a} not registered
err:ole:CoGetClassObject no class object {24e669e1-e90f-4595-a012-b0fd3ccc5c5a} could be created for context 0x1
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:ole:CoGetCallContext ({0000013e-0000-0000-c000-000000000046}, 0x7e37f884): stub
fixme:ole:CoGetCallContext ({0000013e-0000-0000-c000-000000000046}, 0x7e37f86c): stub
fixme:ole:CoGetCallContext ({0000013e-0000-0000-c000-000000000046}, 0x7e37f86c): stub
fixme:ole:CoGetCallContext ({0000013e-0000-0000-c000-000000000046}, 0x7e37f86c): stub

fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
etc.

fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
etc.
```

Other applications under Office 2003 may have similar issues- I haven't tried them yet. I do have MathType 6 working on Office 2003 on an older Windows box I have running, so there is no inherent incompatibility issue there.

THank you!!

---

### Post by b3n0 on 2008-11-22
> **YokoZar said:**
> Ok, I've confirmed the bug...one fix is to replace $HOME/.wine with just .wine

But I'm a bit confused as to why this happens.  It seems like the launcher is assuming things will be in the home directory already, or no longer understands that $HOME is an absolute path.

Hey I'm running Wine 1.1.8. Where do I change this code? Am I editing a shortcut? Excuse the newbie-ness.

Thanks

---

### Post by klemperal on 2008-12-10
How did this end up being resolved?  I'm still not sure what the solution is.

---

### Post by hikaricore on 2008-12-10
> **klemperal said:**
> How did this end up being resolved?  I'm still not sure what the solution is.

Read the thread again.  It's a known bug and there are several solutions to it.

---

### Post by b3n0 on 2008-12-11
This is what I ended up doing.
System > administration > start menu. I found the wine menu on the left and selected that, then selected 'browse c drive' in the centre of the window, think there was a button off to the right of the window, edit or configure, something like that. I changed what was in the command box to...

```
nautilus .wine
```

I'm doing this off the top of my head, as I am on the train and typing this out on my phone. 

Hope this helps.

---

### Post by semi_fiction on 2009-01-03
Try upgrading to the latest beta package (1.1.12).
I did and I was then able to browse my virtual C:/ drive.

---

### Post by a_pirard on 2009-03-28
> **hikaricore said:**
> err try running:

nautilus ~/.wine/drive_c 



The C: drive is not ~/.wine/drive_c
but ~/.wine/dosdevices/c:

André.

---

### Post by dinesh301 on 2011-04-17
I was facing the same problem. Visit [http://thesurmise.blogspot.com/2011/04/ubuntu-wine-c-drive-problem.html](http://thesurmise.blogspot.com/2011/04/ubuntu-wine-c-drive-problem.html) for assistance.

---

