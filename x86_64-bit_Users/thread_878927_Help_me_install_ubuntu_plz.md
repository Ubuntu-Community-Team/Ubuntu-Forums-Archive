---
title: "Help me install ubuntu plz?"
date: 2008-08-03
forum: x86 64-bit Users
---

### Post by tesla.coil on 2008-08-03
hi i am new to ubuntu ...i asked for a cd for 64 bit AMD and i got it few days back ..after going through the normal installtion procedure  by clicking install with in windws after the system boots up ..to select between winxp\server03\ubuntu ..and as i select ubuntu  am stuck in a busybox environment ie..Live CD boot stuck on initramfs/busybox! what am i supposed to do here? i really wanna try ubuntu but some how i donno hw to get past this? :( my pc specs are 
```
System Information
------------------
Time of this report: 8/3/2008, 22:23:03
       Machine name: TESLAMACHINE
   Operating System: Windows XP Professional (5.1, Build 2600) Service Pack 3 (2600.xpsp.080413-2111)
           Language: English (Regional Setting: English)
System Manufacturer: GBT___
       System Model: AWRDACPI
               BIOS: Award Modular BIOS v6.00PG
          Processor: AMD Athlon(tm) 64 Processor 3000+,  MMX,  3DNow, ~1.8GHz
             Memory: 1024MB RAM
          Page File: 386MB used, 2074MB available
        Windows Dir: C:\WINDOWS
    DirectX Version: DirectX 9.0c (4.09.0000.0904)
DX Setup Parameters: Not found
     DxDiag Version: 5.03.2600.5512 32bit Unicode

```

```

---------------
Display Devices
---------------
        Card name: NVIDIA GeForce 7600 GS 
     Manufacturer: NVIDIA
        Chip type: GeForce 7600 GS
         DAC type: Integrated RAMDAC
       Device Key: Enum\PCI\VEN_10DE&DEV_0392&SUBSYS_033E0000&REV_A1
   Display Memory: 256.0 MB
     Current Mode: 1024 x 768 (32 bit) (60Hz)
          Monitor: Default Monitor
  Monitor Max Res: 
      Driver Name: nv4_disp.dll
   Driver Version: 6.14.0011.7519 (English)
      DDI Version: 9 (or higher)
Driver Attributes: Final Retail
 Driver Date/Size: 5/16/2008 14:01:00, 6108928 bytes
      WHQL Logo'd: Yes
  WHQL Date Stamp: n/a
              VDD: n/a
         Mini VDD: nv4_mini.sys
    Mini VDD Date: 5/16/2008 14:01:00, 6557408 bytes
Device Identifier: {D7B71E3E-40D2-11CF-EF7E-352300C2CB35}
        Vendor ID: 0x10DE
        Device ID: 0x0392
        SubSys ID: 0x033E0000
      Revision ID: 0x00A1
      Revision ID: 0x00A1
      Video Accel: ModeMPEG2_A ModeMPEG2_B ModeMPEG2_C ModeMPEG2_D ModeWMV9_B ModeWMV9_A 
 Deinterlace Caps: {6CB69578-7617-4637-91E5-1C02DB810285}: Format(In/Out)=(YUY2,YUY2) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_PixelAdaptive 
                   {335AA36E-7884-43A4-9C91-7F87FAF3E37E}: Format(In/Out)=(YUY2,YUY2) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_BOBVerticalStretch 
                   {6CB69578-7617-4637-91E5-1C02DB810285}: Format(In/Out)=(UYVY,YUY2) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_PixelAdaptive 
                   {335AA36E-7884-43A4-9C91-7F87FAF3E37E}: Format(In/Out)=(UYVY,YUY2) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_BOBVerticalStretch 
                   {6CB69578-7617-4637-91E5-1C02DB810285}: Format(In/Out)=(YV12,0x3231564e) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_PixelAdaptive 
                   {335AA36E-7884-43A4-9C91-7F87FAF3E37E}: Format(In/Out)=(YV12,0x3231564e) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_BOBVerticalStretch 
                   {6CB69578-7617-4637-91E5-1C02DB810285}: Format(In/Out)=(NV12,0x3231564e) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_PixelAdaptive 
                   {335AA36E-7884-43A4-9C91-7F87FAF3E37E}: Format(In/Out)=(NV12,0x3231564e) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_BOBVerticalStretch 
         Registry: OK
     DDraw Status: Enabled
       D3D Status: Enabled
       AGP Status: Enabled
DDraw Test Result: Not run
 D3D7 Test Result: Not run
 D3D8 Test Result: Not run
 D3D9 Test Result: Not run

```

plz help! thanks in advance

---

### Post by jualin on 2008-08-03
Have you tried running the LiveCD on Safe Graphics mode, by pressing F4 when the LiveCD is loading?

---

### Post by BGFG on 2008-08-03
i'd suggest you boot from the ubuntu cd and install there rather than in windows. Do you intend to use that same drive for both OS'es ?

---

### Post by tesla.coil on 2008-08-03
while installing it boots up and i have to select bt various os ( i have 2 at the moment xp and server 03) and then i dont get a GUI mode  i get into  a CLI (Busybox)mode. i tried installing it it another drive it dont work! same problem.

---

### Post by BGFG on 2008-08-03
Sorry if i sound a bit confused, is you maching booting from cd ? because you mentioned choice of OS and that should not be happening if you are booting from the live cd.

---

### Post by tesla.coil on 2008-08-03
> **BGFG said:**
> Sorry if i sound a bit confused, is you maching booting from cd ? because you mentioned choice of OS and that should not be happening if you are booting from the live cd.

ok lemme be precise ..this how i am doing it am in xp  i insert the livecd and select the 2nd option install it with in windows 3) it says its making an image 
4) the cd trap pops out asking me to remove and cd\dvd which i do

