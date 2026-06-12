---
title: "how to set-up dial-up connection?"
date: 2005-12-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by imacQ on 2005-12-25
imac g3 333mhz, ubuntu installation = all went well. can't seem to find how to set-up dial-up connection within the mac forum pages? would it be the same as page info for windows folks to set up modem, drivers, etc. 
this is the url for the windows people: [https://wiki.ubuntu.com/DialupModemHowto?action=show&redirect=SettingUpModems](https://wiki.ubuntu.com/DialupModemHowto?action=show&redirect=SettingUpModems)  i'm new to mac as well as linux. so if this is a dumb question...:confused:  sorry. 

something else maybe important, during the install i skiped "configure the network" is this what i need now? and if so can i put the install disk back in and just do that? but actually i remember i skiped it, because it said something about asking the admistrator for the ip address and i don't know what it is. how do i find out what it is, if i need to do that? 

any suggestions, url referals all greatly appreciated!

---

### Post by imacQ on 2005-12-26
well, i found what i thought i needed, set up connection going from system to preferences to network (i think that's how i got there) set up my internet connection phone #, user name, modem location, etc and set it as activate, but couldn't see any way to connect to internet and when i would go back to network dialog box, it was not activated.

so duh... i decided to reboot with phone line connected thinking it would maybe, somehow make a difference when booting. well the difference is i screwed things up somehow. now when it boots it gets to "configuring network interfaces" hangs there a couple of mins. then goes to "command line like" screen and goes through initial start-up processes again there until it reaches good ole "configuring network interfaces" hangs there forever i guess. 

going to bed... will see if anyone has suggestions in the morning. i'm thinking i should install again? damn :mad:

---

### Post by hentaidan on 2005-12-26
Try hitting Ctrl-C when you see the "Configuring network interfaces". You may need to do it again at "Waiting for network interfaces."

---

### Post by imacQ on 2005-12-26
thanks for suggestion. i have resolved the issue. i did install again, left network settings of install as "not configure now" upon completion of install when via menu to system/ administration/ network and set up dialup connection. then immediately used the chat to connect to ubuntu servers. i'm here now with firefox. don't have to click some icon to connect, but rather just open application and it does connecting "behind the scenes." now i'm a happy newbie! :)

---

### Post by gdgardnerw on 2005-12-28
I also have a iMac G3 333mHz and have been working for four hours trying to get the modem recognized. The system>administration>network seemed to set up the connection, but I can't see where to dial out! I tried the applications>internet>chat and it kept kicking out a series of errors about misspelling. I have even done the wvdial.config and pon through the terminal with no results per [https://wiki.ubuntu.com/DialupModemHowto?action=show&redirect=SettingUpModems](https://wiki.ubuntu.com/DialupModemHowto?action=show&redirect=SettingUpModems). My Firefox does not automatically connect in the background as imaQ's does.

I am an experienced mac user but brand new to linux.

---

### Post by imacQ on 2005-12-28
menu: system...administration...networking then highlight modem connection (assuming you've already configured it) and click activate. now you can close that window and you should be able to click on xchat or firefox and you'll be online. :cool:  if not something else is going on and i'm not linux savy enough to help you. good luck!

---

### Post by gdgardnerw on 2005-12-29
Thanks for your note. I did system>administration>networking and highlighted the modem connection and activated it. Firefox did not respond. I checked the phone line on another extension in the house and I got a dialtone. This tells me that the modem is not being accessed via GNOME.

As you indicate, there seems to be other issues involved. This is very frustrating. Thanks for your notes, imaQ. Anyone else out there have a suggestion? This issue is holding up work I need to get done! Right now I'm on my son's Windows XP machine (how embarrasing) to post this.

---

### Post by gdgardnerw on 2005-12-29
imaQ, you're a genius. I began to mull over what the "other issues" could be. I spent a few minutes reconfiguring the modem through the GNOME and here you have the results! I am posting this from the old lime iMac via Firefox! Thanks for your help! I really appreciate it!

---

### Post by autocrosser on 2006-01-01
Another way is to get Gnome PPP--you need to enable universe & multiverse repositories--I "dock" a link in my top bar--it allows more options than the network "control panel".

---

