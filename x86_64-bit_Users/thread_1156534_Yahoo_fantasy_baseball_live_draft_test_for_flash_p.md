---
title: "Yahoo fantasy baseball live draft test for flash plugin"
date: 2009-05-11
forum: x86 64-bit Users
---

### Post by jeezum crow on 2009-05-11
[http://baseball.fantasysports.yahoo.com/b1/testdraft]("http://baseball.fantasysports.yahoo.com/b1/testdraft")

This test will crash firefox if you have the 64 bit plugin installed. if you are using the nspluginwrapper for the 32 bit version you should see a yellow "Test was successful" message if it works, if it doesn't work then it will continue to display "Connecting to server"

If anyone sees the yellow success message, I'd appreciate a post about how you did it.

---

### Post by Yellow Pasque on 2009-05-11
I had no problem with the site.
I'm using:
- a fresh install of Jaunty/9.04
- the Firefox 3.0.10 package from Ubuntu
- the latest 64-bit Flash plugin
- Open-source ATI (radeonhd) video driver

Why is FF crashing for you with the 64-bit plugin? (start it from the terminal to find out)
In my experience with the proprietary ATI drivers, I got a lot of segfaults in Flash (this was on Arch Linux, but still..)

---

### Post by sagasha on 2009-05-11
I passed the test. Follow the steps [here]("http://www.myscienceisbetter.info/2008/11/install-native-64bit-flash-player-10-on-linux.html")

---

### Post by jeezum crow on 2009-05-11
> **sagasha said:**
> I passed the test. Follow the steps [here]("http://www.myscienceisbetter.info/2008/11/install-native-64bit-flash-player-10-on-linux.html")
Tried your method. Had to create /usr/libs/mozilla/plugins to get it to install there. Still crashes firefox for me. On which version of Ubuntu does it work for you?

---

### Post by sagasha on 2009-05-11
> **jeezum crow said:**
> Tried your method. Had to create /usr/libs/mozilla/plugins to get it to install there. Still crashes firefox for me. On which version of Ubuntu does it work for you?

I'm using Ubuntu 9.04 64bit. When I finished those steps, firefox crashed for me until I re-booted.

---

### Post by jeezum crow on 2009-05-11
> **sagasha said:**
> I'm using Ubuntu 9.04 64bit. When I finished those steps, firefox crashed for me until I re-booted.
Wish I could say same. Kubuntu 9.04 64bit still crashes after reboot. Thanks, though.

---

### Post by sagasha on 2009-05-11
> **jeezum crow said:**
> Wish I could say same. Kubuntu 9.04 64bit still crashes after reboot. Thanks, though.

You could try Seamonkey. I have alpha 2 and it also works. You can download it [here]("http://www.seamonkey-project.org/releases/2.0a2") The 64 bit edition link is near bottom of page

---

### Post by jeezum crow on 2009-05-11
> **sagasha said:**
> You could try Seamonkey. I have alpha 2 and it also works. You can download it [here]("http://www.seamonkey-project.org/releases/2.0a2") The 64 bit edition link is near bottom of page
I think if one mozilla browser works, so will the other, and the other way around. I like the new seamonkey though. Thanks for the tip.

---

