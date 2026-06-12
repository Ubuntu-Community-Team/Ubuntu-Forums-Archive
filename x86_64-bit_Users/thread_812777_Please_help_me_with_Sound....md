---
title: "Please help me with Sound..."
date: 2008-05-30
forum: x86 64-bit Users
---

### Post by Ilias83 on 2008-05-30
Hello,
I'm new on Ubuntu.
I have tried to work Ubuntu 7.10 in the past.
I removed them but I loved them so now I have Ubuntu 8.04
But now I have a lot of problems with sound.
Firstly I had no sound at all.
I fixed the problem by selecting "Multichannel Playback" in drop down menus on Sound Preferences (System->Preferences->Sound)
Now the problem is that I have no sound on firefox on any flash video.
I've tried a lo of things but nothing worked.
I finally got sound by removing swfdec-mozilla and installing flashplugin-nonfree.
But after a while sound stopped again although I haven't changed something.
I have noticed that I have no system sounds like login logout.
Is there something to try?

CPU: AMD 64bit X2 4200+
Sound Card: SoundBlaster Live! 5.1

Thanks in advance...

---

### Post by pixel :-) on 2008-05-30
This is a bug in flash.When this happens try,reloading the page.If this doesn't work,go in tools-->add-ons and deactivate,then reactivate flash,then reload the page.Some times there will be sound and no image, some other times just a white scare and nothing happens.

For system sounds,are you sure you didn't mess with the setting when you where trying to fix your problem?

If you are very new in linux i would recommend installing 32bits.Of course since you are already on it just stay there.More people are using it,comme back in 64 later.They are some minor quirks that can put off newbies.

---

### Post by Ilias83 on 2008-05-30
I tried to solve the problem by deactivating and reactivating flash plugin but nothing happens.
For System Sounds:
From Menu Systems->Preferences->Sound on Sounds tab when pressing the Play button to hear Login or Logout sound nothing happens.

The bug you mentioned is only on 64bit OS?
Thnsk for your help

---

### Post by Ilias83 on 2008-06-02
I solved the problem with Login and Logout sound.
It was PulseAudio.
It was using the on-board sound card as default.
I changed it and now I have sound.
No sound in firefox though.

---

### Post by Ilias83 on 2008-06-02
And finally I solved the problem with audio in firefox.
Right click on applications and then "Edit Menus"
I checked "PulseAudio Device Chooser" so it appears on Applications-> Sound & Video menu.
After that when you click on "PulseAudio Device Chooser" you'll have an icon next to user name on the panel.Click and choose "Configure Local Sound Server"
On the first tab (Network Access) enable the first 3 options
On the second tab Enable the first 2 options.
Thats it I got sound on firefox.

---

