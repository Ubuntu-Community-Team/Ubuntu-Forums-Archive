---
title: "Can suspend successfully once in 9.04, on resume gpm &quot;Cannot retrieve data...&quot;"
date: 2009-05-26
forum: x86 64-bit Users
---

### Post by khamil8686 on 2009-05-26
Im getting fed up with this error, ive been googling extensively and just cant figure it out. This problem does not occur in Ubuntu 8.10 Intrepid Ibex. I did a clean install of Ubuntu 9.04 Jaunty Jackalope x64 and i can suspend once successfully, then when i resume gnome-power-manager puts a plug icon in the tray and says "Cannot retrieve data..." and I cannot suspend again, if I log out, then when i log back in i get the message could not initialize HAL! and the computer locks up, and if i try to restart the screen fades to black and scrolls text up the screen and then locks up and doesnt finish its shut down and i need to do a hard restart. Also if i click on the gnome-power-manager plug icon it brings up a little menu that offers hibernate and offers suspend and if i click on one of them it pops up a partially transparent black box in the top right corner of the screen saying the action is forbidden! What follows is my output for the commands of the "Debugging GNOMEPowerManager Ubuntu Wiki" page at [https://wiki.ubuntu.com/DebuggingGNOMEPowerManager](https://wiki.ubuntu.com/DebuggingGNOMEPowerManager)
Im fairly new to Ubuntu but not afraid of the command line, i love it :) Any help is GREATLY appreciated times 599812634981736491283!!!!!11!111!1 :P My thoughts on the situation is when i resume, HAL daemon (hald) doesnt resume successfully. But i could be wrong :) hehe thank you for reading thus far :) some of the debugging outputs i have attached in text files to limit length of this posting, i will say which file the output is in if it is in a file. In order to get all this information i had to restart several times to get
back to a clean slate, unless otherwise specified i run all these codes from a fresh boot of Ubuntu.
Clean slate=havent done any suspends yet to bring up the gnome-power-manager icon

=================================================================
Debugging before Suspend
=================================================================
```
gnome-power-bugreport.sh
```
This file wasnt found, so i searched for it and found it, and ran the following,
```
/usr/share/gnome-power-manager/gnome-power-bugreport
```
Output>
Distro version:       5.0
Kernel version:       2.6.28-11-generic
g-p-m version:        2.24.2
HAL version:          0.5.12
System manufacturer:  missing
System version:       missing
System product:       missing
AC adapter present:   no
Battery present:      no
Laptop panel present: no
CPU scaling present:  yes
Battery Information:
GNOME Power Manager Process Information:
1000      3390  0.0  0.2 230828  9820 ?        Ss   12:42   0:00 gnome-power-manager
HAL Process Information:
111       2495  0.0  0.1  36540  5012 ?        Ss   12:42   0:00 /usr/sbin/hald
root      2561  0.0  0.0  15816  1260 ?        S    12:42   0:00  \_ hald-runner
root      2592  0.0  0.0  28484  2064 ?        S    12:42   0:00      \_ hald-addon-input: Listening on /dev/input/event1 /dev/input/event0 /dev/input/event3 /dev/input/event4
root      2634  0.0  0.0  28480  2040 ?        S    12:42   0:00      \_ /usr/lib/hal/hald-addon-rfkill-killswitch
root      2651  0.0  0.0  28484  2060 ?        S    12:42   0:00      \_ hald-addon-storage: polling /dev/sr0 (every 2 sec)
root      2652  0.0  0.0  28484  2060 ?        S    12:42   0:00      \_ hald-addon-storage: polling /dev/sr1 (every 2 sec)
root      2654  0.0  0.0  28492  2040 ?        S    12:42   0:00      \_ /usr/lib/hal/hald-addon-cpufreq
111       2662  0.0  0.0  32392  2032 ?        S    12:42   0:00      \_ hald-addon-acpi: listening on acpid socket /var/run/acpid.socket

```
hal-find-by-capability --capability "battery"
```
No output. Probably because i have a desktop computer :) However i dont understand the next command's output since nothing was output on this command.

