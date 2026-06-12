---
title: "upgrade failed - packages broken - no X after reboot"
date: 2007-01-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by paradroid on 2007-01-23
Hi there,

I triggered an [COLOR="Blue"]**auto upgrade **[/COLOR]today. It indicated [COLOR="Blue"]**2 broken packages**[/COLOR] and hadn't succeed several times. After rebooting kubuntu, my X-System did not start and the the display freezed half black, half white.

I tried to fix this problem but apt-get told me to try [COLOR="Blue"]**apt-get -f install**[/COLOR]. This didn't solf the problem. It said my [COLOR="SeaGreen"]**libc6-[COLOR="Red"]2.4[/COLOR]-<whatever>-1ubuntu12-<whatever>.deb**[/COLOR] need [COLOR="Red"]**to be deleted**[/COLOR].  Did so: [COLOR="Blue"]**no effect**[/COLOR]. (I have a dual boot system. This post comes from my Redmond install. Sorry for not being more precize in file names, now.)

I think the problem is, that I have a [COLOR="Red"]**2.6**[/COLOR] [COLOR="Blue"]**kernel amd64**[/COLOR] and some wrong dependences where gathered from the ubuntu servers.

It'll be cool te get help with this issue ](*,)

Thanks guys!

---

### Post by pay on 2007-01-23
Apt doesn't install the wrong dependencies... but something can go wrong when apt is running (like a crash). Your problem doesn't sound like something to do with incorrect packages anyway. It seems like your video driver isn't setup or your xorg.conf is wrong. When you boot it does it come up with a screen to view the X server output (or something like that)? Try reinstalling your video drivers.

---

### Post by Shelnutt2 on 2007-01-23
Same issue here. Last night I had some auto updates, most were beryl updates, and then this morning I restarted and the xserver doesn't load right. All I get is a blank black screen. I tried reconfiguring the xserver but it was a no go. I tried both the frglx and mesa driver.

---

### Post by paradroid on 2007-01-24
thank you all for helping!!!

I figured out the problem.

There was a package dependency with libc6 and libpthread20. I purged libpthread20 (remove surely work as well). Triggered apt -f install as wished. Had no errors and installed libpthread20 again.

=D> 

Maybe my post title caused some misunderstandings. I apologize this.

Cheers

---

### Post by neumeka on 2007-01-24
I just want to confirm paradroid's results:
I am running linux 2.6.17-10-386 and ubuntu edgy, and an nvidia card.  I had an update for libc6 and another package that would not install.  I restarted and X broke.  I uninstalled libpthread20, reinstalled my video divers (via envy).  I could then install the broken packages.  I restarted, everything was fine, so I reinstalled libpthread20.  Everything is fine after a reboot.  Thanks paradroid.  Don't know how you figured that fix out, but it worked.

---

### Post by kuja on 2007-01-24
Looks like the libc6 problem made headlines, look at the ubuntuforums.org front page, in the green box.

---

### Post by paradroid on 2007-01-25
today I received another auto upgrade of libc6.

After reboot no problems! :D 

Thanks to the little helpers !!!

ps: neumeka
I have a similar config like you. Same kernel, nvidia driver and libptread20 installed. Cheers.

---

