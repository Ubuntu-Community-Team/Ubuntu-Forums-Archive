---
title: "ups....problems   &quot;many lost ticks&quot;"
date: 2005-12-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by nortoncillo on 2005-12-16
im using 
Kernel 2.6.12-9-amd64-generic, 'coz after "apt-get upgrade" the >>kernel 2.6.12-10-amd64-generic<< was "kernel panic-ing", so i decide to start only with my good and old 2.6.12-9, but....

now the machine freezes each 3 or 4 days, the messages.log, says nothing exept:
XXXXX Losing some ticks... checking if CPU frequency changed.
XXXXX warning: many lost ticks.
XXXXX Your time source seems to be instable or some driver is hogging interupts

then i try the "fast clock CPU HOW TO", thats here in the forums, but nothing changed... 

im serving web, mail, tomcat, mysql, postgresql, for companies in my country, so.... i need to find out whats happening

can anybody give a hand??

ps: the hardware issue is discarted, everything have being ultra-tested, and for your info... the machine is, AMD64 3.2, 1Gb Ram Corsair, 2 x 200Gb Sata, MB K8Neo2 by MSI...

---

### Post by azcrumpty on 2005-12-16
[QUOTE=nortoncillo]im using 
Kernel 2.6.12-9-amd64-generic, 'coz after "apt-get upgrade" the >>kernel 2.6.12-10-amd64-generic<< was "kernel panic-ing", so i decide to start only with my good and old 2.6.12-9, but....

now the machine freezes each 3 or 4 days, the messages.log, says nothing exept:
XXXXX Losing some ticks... checking if CPU frequency changed.
XXXXX warning: many lost ticks.
XXXXX Your time source seems to be instable or some driver is hogging interupts

then i try the "fast clock CPU HOW TO", thats here in the forums, but nothing changed... 

im serving web, mail, tomcat, mysql, postgresql, for companies in my country, so.... i need to find out whats happening

can anybody give a hand??

ps: the hardware issue is discarted, everything have being ultra-tested, and for your info... the machine is, AMD64 3.2, 1Gb Ram Corsair, 2 x 200Gb Sata, MB K8Neo2 by MSI...[/QUOTE]
I can't provide help at this time, but I can say I feel your pain.  I google for the lost ticks and cpu hog phrases which identified the problem exists.  Google also provided solutions that did not work.  For me, it only does it when I load ndiswrapper to get the wireless driver.  Hopefully, someone with a clue will jump in and help.

---

### Post by nortoncillo on 2005-12-19
.... are all our AMD64 left alone in front of the Kernel Panic Ghost?...


 i see dead kernels....

---

### Post by nortoncillo on 2005-12-22
**...and time goes by...**

C&#180;mon i need a hand over here!

---

### Post by FluffyElmo on 2005-12-22
I really have no idea how to help this specific problem, but is there a reason you're using the *amd64-generic* kernel instead of *amd-64-k8*?

---

### Post by nortoncillo on 2005-12-27
no there are no special reason for that... 
do you think that switching to "k8" kernels would solve the problem?... 
if the answer is yes, could you explain why .. please [isn't lack of faith is just tham i'm a "lil coward bastard" ;) ]

regards

---

### Post by dna on 2005-12-27
Try this:
> While "Losing some ticks" may be a good thing for your pet, it's not something you'd like to see in your kernel logs. If you are seeing this message when booting your Linux 2.6 kernel, try using the ACPI PM timer by adding the "clock=pmtmr" to your kernel's boot options and see if that gets your clock ticking properly, again.



