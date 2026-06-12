---
title: "Shutdown problems"
date: 2008-04-30
forum: x86 64-bit Users
---

### Post by C. Wizard on 2008-04-30
Running 8.04, AMD_64, Kubuntu.
7.10 didn't shut down properly either, nor did Slackware 12, but it is even worst with Kubuntu 8.04.
Doesn't matter if you tell it to shutdown, reboot, or logout, it closes down KDE and then all I get is a black screen. Nothing else. No messages, just a black screen and the machine is not powered down.
Even if I open a console and issue the shutdown command, "shutdown -h now" it goes through the shutdown routine, but doesn't turn off the machine.
Any ideas?
Thanks.

---

### Post by ASULutzy on 2008-04-30
Maybe a weird BIOS setting?

Are you able to shutdown in ANY operating system?

I would start by typing dmesg and scrolling up, and looking for messages regarding apm or acpi, those are power management related things. Post what  you see about them here.

You might have to add something to GRUB to force apm.

---

### Post by C. Wizard on 2008-04-30
> **ASULutzy said:**
> Maybe a weird BIOS setting?

Are you able to shutdown in ANY operating system?

I would start by typing dmesg and scrolling up, and looking for messages regarding apm or acpi, those are power management related things. Post what  you see about them here.

You might have to add something to GRUB to force apm.
Thanks for your reply.

Slackware 11 and XP both shutdown properly. Slackware 12, Kubuntu 7.10 and 8.04 do not.

Nothing in dmesg relating to apm or acpi.

---

### Post by ASULutzy on 2008-04-30
I'm out of ideas:confused:

---

### Post by kislo_metal on 2008-04-30
had a same problem....

---

### Post by lihsus on 2008-04-30
i also have similar problem in hardy with kde4 but in 32bit. Each time i shutdown or restart from kde4, simply blank screen appears and stays like that...
Then i just restart the X-server (by pressing  **ctrl+alt+backspace**), then the login window appears... through which i can easily shutdown or restart, i.e.  it works fine from there.

few days ago i made changes in login manager... then this problem started, before that it was woking just fine !!!

---

### Post by lihsus on 2008-04-30
and one more thing... it does shutdown if u issue **/sbin/halt** from konsole.

---

### Post by kislo_metal on 2008-05-01
loks like hal demon problem..waiting for updates?:guitar:

---

### Post by kislo_metal on 2008-05-01
this problem also on 32-bit system.

---

### Post by Fatal Equinox on 2008-05-01
I have a similar problem with hibernating in ubuntuu 8.04,  Doesn't shut off the labtop and burns the battery once i unplug it. Sony Vaio VGN-AR170g using wubi... Intel centrino duo

---

### Post by Kilz on 2008-05-01
> **C. Wizard said:**
> Running 8.04, AMD_64, Kubuntu.
7.10 didn't shut down properly either, nor did Slackware 12, but it is even worst with Kubuntu 8.04.
Doesn't matter if you tell it to shutdown, reboot, or logout, it closes down KDE and then all I get is a black screen. Nothing else. No messages, just a black screen and the machine is not powered down.
Even if I open a console and issue the shutdown command, "shutdown -h now" it goes through the shutdown routine, but doesn't turn off the machine.
Any ideas?
Thanks.


In the past, whenever I have ran into a problem with shutdowns running into a black screen it is always been video driver related. What video card are you using? what drivers are installed for it and how were they installed?

---

### Post by jeremy12 on 2008-05-01
I to am reciving a issue somewhat like this however mine started from the installation reboot even


Screen shot of the Restart screen:
[IMG]http://i31.tinypic.com/rsvqwy.jpg[/IMG]

---

### Post by C. Wizard on 2008-05-01
> **lihsus said:**
> and one more thing... it does shutdown if u issue **/sbin/halt** from konsole.

That is the same as "shutdown -h now"
and the result it the same, that is, it goes through the shut down procedure, but doesn't turn off the machine.

---

### Post by C. Wizard on 2008-05-01
> **Kilz said:**
> In the past, whenever I have ran into a problem with shutdowns running into a black screen it is always been video driver related. What video card are you using? what drivers are installed for it and how were they installed?
Asus/ATi AX550. Drivers are the ATi "restricted drivers" automatically installed by Adept Manager.

