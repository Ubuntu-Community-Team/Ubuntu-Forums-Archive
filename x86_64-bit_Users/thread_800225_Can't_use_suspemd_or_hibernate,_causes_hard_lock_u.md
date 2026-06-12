---
title: "Can't use suspemd or hibernate, causes hard lock up after pressing power button"
date: 2008-05-19
forum: x86 64-bit Users
---

### Post by philinux on 2008-05-19
Anyone got a fix?

Desktop pc.

---

### Post by philinux on 2008-05-20
Bump.

---

### Post by Elim_Garak on 2008-05-22
> **philinux said:**
> Anyone got a fix?

That's a strange one.  Does it only cause this problem when you try to use the power button to engage the particular power management function, or does it also do it when you do it by clicking the panel button?

I had an old Dell that had a similar problem, and my thoughts were that it was a bios problem.  Set one way in the bios, the buttons would appear, but not function correctly, and set the other way, they simply wouldn't appear at all.

---

### Post by philinux on 2008-05-22
Ok I select quit then suspend. Computer goes to sleep. Keyboard and mouse are off.

Only way to wake it up is to press main power button on pc.

Power comes on mouse keyboard are on, disk drive activity light then nothing.

Only thing then is REISUB and it reboots.

---

### Post by fjgaude on 2008-05-22
I have the same problem and I have a Gigabyte GA-P35-DS4 motherborad. I simply don't use Suspend, knowing that it will, but then I have to, in the end, reboot.

---

### Post by philinux on 2008-05-22
It would be good to get this going to save power etc while away from machine.

I've reported this at launchpad

---

### Post by cubeist on 2008-05-22
I have a similar motherboard - the Gigabyte version of your board with the 780g/sb7000 chipsets and mine suspends and hibernates fine, BUT, I had to enable legacy mouse and keyboard support in bios, and change the suspend mode in bios to S1 (from S3).  I don't know why this enable suspend and hibernate on my board, but if you have those options in your Asus bios it may be worth trying.

On the other hand, this may be an Asus motherboard issue rather than a chipset problem...

---

### Post by philinux on 2008-05-22
What does this mean, what are suspend modes?

Suspend mode in bios to S1 (from S3)

---

### Post by cubeist on 2008-05-22
> **philinux said:**
> What does this mean, what are suspend modes?

Suspend mode in bios to S1 (from S3)

Well, you will have to refer to your motherboard manual for the exact descriptions as they vary from manufacturer's.  On my gigabyte, I have only two options, ACPI S1 and ACPI S3.  These modes control how the MB allocates power to various devices while suspended or hibernated.  If I remember correctly, S1 uses more power because the HDD has to stay awake to keep the session information active, S3 on the other hand puts your session information in RAM and is a lower power sleep state.

Neither mode should be harmful, and in theory, both modes should work with linux, but one may work better than another...

If you need more info, you will have to google what ACPI S1/S3 states are what exactly they do... EDIT - here is a link that explains it better than I! [http://www.motherboardpoint.com/t14786-suspend-mode.html](http://www.motherboardpoint.com/t14786-suspend-mode.html)

---

### Post by markbuntu on 2008-05-23
Suspend, hibernate, none of that works on my machine. But then again sensord tells me that V5stby is 0.00v, only V3.3stby is active. So, it seems that HP has had the option for S1 suspend removed from my motherboard and maybe for S3 also since I am not sure if the ram requires 5v or 3.3v.

I have an HP Pavilion an1330n Media Center with an ASUS A8AE-LE (OEM) motherboard made for HP so HP most likely had Asus cut some corners to keep the price down.

---

### Post by philinux on 2008-05-24
I tried S1 and S3 non worked so set that back to auto.

Here are the bios settings for this, is this looking like it shoudld.

[COLOR="DarkGreen"]PowerSettings

Suspend mode = Auto

ACPI Support = Disabled

ACPI ACPI support = Enabled[/COLOR]

Apm config - not looked at yet
HW monitor config - not looked at yet

---

### Post by Elim_Garak on 2008-05-28
[FONT="Courier New"]Well, now I've been jinxed, it would appear.  When using kernel 2.6.24-17.31, my power management is screwed up.  I can enter suspend mode, but cannot leave it.  If I move the mouse or hit the keyboard, the system sounds like it's waking up (everything starts to make noise as per normal), but the monitor doesn't awaken and it doesn't seem like the system does either.  For instance, the caps lock key and number lock key do not affect the lights on the keyboard, contrary to what is normal.  When I boot into kernel 2.6.24-16.30, it works perfectly.

Any ideas on this one?  Yes, I already reinstalled the kernel just in case it was something strange on that end.[/FONT]

---

### Post by Elim_Garak on 2008-06-02
[FONT="Courier New"]Bump.  Anyone else run into this little problem?[/FONT]

---

### Post by philinux on 2008-06-03
Look like a trip to launchpad.

---

### Post by quee0849 on 2008-06-03
I have the same problem when i upgraded to kernel 2.6.24-17.31 - now suspend and hibernate are broken, but using kernel 2.6.24-16.30 they work fine. I have a G33T-M2 motherboard.

---

### Post by lessfield on 2008-06-03
Same problem w/ my mythbox, which is a Gigabyte ga-8knxp, using the nvidia driver, and a xorg.conf setup for s-video tv output. 
When i pm-suspend and resume, the system powers on but with no screen. 

Sometimes after a resume attempt i can ssh onto my system, but trying to restart X via xinit does not work. 

Also, I have tried playing with some settings in /etc/defaults/acpi-setting but no progress.

Any suggestions as to how to debug?

---

### Post by Elim_Garak on 2008-06-04
> **quee0849 said:**
> I have the same problem when i upgraded to kernel 2.6.24-17.31 - now suspend and hibernate are broken, but using kernel 2.6.24-16.30 they work fine. I have a G33T-M2 motherboard.

[FONT="Courier New"]18, released in the past 24 hours, doesn't help, either.  Apparently, 19 is working for some people.  I've sent what I know to Launchpad.[/FONT]

---

