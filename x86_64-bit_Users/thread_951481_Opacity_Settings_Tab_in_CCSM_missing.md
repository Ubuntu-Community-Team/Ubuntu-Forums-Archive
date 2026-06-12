---
title: "Opacity Settings Tab in CCSM missing?"
date: 2008-10-18
forum: x86 64-bit Users
---

### Post by Sir Rodness on 2008-10-18
The Opacity Setting tab in the General Options of CCSM is no longer there since I've updated to 64bit ubuntu 8.10. Has it been moved to a new location in CCSM? Maybe replaced by an alternate method? Is it something that is just being worked on currently? I've done some hunting around and can't seem to find an answer so I figured I'd bring it here hoping someone is able to shed some light on the situation for me.

---

### Post by CJ56 on 2008-10-18
I can't say for certain about 8.10 64-bit (I'm still using 8.04) but as a way round you could use the Configuration Editor (it's in the repositories if you haven't already got it)

Go to Configuration Editor > Apps > Compiz > General > Screen0 > Options > opacity_matches > Edit

In the Edit box I put the dropdown menus and so on -

Tooltip | Menu | PopupMenu | DropdownMenu

Then edit the opacity_values - I have mine at 95

Is this any help...?

---

### Post by Sir Rodness on 2008-10-18
> **CJ56 said:**
> I can't say for certain about 8.10 64-bit (I'm still using 8.04) but as a way round you could use the Configuration Editor (it's in the repositories if you haven't already got it)

Go to Configuration Editor > Apps > Compiz > General > Screen0 > Options > opacity_matches > Edit

In the Edit box I put the dropdown menus and so on -

Tooltip | Menu | PopupMenu | DropdownMenu

Then edit the opacity_values - I have mine at 95

Is this any help...?

Tried it out. The opacity_matches is no longer there. Maybe they simply deactivated it till the final release? *shrug*

---

### Post by Sir Rodness on 2008-10-24
Found it!
In Intrepid 8.10 to make my menus transparent the setting is now in the Opacity, Brightness and Saturation section in the Opacity Tab under Accessibility options of CCSM. It is no longer a tab in the general options.

Should of realized that earlier. Also there is no post on the Compiz site that mentions this. Did anyone see one there? Anyways...I'm happy again!

Cheers!

---