```
hal-find-by-capability --capability "battery" | xargs -n 1 hal-device
```
Output in file hal-find-by-capability

```
hal-find-by-capability --capability "battery" | xargs -t -n 1 hal-get-property --key battery.rechargeable.is_charging --udi
```
this gives me a usage error. it says the --udi option needs a argument. im assuming it needs a unique device identifier but i dont know any to put as an argument

```
lshal -m
```
Output:
Start monitoring devicelist:
-------------------------------------------------
13:16:01.068: computer_logicaldev_input condition ButtonPressed = power
13:16:18.254: pci_1814_301_rfkill_rt61pci_wlan removed


```
dbus-send --system --print-reply --dest="org.freedesktop.Hal" /org/freedesktop/Hal/devices/computer org.freedesktop.Hal.Device.SystemPowerManagement.Reboot
```
This should restart the computer by sending commands directly to HAL. This Reboot code works just fine, system reboots.

```
dbus-send --system --print-reply --dest="org.freedesktop.Hal" /org/freedesktop/Hal/devices/computer org.freedesktop.Hal.Device.SystemPowerManagement.Shutdown
```
This should restart the computer sending a command directly to HAL. Shutdown code works just fine, system shutsdown.

```
dbus-send --system --print-reply --dest="org.freedesktop.Hal" /org/freedesktop/Hal/devices/computer org.freedesktop.Hal.Device.SystemPowerManagement.Hibernate
```
This seems to hibernate just fine, gives me some softreset errors and 1 or 2 others that i cant remember but if needed i will execute this again and write down the errors. On resume the system resumes to a black screen with a frozen mouse cursor. I couldnt switch to any other ttys and i sucessfully did Ctrl+Alt+Printscreen+REISUB to restart.

```
dbus-send --system --print-reply --dest="org.freedesktop.Hal" /org/freedesktop/Hal/devices/computer org.freedesktop.Hal.Device.SystemPowerManagement.Suspend int32:0
```
Interesting. I ran this and the system suspended fine, but on resume the terminal said "Error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)" and gives me that familiar gnome-power-manager icon in the system tray leaving me unable to suspend again. If i try running this code a second time it tells me "Error org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.Hal was not provided by any .service files"

```
dbus-monitor --session "type='signal',interface='org.freedesktop.PowerManagement'"
```
I ran this code and suspended and resumed and then attempted a second suspend to show if any signals were sent across dbus with the gnome-power-manager plug icon showing, this is the output:
signal sender=org.freedesktop.DBus -> dest=:1.63 serial=2 path=/org/freedesktop/DBus; interface=org.freedesktop.DBus; member=NameAcquired
   string ":1.63"
method call sender=:1.45 -> dest=:1.63 serial=172 path=/org/freedesktop/indicate; interface=org.freedesktop.DBus.Properties; member=Get
   string "org.freedesktop.indicator"
   string "type"

```
dbus-monitor --session "type='signal',interface='org.freedesktop.PowerManagement.Backlight'"
```
I ran this code and suspended and resumed, checked the output of the command still running (sent its output to a file on my desktop) and tried to suspend again. All output was from the first suspend/resume, the 2nd suspend appeared to not even send a suspend signal across dbus, heres the output:
signal sender=org.freedesktop.DBus -> dest=:1.61 serial=2 path=/org/freedesktop/DBus; interface=org.freedesktop.DBus; member=NameAcquired
   string ":1.61"
method call sender=:1.46 -> dest=:1.61 serial=166 path=/org/freedesktop/indicate; interface=org.freedesktop.DBus.Properties; member=Get
   string "org.freedesktop.indicator"
   string "type"

```
gconftool --recursive-list /apps/gnome-power-manager
```
Output is in file gpm.gconf.values.txt

```
gconftool --recursive-unset /apps/gnome-power-manager
```
Successfully reset my gconf settings to default

```
gconftool --recursive-list /apps/gnome-power-manager
```
Output is in file gpm.gconf.default.values.txt

```
diff -u gpm.gconf.values.txt gpm.gconf.default.values.txt
```
Output is in file gpmDiff.