---

### Post by Kilz on 2008-05-01
> **C. Wizard said:**
> Asus/ATi AX550. Drivers are the ATi "restricted drivers" automatically installed by Adept Manager.

You might consider installing the ati drivers from ati. This howto is what I used on my x1050 which is of the same family (x550/x600/x1050). [I recommend method 2]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method")

---

### Post by kislo_metal on 2008-05-01
I have ati x600 and default driver..
by the way- if mashin is started without Xserver the hal work fine.

---

### Post by C. Wizard on 2008-05-01
> **Kilz said:**
> You might consider installing the ati drivers from ati. This howto is what I used on my x1050 which is of the same family (x550/x600/x1050). [I recommend method 2]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method")
Thanks for the reply. The ATi drivers are installed, so what would be the benefit of doing it per your way, other than, perhaps, getting slightly newer drivers?
Thanks, again for taking the time to respond.

---

### Post by piousp on 2008-05-01
I guess the benefit could be that it will shutdown properly with "his" method.
I'm gonna try it out.

---

### Post by Kilz on 2008-05-01
> **C. Wizard said:**
> Thanks for the reply. The ATi drivers are installed, so what would be the benefit of doing it per your way, other than, perhaps, getting slightly newer drivers?
Thanks, again for taking the time to respond.

Newer drivers specifically designed by the manufacturer of your card, installed the way the manufacturer of your card recommends they be installed (using the ati installer file to make packages). After all what have you got to lose , but the problem you are having?

---

### Post by leomelo on 2008-05-01
Same problem here,but with a 32 bit.

---

### Post by Yellow Pasque on 2008-05-01
The 8-3 and 8-4 Catalyst drivers are much better than the ATI of old, especially with Ubuntu 8.04. The developers have gotten them to the point where I'm comfortable recommending them to n00bs (as long as it's not AGP).

---

### Post by C. Wizard on 2008-05-02
> **Kilz said:**
> Newer drivers specifically designed by the manufacturer of your card, installed the way the manufacturer of your card recommends they be installed (using the ati installer file to make packages.
I guess I'm not understanding you or you are not understanding me. :) The ATi drivers from ATi are installed in my system.  Here is a snapshot of the ATi Catalyst report:

---

### Post by kislo_metal on 2008-05-02
I think you looking in wrong way.
I try to install new ati drivers but problem is not diaper.
Now had reinstall kubuntu, but don`t upgrade one packet - hal.
think you need to downgrade you hal.
for me - it`s work perfect.:guitar:

---

### Post by Kilz on 2008-05-02
> **C. Wizard said:**
> I guess I'm not understanding you or you are not understanding me. :) The ATi drivers from ATi are installed in my system.  Here is a snapshot of the ATi Catalyst report:

What I am telling you is this.
1. You reported an issue
2. I have suggested a fix that cant hurt anything and may solve the issue.
3. If you dont want to do the fix thats fine, enjoy the problem.
4. Have a nice day.  :D

---

### Post by jeffrobodean on 2008-05-02
I had the same problem in Kubuntu AMD64 with the Radeon 9550, disabling the ATI accelerated graphics driver solved the problem.  Go to KMenu >System >Hardware Drivers Manager and uncheck the box next to the driver.

---

### Post by suryaoruganti on 2008-11-08
I had the same problem with Kubuntu 8.10,
In the System Settings, Go to advanced->login manager, in that go to the ShutDown tab.

For Halt, give the command :/sbin/shutdown -P
This will enable shutdown.


Alternative Workaround:
When u get the blank screen, press ctrl+alt+f2 , 
login and then use the command "sudo shutdown"
HTH

---

### Post by CX15 on 2008-11-16
> I had the same problem with Kubuntu 8.10,
In the System Settings, Go to advanced->login manager, in that go to the ShutDown tab.

Hi

New here so need more help.

Where do I find "System Settings" ??

I searched the help file as well as online, but I am not sure where to find it.

Im running Intrepid.

Thanx

---

