---
title: "Bluetooth wont start"
date: 2008-09-18
forum: x86 64-bit Users
---

### Post by Bloemetjesgordijn on 2008-09-18
Hi guys,


I have some trouble with my bluetooth keyboard. For some reason my bluetooth keyboard does not work after boot, To solve this now I have to do "sudo hidd --search"


Please help I have tried everything.

I rebooted Ubuntu a few times, during a boot i noticed..."Bluetooth host down" Maybe this helps

Agian please help

kind regard

Bloemetjesgordijn

---

### Post by John Jason Jordan on 2008-09-18
> **Bloemetjesgordijn said:**
> I have some trouble with my bluetooth keyboard. For some reason my bluetooth keyboard does not work after boot, To solve this now I have to do "sudo hidd --search"

I rebooted Ubuntu a few times, during a boot i noticed..."Bluetooth host down" Maybe this helps
I am not clear about what you are saying. Does the keyboard work after you do "sudo hidd --search"?

Bear in mind that bluetooth devices doge not work until after Ubuntu has booted. For example, a lot of people with bluetooth keyboards have problems if they need to use the keyboard to access the BIOS. To get into the BIOS they have to plug in a standard keyboard temporarily.

I can also suggest that you install a utility called blueman. It is not in the standard Ubuntu repositories, but you can add the repository for it and install it with instructions here:

[http://blueman.tuxfamily.org/index.php?option=com_content&view=article&id=51&Itemid=56]("http://blueman.tuxfamily.org/index.php?option=com_content&view=article&id=51&Itemid=56")

---

### Post by Bloemetjesgordijn on 2008-09-19
> I am not clear about what you are saying. Does the keyboard work after you do "sudo hidd --search"?

Yes, the keyboard and mouse (they are integrated into one) are working after "sudo hidd -- search"

> I can also suggest that you install a utility called blueman. It is not in the standard Ubuntu repositories..

Thx, I have allready tried that and more...I have installed Blueman (worked once, but not any more), reinstalled the default BT from Ubuntu (same issue-> no succes) and Bluez 4.6 (no succes, however i dont know if the install went ok).

Thinking of it, this might be the problem, maybe all the programs are messing with each other...

Eitherway, I have cahnged: in /etc/default/bluetooth
HIDD_ENABLED=0 to 1
and HIDD_OPTIONS="--connect aa:bb:cc:dd: --server"

but after reboot ... no BT keyboard and mouse

oops](*,):oops:

Just found out, that I should have done also: "echo hidp | sudo tee -a /etc/modules"

Maybe this should help. *shame* :oops:


Cheerz

Bloemetjesgordijn

---

### Post by Bloemetjesgordijn on 2008-09-22
Hi,

This "echo hidp | sudo tee -a /etc/modules" did the trick.

However at bootup I get all kind of "OK"  messages, but eventually I get the message "Bluetooth host down"

If I touch my BT Keyboard (press key or mouse), it goes away and I have BT connection.

It looks like Ubuntu is trying to find my BT Keyboard.

Does anyone have a solution, to solve this "Bluetooth host down" message???


Cheeerz

Bloemetjesgordijn

---