After running the last 4 codes, probably resetting the gconf settings is what
caused the change, i can suspend the first time and i resume with no gnome-power-manager tray icon
telling me that it "Cannot retrieve data..."

```
gnome-power-cmd.sh suspend
```
gnome-power-cmd.sh wasnt found so i searched for it and ran the code below

```
/usr/bin/gnome-power-cmd suspend
```
this command returned something interesting. on resume i get no gnome-power-manager tray icon telling me
that it "Cannot retrieve data..." but the terminal window says:
Suspending
Error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Failed

When i try to run the command again, since usually the first suspend works fine and the second doesnt work
i get this:
Suspending
Error org.freedesktop.DBus.Error.Spawn.ChildExited: Launch helper exited with unknown return code 0
Failed

The suspend and Hibernate options are no longer offered in my "Start menu" after this also.

```
killall gnome-power-manager
```
successfully works. feels good to kill something after restarting my computer so many times, ive been
collecting all this info for a good three hours now :P

```
gnome-power-manager --verbose --no-daemon 2>&1 | tee ~/Desktop/gpm.debug.log.txt
```
Output is in gpm.debug.log.txt, when i resume it complains about proxy NULL and that it cant obtain list of
batteries, i dont have batteries, i have it plugged in to AC but i have no idea. The suspend and hibernate options also disappear from "start" menu on resume.

```
dbus-send --session --print-reply --dest="org.freedesktop.PowerManagement" --type=method_call --reply-timeout=6000 /org/freedesktop/PowerManagement org.freedesktop.PowerManagement.CanSuspend
```
I havent restarted to a clean slate since the next section says finding out why suspend/hibernate arent offered. This code returns this error:
Error org.freedesktop.DBus.Error.Spawn.ChildExited: Launch helper exited with unknown return code 0

```
gconftool-2 -g /apps/gnome-power-manager/general/can_suspend
```
This says i can suspend

```
polkit-auth | grep power-management.suspend
```
This returns:
org.freedesktop.hal.power-management.suspend
Which means i can suspend according to the wiki page. If it didnt return anything then i cant suspend it says.

```
hal-device | grep power_management.can_suspend
```
This returns the error:
Could not initialise connection to hald.
Normally this means the HAL daemon (hald) is not running or not ready.

```
pm-is-supported --suspend || echo "Not supported"
```
This code doesnt return anything which means suspend should be supported according to the wiki.

3 Errors i get on boot im not sure are related to or not are the following:
[1.572014]ata1:softreset failed (device not ready)
[2.796017]ata3:softreset failed (device not ready)
modprobe: FATAL: Could not load /lib/modules/2.6.28-11-generic/modules.dep: No such file or directory
Then boots as normal! I found that if i repackaged the initrd with modules.dep, i found a step-by-step online, and i made a easier to follow tutorial at [http://ubuntuforums.org/showthread.php?t=1162619](http://ubuntuforums.org/showthread.php?t=1162619)
However since figuring out how to get rid of that error i have done a clean install of Ubuntu 9.04 and currently have that error showing every boot. so repacking the initrd shouldnt be a factor in this problem.

Im not sure what it could be, im going to post this now and begin working on the DebuggingACPI wiki page to see if that helps. In the meantime hopefully someone posts a solution :P That would be cool! hehe thank you for your help if you have read this far!

---

### Post by khamil8686 on 2009-05-26
I went through the ACPI debugging wiki page at: [https://wiki.ubuntu.com/DebuggingACPI](https://wiki.ubuntu.com/DebuggingACPI)
here are the results:

I updated my BIOS to the most recent version, this didnt fix the problem im having. The next steps were booting with various kernel parameters...
booting with the acpi=off kernel parameter allowed me to boot but didnt give me the option to suspend
in the "start" menu
booting with acpi=ht kernel parameter allowed me to boot but gave me no suspend option
booting with pci=noacpi allowed me to boot but gave me no suspend option
booting with acpi=noirq allowed me to boot but gave me no suspend option
booting with pnpacpi=off restored my suspend option but the suspend option didnt work
booting with noapic restored the option but the option didnt work
booting with nolapic gave me the error of:
[0.220064] BIOS bug, local APIC #0 not detected...
[0.220099] ... forcing use of dummy APIC emulation. (tell your hw vendor)

After displaying that message the computer froze with a blinking cursor at the next line, couldnt switch
ttys or anything, ctrl+alt+printscreen+reisub didnt even work.

On that wiki i found debugging kernel suspend and understanding suspend, im going to check those out now.

---

### Post by khamil8686 on 2009-05-27
tried different graphics driver configurations with mixed results, in the end nothing really fixed the problem. maybe 9.10 will work for me? :cry:

---

### Post by pixel :-) on 2009-05-28
too bad no one ansered, you seemed motivated :)

---

### Post by khamil8686 on 2009-05-28
> **pixel :-) said:**
> too bad no one ansered, you seemed motivated :)

