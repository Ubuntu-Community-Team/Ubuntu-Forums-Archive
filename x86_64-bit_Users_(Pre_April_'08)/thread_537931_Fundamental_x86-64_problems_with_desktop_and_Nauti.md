---
title: "Fundamental x86-64 problems with desktop and Nautilus"
date: 2007-08-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by monsieurrigsby on 2007-08-29
All,

   Couldn't find any other relevant thread and was surprised, since I seem to be having some fundamental issues with basic GUI desktop / Nautilus stuff. 

Fairly frequently (once every few days maybe, but not predictable), I get "stuck" in the middle of a drag and drop operation e.g. move desktop icon, resize window, resize column in File Browser. The cursor gets stuck in its particular icon (resize or whatever) and everything locks (no Alt-Tab or anything else). The only way I've found to get out is to bring up a virtual console (Ctrl-Alt-F1), log in and kill any running nautilus processes (another one seems to respawn automatically normally).

Probably independently, I also had an issue where OpenOffice (I assume) crashed the keyboard buffer - I just got continual "e" characters, whatever window I was in and whatever session I started (e.g. console). Had to hard reboot. Again, surprising since vanilla OpenOffice. I'm assuming this just a one-off but the first problem recurs all the time.

I haven't seen these problems in 32-bit Ubuntu (though admittedly, I haven't run this on the same PC yet). I have a fairly vanilla Feisty installation on an Acer Aspire 5100 laptop (only added standard stuff such as totem-xine, etc., all from repos).

Has anyone experienced similar and, if so, is this a 64-bit Ubuntu only issue (or maybe Feisty only?). Search of Launchpad didn't throw anything up I could see...

Any help appreciated or I'm going to revert to 32-bit and I don't want to wimp out :-(

Cheers,
Stuart

---

### Post by Cappy on 2007-08-29
I had this same bug and as far as I know it is fixed:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/41301](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/41301)

You should try adding
```
noapic pci=off
```
onto your /boot/grub/menu.lst

If you need further instructions on adding boot parameters look here:
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

---

### Post by meho_r on 2007-08-29
Well, I had same issue from time to time, but not necessarily when drag-and-drop something. Sometimes it occurs when press a button (i.e. Send/Recieve in Evolution). I suspected that Compiz Fusion has something to do with it. I'll try "noapic pci=off". Thanks :)

---

### Post by monsieurrigsby on 2007-08-30
OK, thanks for the advice.

Note that bug 41301 mentioned is definitely not the same, because that talks about Alt-Tab being usable. I occasionally have problems when the focused window (normally Firefox) gets stuck with the hand icon cursor, but I can get out of this with Alt-Tab (so maybe 41301 is still live in Feisty as well). The other problem I have is significantly more serious.

Anyway, I will try disabling APIC and PCI devices as mentioned (guess there are no issues with latter on a laptop since no PCI devices installed). As I understand, APIC is just an alternative (advanced) interrupt handler and there are no real repercussions in disabling it (unlike disabling APCI which would affect all laptop power mgmt stuff).

[ Sorry, like to know *why* I'm doing stuff :-) ]

Cheers,
MonsieurRigsby

P.S. Oh, and "refreshing" X (Ctrl-Alt-F1, Ctrl-Alt-F7) doesn't sort the problem, as also mentioned in bug 41301.

---

### Post by monsieurrigsby on 2007-08-30
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/114365](https://bugs.launchpad.net/ubuntu/+bug/114365) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Doh :oops:

Didn't read the 41301 bug too fully, now did I. Bug 114365 is mentioned and that *is* the problem I'm having: [https://bugs.launchpad.net/ubuntu/+bug/114365](https://bugs.launchpad.net/ubuntu/+bug/114365)

I'll add my info to the bug.

MonsieurRigsby out.

---

