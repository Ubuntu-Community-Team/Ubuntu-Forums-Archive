---
title: "[Help]why i cant install Ubuntu linux 5.04"
date: 2005-07-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by yun555 on 2005-07-14
Hey,

i have a new Compaq Presario R4025CA Notebook Computer with AMD 64 3200+ cpu and ATI RADEON® XPRESS 200M IGP video graphics (128MB memory):
2.0GHz AMD Athlon™64 Processor 3200+ with Cool'n'Quiet™ Technology, 512KB L2 cache, up to 2000MHz system bus 
1024MB DDR SDRAM (2 x 512MB) at 333MHz
ATI RADEON® XPRESS 200M IGP video graphics with 128MB DDR (dedicated) video memory 

Today I tried to install ubuntu linux version 5.04 for AMD64/ET64T, but it was always dead and black screen after boot up and select the default install. 

so anyone knows what happen?  it's the problem about video card and how to fix it up?  

thanks.

---

### Post by fistfullofroses on 2005-07-14
[QUOTE=yun555]Hey,

i have a new Compaq Presario R4025CA Notebook Computer with AMD 64 3200+ cpu and ATI RADEON® XPRESS 200M IGP video graphics (128MB memory):
2.0GHz AMD Athlon™64 Processor 3200+ with Cool'n'Quiet™ Technology, 512KB L2 cache, up to 2000MHz system bus 
1024MB DDR SDRAM (2 x 512MB) at 333MHz
ATI RADEON® XPRESS 200M IGP video graphics with 128MB DDR (dedicated) video memory 

Today I tried to install ubuntu linux version 5.04 for AMD64/ET64T, but it was always dead and black screen after boot up and select the default install. 

so anyone knows what happen?  it's the problem about video card and how to fix it up?  

thanks.[/QUOTE]
 Personally I have never heard of such a problem... however, were I you I would personally start thinking of using either Sorcerer Linux or a 32bit distro until the next release of Ubuntu AMD64, because truthfully Ubuntu is the best 64bit distro, and should you choose any other you will be greatly dissapointed.

Sorcerer dls all your packes as source and builds them for your comp... so it works on almost any platform.

---

### Post by varunus on 2005-07-14
When do you see a black screen?  During the install or after the install is complete?  Its not clear from your post, sorry.

---

### Post by DancingSun on 2005-07-14
Was the install successful?  If you did the default install, you are aware that this will wipe out everything that was on the hard disk right?

In that case, you might as well do a re-install, might be faster than trying to find out what went wrong..

---

### Post by yun555 on 2005-07-18
no, still does not work.

when i chose default install, then display:
loading|install|...............
loading|install|.....
.....

and display black screen when loading video card drive (i guess).

maybe have to wait for next 64bit version.






[QUOTE=DancingSun]Was the install successful?  If you did the default install, you are aware that this will wipe out everything that was on the hard disk right?

In that case, you might as well do a re-install, might be faster than trying to find out what went wrong..[/QUOTE]

---

### Post by uniko on 2005-07-18
You could try diabling acpi for the install. Instead of default install, type 

expert acpi disable

Acpi modules has caused trouble on laptops before, you can do search for more information if you like.

---

### Post by jon_gunnar on 2005-07-18
[QUOTE=yun555]no, still does not work.

when i chose default install, then display:
loading|install|...............
loading|install|.....
.....

and display black screen when loading video card drive (i guess).

maybe have to wait for next 64bit version.[/QUOTE]
Just a shot in the dark. When I installed the AMD64 version I were sure something had gone wrong. Tried several times and just got the black screen as you do.

But then I just let it hang there and after a "LONG" time it just started up. In the end I found out that it was problems with one of the usb ports that did this.
And when I write long I'm talking 6-7 minutes or something.

---

### Post by damonw5 on 2005-07-18
I could be wrong, but I think you could try the "standard" 32-bit version of Ubuntu...

---

### Post by DancingSun on 2005-07-18
[QUOTE=jon_gunnar]Just a shot in the dark. When I installed the AMD64 version I were sure something had gone wrong. Tried several times and just got the black screen as you do.

But then I just let it hang there and after a "LONG" time it just started up. In the end I found out that it was problems with one of the usb ports that did this.
And when I write long I'm talking 6-7 minutes or something.[/QUOTE]

Yes, try the installation with minimal USB devices attached to the computer.

Also, you might want to check if it's your integrated video causing the problem.  Try running the AMD64 LiveCD and see if it works.  Search around the forums to see if there are other users with the same video solution having problems.

---

