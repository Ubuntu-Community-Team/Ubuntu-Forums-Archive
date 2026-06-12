---
title: "i turned off graphical boot then i had a problem..."
date: 2008-04-26
forum: x86 64-bit Users
---

### Post by chrisx16x2008 on 2008-04-26
i turned off graphical boot cuz i heard it would make my computer faster and as soon as i did my scrren went to black with white text and restarted my system.  now when i wanna turn on my computer it says no resume image, booting normally... and it doesnt change from tht screen. help please

---

### Post by esdaniel on 2008-04-26
Try Ctrl-Alt-F7, this should take you from TTY1 (Ctrl-Alt-F1) to TTY7 (the default terminal for graphical display).

---

### Post by chrisx16x2008 on 2008-04-26
i tried tht nothing happened

---

### Post by esdaniel on 2008-04-26
Does the boot sequence play out i.e. after seeing 'booting normally' do you get left with a shell prompt?  Can you login in to shell?

If so, you can start the desktop manager by from the command line, if not then it would be best to start in recovery mode, go to shell prompt, log in and change back what you previously edited.

---

### Post by chrisx16x2008 on 2008-04-26
no it says no resume image, booting normally... then after a few spaces it says Kernel Alive

---

### Post by chrisx16x2008 on 2008-04-26
also i kinda dont even think it is the graphical boot thats the problem cuz what happens is i turn the computer on it shows the load screen then goes to that text tht says no resume iamge....Kernel alive. i also changed the graphical boot by going to administration-> "something" and i dont know how to turn it back on through recovery

---

### Post by esdaniel on 2008-04-28
> **chrisx16x2008 said:**
> no it says no resume image, booting normally... then after a few spaces it says Kernel Alive

Sorry for delay getting back to you... if you see Kernel Alive I'm hoping you can also see the text login prompt, can you see something like:

*YourHostName Login:*

(PS. Try hitting the return key to see if a prompt does appear)

If so, then you can login with your user ID and password then launch your desktop manager as per earlier suggestions, if not then it's a case of going into recovery mode and starting your desktop manager from there.

If this does not prevail and as you're still able to post here I've assumed the computer on which you're doing that may well be near the one you're having problems with then I'd recommend  the IRC channel to get some realtime help/diagnosis/support:
[https://help.ubuntu.com/community/InternetRelayChat](https://help.ubuntu.com/community/InternetRelayChat)

Let us know how you get on either way and watch this thread in case other members have more advice to share.

One other thought crossed my mind on a tangent - while highly unlikely if you set Ubuntu to 'server mode' by accident - if so then that is a whole other kettle of fish that requires you to login and enter the following: [I]sudo apt-get install ubuntu-desktop
[/I]This is of course on the basis that you can login in either normal or recovery mode.

---

### Post by chrisx16x2008 on 2008-04-28
i know how to get in recovery but how would i start dekstop manager? and what wou;d i do from there?

---

### Post by esdaniel on 2008-04-29
To launch (restart) the desktop manager code:
[I]sudo /etc/init.d/gdm restart

[/I]If you're unable to start GDM then it might be best to reinstall the desktop:
*sudo apt-get install ubuntu-desktop*

Then use the following to launch, you might need to press Ctrl-Alt-F7 to access the login screen:
*sudo /etc/init.d/gdm start*

---