5) i get an option to do automatic reboot or select ill boot manually later

6)the system restarts (since i dnt select the 2nd option

7) at the boot menu i get 3 options server 03\xp\ubuntu ,i select ubuntu.

8) then it says kernel loaded and stuff, i see the ubuntu logo with progress bar moving from righ to left 

9) then i get the busybox :(

same prblm mentioned here
[http://ubuntuforums.org/showthread.php?t=876951](http://ubuntuforums.org/showthread.php?t=876951) 

lol am really pissed off at the moment  coz i v.badly wanted to install ubuntu and learn it:(

---

### Post by jualin on 2008-08-03
What I would do first is make sure Ubuntu is not installed. Check in Windows Control Panel and if Ubuntu is installed uninstall it first. Then i would recommend you checking the tutorial on my signature to install Ubuntu "Dual Booting with Windows" (Having windows and Ubuntu in the same machine)

---

### Post by jualin on 2008-08-03
> **tesla.coil said:**
> ok lemme be precise ..this how i am doing it am in xp  i insert the livecd and select the 2nd option install it with in windows 3) it says its making an image 
4) the cd trap pops out asking me to remove and cd\dvd which i do

5) i get an option to do automatic reboot or select ill boot manually later

6)the system restarts (since i dnt select the 2nd option

7) at the boot menu i get 3 options server 03\xp\ubuntu ,i select ubuntu.

8) then it says kernel loaded and stuff, i see the ubuntu logo with progress bar moving from righ to left 

9) then i get the busybox :(

same prblm mentioned here
[http://ubuntuforums.org/showthread.php?t=876951](http://ubuntuforums.org/showthread.php?t=876951) 

lol am really pissed off at the moment  coz i v.badly wanted to install ubuntu and learn it:(

In that case uninstall Ubuntu using Windows Control Panel and then follow the link in my signature. A main difference in the procedure that I recommend is that you are not going to put the CD when you are in Windows. You are going to use the LiveCD directly without putting first into Windows. Check my sig for more details. And let me know if you have more questions.

---

### Post by tesla.coil on 2008-08-03
> **jualin said:**
> What I would do first is make sure Ubuntu is not installed. Check in Windows Control Panel and if Ubuntu is installed uninstall it first. Then i would recommend you checking the tutorial on my signature to install Ubuntu "Dual Booting with Windows" (Having windows and Ubuntu in the same machine)

i went to control panel i found ubuntu there in add and remove prgrms with 60 mb diskspace ..i guess i didnt uninstall it properly ill try installing again hope it works.

Actually am on 80 GB hDD with win xp in drive C and server 03 in E drive ..and other drives have other important data.. if i follow ur installtion procedure can i isntall the OS with in E or C drive with out LOSS OF data?

---

### Post by BGFG on 2008-08-03
Yeah, what Jualin said. :) Don't worry, the Live cd gives you several options for disk usage. One of them is to resize your partition using the unused diskspace currently on your harddrive. 
This is just me but id suggest you defrag your drive before you proceed. To ensure you have the max space available.
I'd suggest Defraggler by Piriform.

---

### Post by tesla.coil on 2008-08-03
> **BGFG said:**
> Yeah, what Jualin said. :) Don't worry, the Live cd gives you several options for disk usage. One of them is to resize your partition using the unused diskspace currently on your harddrive. 
This is just me but id suggest you defrag your drive before you proceed. To ensure you have the max space available.
I'd suggest Defraggler by Piriform.

ya ill try and let u knw guys thanks all for assistance...i ll defrag my drive E ..and try installing it..what i wanted to knw was ..shud i select automatic partioning or manual ?if i selct any of these too ..will it format my drive or will it just install the ubutun wiht in drive E that has server 03 in it?

---

### Post by jualin on 2008-08-03
> **tesla.coil said:**
> ya ill try and let u knw guys thanks all for assistance...i ll defrag my drive E ..and try installing it..what i wanted to knw was ..shud i select automatic partioning or manual ?if i selct any of these too ..will it format my drive or will it just install the ubutun wiht in drive E that has server 03 in it?

you need to select that during the installation. Remember to back up your data first just in case something goes wrong. Check the link in my signature "Dual Boot"

---

### Post by BGFG on 2008-08-03
> **tesla.coil said:**
> ya ill try and let u knw guys thanks all for assistance...i ll defrag my drive E ..and try installing it..what i wanted to knw was ..shud i select automatic partioning or manual ?if i selct any of these too ..will it format my drive or will it just install the ubutun wiht in drive E that has server 03 in it?

When you get to that point of the install, there's a graphical slider that shows your windows drive and you can basically toggle the slider to allot space to your Ubuntu.
As for manually, i did one yesterday, it's very powerful and actually quite easy but the drive hierarchy takes a little getting used to after windows. If you want to try that way do your reading beforehand. 
Since you're a beginner i suggest guided partitioning.
I'll check out Jualin's howto an post back here.

Yup, He pretty much has it all covered.

On another note:
I think we need an online video of a manual disk config for newbies.

---

### Post by tesla.coil on 2008-08-03
> **BGFG said:**
> When you get to that point of the install, there's a graphical slider that shows your windows drive and you can basically toggle the slider to allot space to your Ubuntu.
As for manually, i did one yesterday, it's very powerful and actually quite easy but the drive hierarchy takes a little getting used to after windows. If you want to try that way do your reading beforehand. 
Since you're a beginner i suggest guided partitioning.
I'll check out Jualin's howto an post back here.

Yup, He pretty much has it all covered.

On another note:
I think we need an online video of a manual disk config for newbies.


Thanks its working!!! but i cant change my resolution to 1024 !! its stuck on 800*600 with half the screen size i am on nvidia 7600GS card nw frm where do i get its drivers from?? any help regarding that

---

### Post by BGFG on 2008-08-03
Ital! 
Ok so now you need to go System>>Administration>>Hardware Sources and enable your nvidia driver.
let me know if that works.

---

### Post by tesla.coil on 2008-08-03
> **BGFG said:**
> Ital! 
Ok so now you need to go System>>Administration>>Hardware Sources and enable your nvidia driver.
let me know if that works.

lol my monitor is 8 yrs old LG studio works 552V i had to manually select the monitor frm the screens and graphics options :) selectd the one that supports 60 hz and its working now ..havent installed the drivers yet! shud i go to the nvidia site and get the linux drivers? am currently updating the ubuntu. Ubutu is GREAT great customization! never knew it has an inbuilt yahoo\msn messenger!

