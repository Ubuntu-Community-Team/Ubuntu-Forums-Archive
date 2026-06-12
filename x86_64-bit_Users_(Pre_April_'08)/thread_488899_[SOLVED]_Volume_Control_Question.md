---
title: "[SOLVED] Volume Control Question"
date: 2007-06-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by crjackson on 2007-06-30
Just what does the volume control on the system tray do?

It recognizes my Logitech media/internet keyboard.  When I use the volume keys a nice little gui pops up and shows a volume progress bar.  When I press the mute, it shows to be muted.  However it doesn't actually lower the volume or mute anything that I can tell.

When I'm using a music player or playing a movie I have to use the controls of that particular player to raise/lower/mute the volume.

Just what does this "Master" control actually do?

---

### Post by skyhook19 on 2007-07-01
I noticed that is also happening to me.  I installed a PCI soundcard to replace to integrated sound.  I can't remember if this was a problem before that or not,

---

### Post by litemotiv on 2007-07-01
the master volume control can sometimes attach to the 'wrong' audio port by default, e.g. the headphones output when you are using the main stereo out, or the volume of an attached webcam. you can right-click on it and check the advanced settings to be sure it's configured to use the right ports.

---

### Post by crjackson on 2007-07-01
> **litemotiv said:**
> the master volume control can sometimes attach to the 'wrong' audio port by default, e.g. the headphones output when you are using the main stereo out, or the volume of an attached webcam. you can right-click on it and check the advanced settings to be sure it's configured to use the right ports.

okay, i'll try to attach it to a different port and see what happens.

---

### Post by crjackson on 2007-07-01
> **litemotiv said:**
> the master volume control can sometimes attach to the 'wrong' audio port by default, e.g. the headphones output when you are using the main stereo out, or the volume of an attached webcam. you can right-click on it and check the advanced settings to be sure it's configured to use the right ports.

Okay, that fixed the volume icon controlling the sound levels, now how do I get the keyboard keys to lock onto that volume slider?

---

### Post by crjackson on 2007-07-02
Anyone?

---

### Post by crjackson on 2007-07-04
Wow, I guess this one can't be fixed.

Thanks for looking.

---

### Post by crjackson on 2007-07-04
So no one has a clue.  I'm disappointed and surprised.

---

### Post by crjackson on 2007-07-04
Well I figured it out.  Thanks for the help.

---

### Post by evadwolrab on 2007-07-06
[B][FONT="Arial"]> **crjackson said:**
> Well I figured it out.  Thanks for the help.
Can you please post how you fixed it? I've just switched to ubuntu and have the same problem. I've got the right audio channel selected and the taskbar slider works. I just can't get my keyboard to do it.

Edit: I've just realised I'm the 64-bit forum but I imagine it'll have the same solution. I've got a 64bit processor but I'm running 32-bit Feisty.
[/FONT][/B]

---

### Post by crjackson on 2007-07-06
> **evadwolrab said:**
> [B][FONT="Arial"]
Can you please post how you fixed it? I've just switched to ubuntu and have the same problem. I've got the right audio channel selected and the taskbar slider works. I just can't get my keyboard to do it.

Edit: I've just realised I'm the 64-bit forum but I imagine it'll have the same solution. I've got a 64bit processor but I'm running 32-bit Feisty.
[/FONT][/B]

I'm in windows right now doing some video editing so I'll have to work from memory.

Right click on the applications menu button.  Select edit menus.  Find the control panel applett and put a check mark in the box to activate it.  Go to the control panel.  Click on sound.  At the bottom of the settings page, it comes right out and asks you which volume slider you want to associate with the keyboard buttons.
Select the correct one, close and your all done...

Hope this helps you.

---

### Post by evadwolrab on 2007-07-06
> **crjackson said:**
> I'm in windows right now doing some video editing so I'll have to work from memory.

Right click on the applications menu button.  Select edit menus.  Find the control panel applett and put a check mark in the box to activate it.  Go to the control panel.  Click on sound.  At the bottom of the settings page, it comes right out and asks you which volume slider you want to associate with the keyboard buttons.
Select the correct one, close and your all done...

Hope this helps you.[B][FONT="Arial"]
Perfect, thankyou!

Does anyone have play/skip etc buttons on their keyboard? I´ve set up the shortcuts for them but Banshee doesn´t seem to recognise them. I know progs like songbird can most likely see to all my podcast needs so does anyone know if any of the modern media players that can do podcasts also recognise media keyboard buttons?

Or do I just need to find a way to get Banshee to recognise them?[/FONT][/B]

---

### Post by crjackson on 2007-07-06
> **evadwolrab said:**
> [B][FONT="Arial"]
Perfect, thankyou!

Does anyone have play/skip etc buttons on their keyboard? I´ve set up the shortcuts for them but Banshee doesn´t seem to recognise them. I know progs like songbird can most likely see to all my podcast needs so does anyone know if any of the modern media players that can do podcasts also recognise media keyboard buttons?

Or do I just need to find a way to get Banshee to recognise them?[/FONT][/B]

Yeah, it was so simple I couldn't believe no one could help me.  I don't know about the skip/play buttons.  I'll have to check it out later when I get a chance.

---

### Post by mgmiller on 2007-07-09
> Right click on the applications menu button. Select edit menus. Find the control panel applett and put a check mark in the box to activate it. Go to the control panel. Click on sound. At the bottom of the settings page, it comes right out and asks you which volume slider you want to associate with the keyboard buttons.
Select the correct one, close and your all done...

Thank you.... This just started happening to me for no reason.  My keyboard buttons always worked properly before the last reboot, suddenly, they were controlling only the surround channel.  Your tip fixed it.

---

### Post by crjackson on 2007-07-09
> **mgmiller said:**
> Thank you.... This just started happening to me for no reason.  My keyboard buttons always worked properly before the last reboot, suddenly, they were controlling only the surround channel.  Your tip fixed it.

Great.  It's good to see this information is helping people.

---

