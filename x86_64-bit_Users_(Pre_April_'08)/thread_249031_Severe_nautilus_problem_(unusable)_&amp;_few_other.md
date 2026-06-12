---
title: "Severe nautilus problem (unusable) &amp; few other smaller issues"
date: 2006-09-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by wgaprotest on 2006-09-02
K, I must say I gave up on Ubuntu for my 64-bit setup here, and struggled for weeks with Mandriva (some said I was too patient) and now I'm back. This time around the actual install was a bit scary (it kept on saying there were disk problems on anther key windows partition, so I'd stop, check, couldn't find any...finally told it to ignore and continue installation--no probs) I did get it going here.

I've only had the install for a few days, and am proud to say I've got sound, network (with samba), and a brother mfc210 printing locally (not for network computers yet, faxing, or scanning-later). The last bit really took some doing, but the documentation on this site really helped force the 32-bit architecture apps in.

Biggest problem: Nautilus has become completely unusuable, and I don't dare to open it or else a lot of things slow down horribly (like firefox). I don't know how to kill it completely, as the 'sudo killall nautilus' command line I read about didn't work for me. Everytime I try to force it to quit from the gui it just pops right back up again. Help!!! What's an OS witout a working filesystem? The only thing that will kill it is warm rebooting, as I can't even exit/restart properly whenever nautilus is misbehaving in this way.

This problem started when I was copying some music files from a samba drive on son's XP machine to my home music folder. Copying worked, yet when I try playing some in amarok, I *sometimes* get a 'could not launch mail client" and something about kmail, which I didn't even have installed at first (I do now just to see if the error would go away). Another time I can play the same song without the mail error message, but then a different song gives me the message...

Other smaller problems: every time I reboot my net access won't work until I go into shell and type 'sudo dhclient'. Fairly quick workaround/fix, but annoying that I have to do this every time. Isn't it supposed to restart during boot/init process? Like when it's booting and all the processes get loaded?

Nor does the network let go during proper shutdown. I'll have to get some more information as to the processes that aren't shutting down, 

I think I need to edit boot/init, but I'm nervous, as I'm still a newbie with linux, and while I was doing this kinda stuff (fooling windows and such with 2 drives, editing grub's menu.list, etc., with mandriva, it only worked for awhile, and then started 'not working' as usual. Yes, I'm still adjusting to ubuntu...

Please! I don't want my ubuntu falling apart, too. I need to have this nautilus problem fixed asap.

Thanks in advance...

---

### Post by Mongoose on 2006-09-02
Sounds like issues with the install.  You're using LTS installed from the cd, or did you try updating over an exisiting install?  Also it might help to list what kind of machine you have such as processor and motherboard at least.

---

### Post by wgaprotest on 2006-09-02
Sorry, the clean install from the cd went pretty well actually (besides that one bump that didn't seem to affect anything) and everything was essentially working as it should with dapper dan for the amd 64.The printer was detected, but it was too new to have drivers and stuff with the distro, so I knew I'd have to install drivers after the install. And yes, I made sure to update everything right after the install a few days ago -- but the nautilus problem only happened all of a sudden last night. 

A brief list of my essential hardware is as follows:
Asus A8N32-sli mobo with 2 onboard nics, 7.1 sound, and nvidia nforce 4 chipset
AMD 64 x2 3800+ dual core CPU, 2G ram, 300G maxtor sata hdd (for win xp MCE) & 300G Samsung ide hdd (for my linux distros)
thermaltake mozart case with antec 2 550W PS
1 XFX GeForce 7800GT PCIE video card, nvidia chipset, 256 memory, with TV-out, connected via DVI cable to acer 22" wide screen LCD pannel, 1650 x 1050 res.
1 powercolour PCIE x1 tuner, run by ati theatre 550 pro (only works with win)
1 hauppauge 250 tuner, wintv-pvr (which I intend to get working for linux via mythtv, but later, after I get everything else working the way I want)
LG 4176 cd/DVD-writer, floppy, 7.1 creative inspire speakers, normal keyboard, usb mouse, the brother mfc210 usb printer

I think that's everything. I'm switching (for now) between the win mce os and linux distros by going into bios and switching between the different hdds, although grub on hda1 does have listings for ubuntu, mandriva, and the win mce. Remember that, when working just with mce & mandriva, I had fooled windows to think it was booting from 1st hdd (when booting from samsung ide), and it had worked beautifully -- the first couple of times I  used the mce option from grub, then it would eventually stop working and the "root noverify" line in menu.lst would mysteriously disappear, along with the mapping edits to menu.lst. I'd end up seeing the menu.lst entry on the monitor and there it would stop. But like I said: the booting from different drives is another issue I had solved, and so will be able to do again later.

The main severe problem is the very recent nautilus-becoming unusable. How to kill the processes when it wants to hang my ubuntu system? Less essentially: How to edit my boot/init to make sure dhclient gets activated at boottime? and actually shut down at system shutdown?

---