Google is your friend[http://www.google.com/search?hl=en&q=linux+Losing-some-ticks&btnG=Google+Search]("http://www.google.com/search?hl=en&q=linux+Losing-some-ticks&btnG=Google+Search")

---

### Post by nortoncillo on 2006-01-05
aparently the problem begins with the lack of suport for the Nforce4 chipset...
.. how come to this?... just reading the blog of this guy, who has the same problem, but with a sis chipset...
[http://pc-freak.blogspot.com/2004/11/warning-many-lost-ticks.html](http://pc-freak.blogspot.com/2004/11/warning-many-lost-ticks.html)

and solve the problem by adding the drivers to the kernel... 

sounds easy...

sounds

---

### Post by FluffyElmo on 2006-01-05
Have you tried the k8 kernel? It may still have this problem, but since it's compiled specifically for amd64 it may have better support for some of it's features?

There really isn't any risk. If for some reason it doesn't work you can just hit Esc at boot and select your old kernel in the boot menu.

---

### Post by nortoncillo on 2006-01-05
yes i've installed the 2.6.12-10-amd64-k8 kernel and no change at all

---

### Post by booru on 2006-01-11
I have the fast clock and keyboard repeat problem... if I leave my computer on for a day, the clock increases in speed significantly and the longer it stays on the more the clock races. Also, if I press some key once I sometimes get repeated characters for no apparent reason (it is not due to key repeat speed/delay trust me). Pressing eg. k will sometimes yield kkkkkkkkkkkkkk as you can imagine this is quite an annoying problem. When I came back from christmas vacation, my clock was running at 5 days ahead of time and each second (real life time) corresponed to 5 or so seconds on the clock. 

I have... 
[LIST]
[*] AMD64 X2
[*] Kernel 2.6.12-10-amd64-k8-smp, I have tried all kernels from 2.6.9. the problem perists. 
[*] I have the nForce4 chipset and the ASUS A8N-E motherboard
[*] tried the clock pmtmr with no success. 
[*] I have not found a solution to this problem...
[/LIST]

---

### Post by plg on 2006-01-11
Hmm, some of your problems look familiar. I also have NForce chipset, Asus A8N-SLI motherboard... and I've seen the "Lost ticks" message.

If I use a non-smp kernel I have no problems, so that's why I'm sticking to amd64-k8 and not amd64-k8-smp. Version 2.6.12 on both.

I have posted my problem in the thread "AMD64 SMP and NVIDIA 7800...".

/ Patric

---

### Post by nortoncillo on 2006-01-11
humm... 
...but why do i get the same problem using any kernel?, i mean, i've tested the k8 , amd64 generic, smp, etc... and the problem persist...

weird

---

### Post by Jave27 on 2006-01-11
I can't say that I noticed the "lost ticks" issue, but until a couple of days ago after upgrading my RAM and Video card, I was having the issue of the PC just randomly freezing on me.  When it happened during Linux, Windows, then finally while merely glancing around my BIOS settings, I realized it probably wasn't Ubuntu causing the issue.

To fix, I started changing the settings in the BIOS (when it wasn't freezing) from "Auto" to manual settings, particularly the CPU Frequencies & Voltage, and the RAM clock settings.  I probably don't have everything exactly correct, but if your system is experiencing hard freezes (like the mouse and everything quit moving, but the display remains on), then it is mostly likely a BIOS issue.  Update to the latest BIOS of your motherboard and start changing things (but be VERY careful - incorrect settings on some boards may fry things).  

Sorry I can't be more specific, but getting hardware to work properly together is still a bit of voodoo science at times.

---

### Post by nortoncillo on 2006-01-11
i've checked de bios setup, and turned everything to manual (haven't realize that were in auto), and up to this minute there are no "lost ticks" messages... that is good for me and my users

but, the idea is not to turn off the "cool n' quiet" feature forever.... i mean, it's a goodfeature after all isn't

so 

is there a "SOLUTION" for this issue?

a definitive one

---

### Post by Jave27 on 2006-01-11
My understanding is that the Cool-n-Quiet only functions if you leave the CPU frequency setting to **Auto **(and have Cool-n-Quiet to Enabled of course).  It might be just the memory settings that need manual adjustments.  ASUS has released a new BIOS beta version at [their site]("http://www.asus.com") (1018.001), which I haven't tried yet.  You can find a lot of stuff about that board at [http://forums.viaarena.com](http://forums.viaarena.com).

---

### Post by Jave27 on 2006-01-11
Sorry, just re-read and realized you're not using the same board.  :-)

Anyway, try updating the BIOS to the latest anyway, reset the CMOS using the jumper on your board (apparently that fixes a lot of stuff sometimes), then start tweaking items one at a time.

---

### Post by nortoncillo on 2006-01-11
[QUOTE=Jave27]Sorry, just re-read and realized you're not using the same board.  :-)
[/QUOTE]

use to happen....


well up to this minute, there are no lost ticks in sight, will see if they appear again...

by the way, could solve the problem compile the kernel?, and add some special funcion or support?

i've compiled only my home machine (a P3), never an AMD64

---

### Post by Jave27 on 2006-01-11
> by the way, could solve the problem compile the kernel?, and add some special funcion or support?

I really don't think it's a Linux issue, since I had the exact same problem in Windows, and it also locked up once while I was browsing through the BIOS settings.  I'm positive that my problem at least was strictly hardware related.  Using a different kernel wouldn't have solved anything.  I just upgraded to the latest BETA version of the BIOS and it seems to be working fine for me now as well.

---

### Post by nortoncillo on 2006-01-12
well is evident that the issue was the Bios tweaking


so, i'll be testing different tweaks... to isolate the fail

---

### Post by argh on 2006-05-01
Did you solve your problem? Was it bios related?
 I have the exact same hardware and kernel version. I got the 'lost ticks' error messages after installing the latest nvidia graphic driver. Had to unload it to make the system normal again.

---

### Post by nortoncillo on 2006-05-02
i solved the problem tweaking the bios, i mean setting every "cool 'n quiet" feature off.....

it worked for me, but im not totally satisfy with the solution....

---

