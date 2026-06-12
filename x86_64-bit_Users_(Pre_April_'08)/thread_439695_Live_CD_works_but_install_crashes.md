---
title: "Live CD works but install crashes"
date: 2007-05-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by Sladi on 2007-05-10
Hi! 
I just tried the live 64bit Live CD and it worked well. 
Then I installed it to the HDD and it wont boot except in recovery mode. 

I tried xinit and it crashes (some message about "kernel alive", "mapping" and then a hard locked black screen). I also tried changing ati to vesa in xorg.conf and disabling AGP fast writes and aperture in BIOS. 

Can someone help me please? 


Regards, 
Sladi 


edit:
My system is: 
Amd A64, Via Kt800, Radeon X800XL, IDE HDD and DVD

---

### Post by blueturtl on 2007-05-11
Have you tried using the regular 32-bit version or do you spesifically need the 64-bit edition?

64-bits is kind of a buzz-word right now but there is little to no-benefit in actually going 64-bit just now.

---

### Post by Sladi on 2007-05-11
The 32bit version worked fine. 

I'd like to use the 64bit version very much because I could use 64bit Blender and rendering programs usually benefit noticeably. Every program and driver I need is available in 64bit.
 I also installed Blender using the live CD and it seemed to render quicker.

---

### Post by blueturtl on 2007-05-11
Unfortunately I'm out of my depth when it comes to kernel errors, I hope someone else can provide assistance for you. Having the exact error message will help us narrow it down though (if you can get it). Are you sure the 64-bit desktop cd is not corrupted? That would explain why you can run it, but the installed version fails to load...

---

### Post by Sladi on 2007-05-11
Thanks blueturtl! :) 

I burned the CD again but it still won't work. I also checked the MD5 of the iso. 
The same error happes when I choose to check the CD for errors in the boot menu. 
I had teken a photo of the message before the PC locked up. It says: 
```
Kernel alive 
Kernel direct mapping tables up to 100000000 @ 8000-d000
```

Regards, 
Sladi


edit: 
As I said recovery mode boots fine. 
Is it normal that I don't have to login though? I automatically get root access. 

edit2: 
Using the live CD the films in Examples won't work. I get audio but no video. Is this a common problem?

---

### Post by blueturtl on 2007-05-12
Recovery mode gives you root access because it is often required to fix things. Needless to say you shouldn't run in safe mode regularly.

You could try defining boot parameters at the boot menu before selecting to boot the default kernel. I think you hit the key c or e to edit, Grub will have this information for you. Anyway, add the commands 'noapic nolapic' and see if that helps.

As for the videos, I really can't say - I rarely use Totem (Video Player) to play anything. I have mplayer and xine installed on my desktop system.

---

### Post by Sladi on 2007-05-13
I doubt it's ACPI or APIC because checking CD integrity crashes already. I tried changing the drive and burning to CD an DVD too. I also tried changing many BIOS settings. 
I also tried installing 64Studio and it's the same, although checking the CD won't crash but says that there is no valid CD in the drive. 

Thanks, blueturtl. 


Regards, 
Sladi

---

### Post by neroscu on 2007-05-13
> **Sladi said:**
> I doubt it's ACPI or APIC because checking CD integrity crashes already. I tried changing the drive and burning to CD an DVD too. I also tried changing many BIOS settings. 
I also tried installing 64Studio and it's the same, although checking the CD won't crash but says that there is no valid CD in the drive. 

Thanks, blueturtl. 


Regards, 
Sladi

just add the boot option [COLOR="Red"]noapic[/COLOR] .

boot from DVD-ROM , when you see the installation menu,

press F6 , then add [COLOR="Red"]noapic[/COLOR] at the end of that sentence.

---

### Post by Sladi on 2007-05-17
I tried that and it didn't work. I also tried 64Studio.

---

