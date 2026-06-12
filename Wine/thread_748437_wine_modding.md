---
title: "wine modding"
date: 2008-04-07
forum: Wine
---

### Post by gaurdianAQ on 2008-04-07
I read something that you can use windows DLL's in replacement of WINES how would this work and is there a place I can learn a bit more about the wine architechture because I would like to be able to better integrate windows into linux so that people can have the comfort of programs they are familiar while running ubuntu. like would i be able to transfer files directly from vista into Ubuntu making it more compatible with windows

---

### Post by Oldsoldier2003 on 2008-04-08
> **gaurdianAQ said:**
> I read something that you can use windows DLL's in replacement of WINES how would this work and is there a place I can learn a bit more about the wine architechture because I would like to be able to better integrate windows into linux so that people can have the comfort of programs they are familiar while running ubuntu. like would i be able to transfer files directly from vista into Ubuntu making it more compatible with windows

In some cases you can replace certain dlls with the windows versions. With that said it is not recommended except as workaround in order get get certain applications to work correctly. The reason for this is that wine is not windows- the dlls provided by wine are not actual windows provided dlls, adding a bunch of windows native dlls can break your wine.

If you are interested in wine head on over to winehq and look around into helping the project, there are already enough forks of the project so it would be nice to get some more help on the core project.

---

### Post by Rocket2DMn on 2008-04-08
Another alternative is to setup seemless integration with Virtual Box - this is a virtual machine setup that has you install a legal copy of windows by granting it a certain amount of disk space and RAM usage.  This means when you boot into Ubuntu, you can also tell it to boot the windows virtual machine (requires more RAM than a single Ubuntu boot, but is well worth it if you use a fair number of windows programs).
You can read some more here: [https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)
Also, here is a great HowTo to set it up if you want - [http://lifehacker.com/367714/run-windows-apps-seamlessly-inside-linux](http://lifehacker.com/367714/run-windows-apps-seamlessly-inside-linux) - The HowTo is designed for Gutsy, but I used this to setup in Hardy (still in Beta testing stages) and it worked great there, too.

---

### Post by p_quarles on 2008-04-08
Thread moved to the Wine discussion area.

---

### Post by gaurdianAQ on 2008-04-25
so if Im gonna be doing some gaming in windos should I give half my ram for windows I have 2 gigs of ram in total I plan on putting vista on

---

### Post by Rocket2DMn on 2008-04-25
> **gaurdianAQ said:**
> so if Im gonna be doing some gaming in windos should I give half my ram for windows I have 2 gigs of ram in total I plan on putting vista on

In a dual boot system, only one OS can be running at a time, so both can take full advantage of your RAM capacity.  If you hibernate either system (I do not recommend hibernating windows with a dual boot since you won't be able to easily mount the windows partition back in Ubuntu), whatever they have stored in RAM is written to the hard disk.
RAM is volatile memory which means if the system reboots or loses power, whatever was in RAM is cleared and has to be reloaded by whatever OS is booting.
Wine will make use of your RAM like any regular program on your computer, you don't have to deal with it.
If you are setting up a virtual machine, that is the only time you need to worry about RAM, you can give a certain amount of RAM to the VM.  If you do WinXP, I would suggest around 512-768 MB of RAM if you are planning on using intensive applications with it (like games).

---

