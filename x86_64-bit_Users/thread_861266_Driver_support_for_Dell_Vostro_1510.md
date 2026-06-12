---
title: "Driver support for Dell Vostro 1510"
date: 2008-07-16
forum: x86 64-bit Users
---

### Post by fundae on 2008-07-16
Hi guys,

I've used some Linux distros over the years but for one reason or another I've primarily worked on Windows, so apologies if this is a stupid question.

I'm getting a Dell Vostro 1510, and I want to install the 64-bit Ubuntu, but I'm a little concerned about the driver support. I know that on windows device drivers have to 64-bit when running on a 64-bit OS. Does this restriction apply to Linux as well? If so, will I find 64-bit drivers for the Vostro? 

I googled for linux driver support for the Vostro 1510, and found two conflicting reports - one guy claimed that most things worked, but he had to do some extra work to make the sound work; another guy claimed that everything worked out of the box. There wasn't any mention of the "bitness" of the OS used. 

I will primarily be using the laptop to write code. I expect to mainly use vim, gcc, llvm and python. I may run a few other interpreters and compilers and will of course use a music player and a web-browser. 

What do you guys recommend - should I do a dual install of the 32 and 64 bit versions? Or just stick to 64 bit only? Am I missing some factors that need to be taken into consideration before making this decision?

Thanks in advance,
Pramod

---

### Post by phidia on 2008-07-16
I'm a little weird on this issue but I like 64 bit and I do think there _is_ a difference particularly with video playing & editing.
To your 1st question: yes if you use a 64 bit OS linux, windows, whatever you need 64 bit drivers. 
I didn't have time to search for the specs on your model, but for laptops it seems intel (cpu & wireless) works the best for having everything work without excessive problems.

---

### Post by darkknight045 on 2008-07-17
This is sort of the default response, but it is the best you can do:

Download and burn the liveCD and give it a whirl, its virtually* risk free!

If it works on the liveCD it should work just fine with a full install.  This is not a foolproof test, but it will show you what is going to work out-of-the-box versus what needs tinkering to run properly.

[SIZE="1"]*You can still login as root and go to town on your system.  This can be a good thing (file recovery) or a bad thing, utterly unprotected file destruction.[/SIZE]

---

### Post by risqnul on 2008-07-23
Hi everybody,

I have a DELL Vostro since the end of May.
I'm running Kubunbu 8.04 64 on it.
List of quirks with this distribution :
1) Driver problem with ethernet interface. Had to recompile r8168 driver module for kernel 2.6.24 (it's a Linux kernel "bug").
2) X.org video driver sticks to "vesa", so no 3D acceleration. I don't know how to change it without breaking the setup (tried). It happens that Mandriva 2008 (which i tried) selects the correct Intel GM965 driver.
3) Can't connect with Wifi when the network is password-protected (any help on this one would be appreciated).
4) Suspend to RAM often doesn't resume all right, hibernate doesn't work.
5) Some blue function keys don't work (CRT/LCD, sleep...). But screen brightness, sound volume and CD keys work, so i guess it's just a matter of key mapping. 

Notice : I'm using this setup daily for my work (removed Vista altogether - would have kept XP).
I know my input is quite basic... but hope this helps.
It's sad that DELL doesn't offer a UBUNTU setup for this machine...

---

### Post by empty_tank on 2008-07-23
> **risqnul said:**
> Hi everybody,

I have a DELL Vostro since the end of May.
I'm running Kubunbu 8.04 64 on it.
List of quirks with this distribution :

3) Can't connect with Wifi when the network is password-protected (any help on this one would be appreciated).

4) Suspend to RAM often doesn't resume all right, hibernate doesn't work.


I am using Vostro 1400n with ubunty hardy 8.04.1 amd64.  Maybe I can help with the last 2 problems.

for the wifi connecntion, I installed wicd to replace network-manager.  I had no problems since with secured wifi connections.

for hibernation, I have posted previously about editing grub menu see [http://ubuntuforums.org/showthread.php?p=5328001#post5328001](http://ubuntuforums.org/showthread.php?p=5328001#post5328001)


hope this helps you.

---

### Post by Duranxl on 2008-07-23
I have a Vostro 1500 and im running Ubuntu 64bit.

Had to fiddle around to get my 8600M GT working but besides that everything worked right away.
Ethernet, sound, wireless, laptop hotkeys, everything:)

---

### Post by fundae on 2008-07-27
I got the laptop on Friday, installed Ubuntu 8.04 64-bit and found out that my internet connection wasn't working. After a bit of digging around I found out I need to pass "pci=nomsi" to the kernel when booting. It was a little frustrating until I found that out, but things are working nicely now. 

Thank you everyone for your input.
-- Pramod

---

### Post by skiold on 2008-07-28
Hi,
I have a Dell Vostro 1510 with the same trouble.
Could you explain me how to pass "pci=nomsi" to the kernel?
I would appreciate a lot for your help.

Thanks in advance

---

### Post by fundae on 2008-07-29
> **skiold said:**
> Hi,
I have a Dell Vostro 1510 with the same trouble.
Could you explain me how to pass "pci=nomsi" to the kernel?
I would appreciate a lot for your help.

Thanks in advance

See here for instructions:

[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

You have to add "pci=nomsi" at the end of the line that begins with "kernel".

---

### Post by nexuz on 2008-07-30
I've just installed Ubuntu 8.04 in my Vostro 1510, and everything works just perfect, sound, wireless, bluetooth, hotkeys, everything, but you have to install envy for the correct instalation of the nvidia driver.

---

### Post by fundae on 2008-07-31
Ok, it turns out the pci=nomsi thing doesn't really work. The thing has stopped working. Grr!

It must've been some random luck that once I added the line the damn thing started working. The little icon [wired connection] shows up as connected even when no cable is plugged in. I am getting highly frustrated, because its really hard to get anything done without an internet connection.

Any ideas will be much appreciated.

Thanks,
Pramod

**UPDATE:** Downloading the r8168 driver from Realtek, compiling and installing it seems to solve the problem.

---

### Post by alexander1 on 2008-09-04
> **risqnul said:**
> 3) Can't connect with Wifi when the network is password-protected (any help on this one would be appreciated).I thought I had the same problem, but you just have to try it some times and you probaply have to delete the saved WLAN and reenter the password.

I get the Wlan to work with ndiswrapper. 


I did manage to get the external mic to work. Here is how:
[http://ph.ubuntuforums.com/showthread.php?p=5727032#post5727032](http://ph.ubuntuforums.com/showthread.php?p=5727032#post5727032)

---

