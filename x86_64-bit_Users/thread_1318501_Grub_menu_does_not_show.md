---
title: "Grub menu does not show"
date: 2009-11-07
forum: x86 64-bit Users
---

### Post by voncloft on 2009-11-07
I installed Ubuntu 9.1 recently 64 bit.  When it boots it says "Loading grub" but it does not show a list.  It goes straight to the Ubuntu symbol.  Any help at all would be great.  I heard that it is no longer the menu.lst file that controls 64 bit booting if anyone could direct me to what file it is I believe its grub.cfg since it uses grub2 now - and how to fix the problem to show the menu that would be great.

---

### Post by oldfred on 2009-11-07
If you only have one operating system that is how grub2 boots - it boots directly to the only system installed unless you tap the edit out(space bar) s/b shift key  . Old grub used the escape key so that is another change.

The menu is now in grub.cfg and is not to be edited as it is dynamically created with every change and update. All edits would be overwritten. You actually edit separate files /etc/default/grub has the settings and /etc/grub.d/40_custom is the default place for manual edits that you previously would have added to the bottom of menu.lst. After every change you run sudo update-grub2 to create a new grub.cfg.

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by fmigpaulo on 2009-11-07
> **oldfred said:**
> The menu is now in grub.cfg and is not to be edited


How could i change the order of my operating systems? I used to switch them in menu.lst

Changing their order in /etc/default/grub would have the desired efect?

---

### Post by oldfred on 2009-11-08
If you are creating custom entries you can create any number of 2 digit & underscore files like /etc/grub.d/40_custom or like a 06_custom where the 06 is before the other numbers. So all the custom entries will be in the custom file number order in grub.cfg. Each file must be executable and you run update-grub2 to rewrite grub.cfg. I do not think there is an easy way to reorder the standard entries, unless you turn off osprober and do it all manually.

You can select boot order and other parameters in grub as you did at the top of the old menu.lst.

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html](http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html)

---

