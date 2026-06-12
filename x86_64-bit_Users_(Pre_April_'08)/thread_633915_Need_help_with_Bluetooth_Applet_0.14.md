---
title: "Need help with Bluetooth Applet 0.14"
date: 2007-12-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by poed on 2007-12-07
Hi all,

I'm an old Debian user who has finally taken the step into Ubuntu. By the looks of it, it's really nice! I do however need to be able to sync my phone via bluetooth. I have searched a lot to say the least, and are unable to find information regarding bonding with SonyEricsson T650i. Could it be that the phone is too new? Having read at [www.bluez.org](www.bluez.org) gives no clue either.

I would need help determining if it is a bug, not yet implemented or something else. I can sucessfully connect an old SE K750i, so I dont really believe something is malfunctioning. T650i works great in windows at work btw.

Please help!

TIA, Pontus

---

### Post by badrunner on 2007-12-07
> **poed said:**
> Hi all,

I'm an old Debian user who has finally taken the step into Ubuntu. By the looks of it, it's really nice! I do however need to be able to sync my phone via bluetooth. I have searched a lot to say the least, and are unable to find information regarding bonding with SonyEricsson T650i. Could it be that the phone is too new? Having read at [www.bluez.org]("http://www.bluez.org") gives no clue either.

I would need help determining if it is a bug, not yet implemented or something else. I can sucessfully connect an old SE K750i, so I dont really believe something is malfunctioning. T650i works great in windows at work btw.

Please help!

TIA, Pontus

Being able to connect via bluetooth and browse etc should just work. Its normally much easer to connect to the pc from the phone rather than the other way round (all you do is get a nice notification and put the pin in, easy). I think the default for bluetooth devices might not be discoverable, but right click the applet and set it in the preferences. Getting music/pictures between my phone and the pc is a doddle (although for file browsing you need to install gnome-vfs-obex i think its called), i think my phone even came out after feisty was released, but it still worked there fine. 

Syncing on the other hand is very likely not to work at all, there is a hell of a lot of development work going into getting decent sync support into the next ubuntu release, but realistically looking at what's out there now I doubt its going to be very good in 6 months time. I imagine it will be in the state that gtk-displayconfig was for gutsy, i.e. most of the pieces are there behind the scenes, but the frontend is worse than useless. Maybe not though, i would love to be proved wrong. Opensync seems to be the only solution at all to syncing phones and addressbook etc., but it doesnt seem to work with many yet, and its very black magic to set up.

---

### Post by poed on 2007-12-08
> **badrunner said:**
> Being able to connect via bluetooth and browse etc should just work. Its normally much easer to connect to the pc from the phone rather than the other way round (all you do is get a nice notification and put the pin in, easy). I think the default for bluetooth devices might not be discoverable, but right click the applet and set it in the preferences. Getting music/pictures between my phone and the pc is a doddle (although for file browsing you need to install gnome-vfs-obex i think its called), i think my phone even came out after feisty was released, but it still worked there fine. 

Syncing on the other hand is very likely not to work at all, there is a hell of a lot of development work going into getting decent sync support into the next ubuntu release, but realistically looking at what's out there now I doubt its going to be very good in 6 months time. I imagine it will be in the state that gtk-displayconfig was for gutsy, i.e. most of the pieces are there behind the scenes, but the frontend is worse than useless. Maybe not though, i would love to be proved wrong. Opensync seems to be the only solution at all to syncing phones and addressbook etc., but it doesnt seem to work with many yet, and its very black magic to set up.

Thanks for confirming the possible bug with the T650. I will mail [www.bluez.org](www.bluez.org) and then file a bug against Bluetooth Applet 0.14. Sad to hear about syncing though. Good news is that the effort now put in eventually will evolve into somthing great! :)

---

### Post by badrunner on 2007-12-09
I noticed today the bluetooth packages in gutsy arent the newest. If you search for the blueman project, they have a more up to date bluetooth stack in the repository. Also the gnome-phone-manager software shipped with gutsy is completely broken for all but a few nokia phones, it was fixed upstream quite a while before gutsy's release, but no update was made. There are packages for 0.4 in someones ppa which have been working great with my samsung phone, but i forget where i found them.

---

### Post by poed on 2007-12-10
Thanks! I didn't know that. I have by initiating the bond from the phone successfully bonded (I think), but browsing still does not work. I will try upgrading and see what happens.

Thanks again.

---