still motivated :P would like to figure it out but just gotta give it time, will probably be something ungodly simple that fixes it all in the end. until then *pats stack of books on linux* gonna be reading :P i think for a short time i was able to get the error gone, could suspend/resume a few times i think (dont remember, i have a brain injury, basically if you have seen the movie finding nemo, im kinda like dory, short term memory loss :) if my memory isnt fooling me i suspended/resumed a couple of times but then i suspended for a few hours and came back and the error was there, i was trying out different configurations of my gfx driver, tried fglrx, tried to manually install, and so on, im just not able to reliably repeat my results. i have ati radeon 3200 HD if that helps anyone :) im taking a break for a few days though, unless someone posts a fix beforehand. being new to ubuntu and linux in general messing around so much i messed up 9.04 many times and then did fresh reinstalls, and i messed up my other partition a few times on accident through my trial and error. im learning alot :) at least thats good :)

---

### Post by Didjit on 2009-05-30
I have never been able to suspend out of the box since Dapper.  I use "s2ram", its in package **"uswsusp". [B]I have to use **[/B]"s2ram --force --vbe_save**" as my options. Then I just hack **/usr/lib/hal/scripts/linux/hal-system-power-suspend-linux to call "s2ram". Not a perfect solution to your problem, but it has always just worked for me.

HTH

Didjit

---

### Post by khamil8686 on 2009-05-30
> **Didjit said:**
> I have never been able to suspend out of the box since Dapper.  I use "s2ram", its in package **"uswsusp". [B]I have to use **[/B]"s2ram --force --vbe_save**" as my options. Then I just hack **/usr/lib/hal/scripts/linux/hal-system-power-suspend-linux to call "s2ram". Not a perfect solution to your problem, but it has always just worked for me.

HTH

Didjit

suspend works for me in 8.10 though, i hear 9.04 changed to pmutils or something. maybe my computer isnt compatible with pmutils or something?
thank you :) i will look into this!

---

### Post by khamil8686 on 2009-06-02
i have ati radeon HD 3200. i can suspend successfully on a live install and before i install fglrx or manually install the driver, only have ati because when i bought this mobo i was using windows. gonna check out some nvidia cards and see what would be most compatible :)

---

### Post by khamil8686 on 2009-06-07
ordered a nvidia video card and going to bypass the ati one on my mobo, hopefully it fixes it :)

---

### Post by khamil8686 on 2009-06-10
new nvidia geforce 8400 graphics card running with a fresh install of ubuntu jaunty. suspend option and hibernate option disappear after a suspend. motherboard problem? ...

---

### Post by khamil8686 on 2009-06-18
same problem with new graphics card. least i got an nvidia graphics card now. turns out the problem was wicd. i included wicd in my clean install + update process figuring it couldnt possibly be wicd and turns out it was! the hardest problems are always solved by flipping a switch or something :P so i just use networkmanager now, had to resolve an issue with rt61pci staying in the kernel over suspend, or something. i believe. whatever, stuff works now, im happy :D:D:D

---

### Post by AClark on 2009-06-19
I think that now that the rt61pci driver is being removed before suspending you will find that WiCd works perfectly - at least it does for me after the same fix.

---