---

### Post by jualin on 2008-08-03
Just enable the drivers the way that BGFG told you in the post above.

---

### Post by BGFG on 2008-08-03
Yeah you can do that,.. or go to System>>Administration>>Synaptic Package Manager and search for nvidia. Click on the package, read the description and decide if you want it. I think the latest nvidia driver in the repositories is nvidia-glx-new. either way should work out fine...

when your'e done working hard at your install, Check out the cafe for some fun convo....

---

### Post by jualin on 2008-08-03
If that doesn't work then you will need to install the drivers manually. We'll tell you how if it doesn't work. Also Ubuntu is not a "customization" is a different operating system, not a better Windows Vista just a new operating system;). Good luck and Welcome to the family!

---

### Post by BGFG on 2008-08-03
> **jualin said:**
> If that doesn't work then you will need to install the drivers manually. We'll tell you how if it doesn't work. Also Ubuntu is not a "customization" is a different operating system, not a better Windows Vista just a new operating system;). Good luck and Welcome to the family!

I think he might have meant great 'at' customization. But either way dosn't matter. 
So yeah, What Jualin said, welcome to the fold...
(I'm talking like i've been here forever, but in actuality, i think i joined at the beginning of june :))

---

### Post by jualin on 2008-08-04
> **BGFG said:**
> I think he might have meant great 'at' customization. But either way dosn't matter. 
So yeah, What Jualin said, welcome to the fold...
(I'm talking like i've been here forever, but in actuality, i think i joined at the beginning of june :))

Nice, very nice!!! Joined a month ago and already helping people, amazing man! It took me like 6 months after I got used to Ubuntu to be able to give suggestions of how to fix problems. Nice thing you are doing man, we need more people like that, people willing to give back to the community. :)

---

### Post by tesla.coil on 2008-08-04
thanks guys everythings working fine now ! thanks to all !!! hope to learn more abt this wonderful OS:guitar:

---

### Post by BGFG on 2008-08-04
> **jualin said:**
> Nice, very nice!!! Joined a month ago and already helping people, amazing man! It took me like 6 months after I got used to Ubuntu to be able to give suggestions of how to fix problems. Nice thing you are doing man, we need more people like that, people willing to give back to the community. :)

Thanks man, linux in general is juat a great place to be. Plus in here just feel like family and friends. Hope to do like yourself and get some useful howto's out there.

So i'll see you guys around the forums! :popcorn:

---

### Post by jualin on 2008-08-05
> **BGFG said:**
> Thanks man, linux in general is juat a great place to be. Plus in here just feel like family and friends. Hope to do like yourself and get some useful howto's out there.

So i'll see you guys around the forums! :popcorn:

Of course, see you guys around ;). And I am glad everything worked out well. Enjoy your Ubuntu tesla!

---

