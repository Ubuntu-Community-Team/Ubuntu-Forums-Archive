---
title: "Athlon-64 X2 with 32-bit SMP kernel?"
date: 2005-10-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by Kirk Wolf on 2005-10-20
I want to build a new computer and use an AMD-64 X2.  For now, I want to stick with a 32-bit kernel.  Can I use a 32-bit SMP kernel and support the dual core AMD-64?   

Thanks,
Kirk Wolf

---

### Post by Sutekh on 2005-10-20
I have the X2 3800, and am using the k7-smp kernel.  I am planning on installing 64bit Ubuntu, but for now 32bit is working great for me.  I only have one issue with the kernel I'm using, and that is I don't seem to have powernow/frequency scaling working.

---

### Post by Kirk Wolf on 2005-10-21
Thanks for sharing! 

Can you comment on performance?
Have you had any problems with apps or drivers (tricky things like codecs / multimedia stuff?)

Thanks, 
Kirk

---

### Post by Sutekh on 2005-10-21
Okay, using the standard i386 kernel worked fine, and installing things like NVIDIA drivers and codecs (using EasyUbuntu/Automatix) worked fine.  I installed the k7-smp kernel and got a large boost in performance, which you'd expect seeing as both cores are being used.  Ubuntu loads so quick I don't even see the splash screen :cool: 

I haven't run into any issues yet, but I've only been using Breezy for about a week (and Linux about 3 weeks).  I haven't got cpu scaling (powernow) working, but I haven't really tried yet.  I believe that powernow is automatically installed when you use 64-bit Ubuntu.  I want to try installing the 64-bit version soon, but haven't had time yet.

There's no reason why the 32-bit SMP kernel would create problems on an AMD64.  I mean after all the CPU is designed to run 32-bit programs, and 32-bit WinXP was never a problem.  Aside from typical windows problems ;)

What processor are you considering?

---

### Post by Kirk Wolf on 2005-10-22
Thanks for the info.  I'm also considering an X2 3800.  Seems like good bang/buck.

---

### Post by jecos on 2005-10-22
[QUOTE=Sutekh]I have the X2 3800, and am using the k7-smp kernel.  I am planning on installing 64bit Ubuntu, but for now 32bit is working great for me.  I only have one issue with the kernel I'm using, and that is I don't seem to have powernow/frequency scaling working.[/QUOTE]

For your cpu's sake don't run a k7 kernel atleast run 686 which is supposed to have more features..
I have an AMD64 and would never run k7 cause thats for an Athlon XP.

---

### Post by RAOF on 2005-10-23
[QUOTE=jecos]For your cpu's sake don't run a k7 kernel atleast run 686 which is supposed to have more features..
I have an AMD64 and would never run k7 cause thats for an Athlon XP.[/QUOTE]
Um.  In what way is the 686 kernel meant to have more features than the k7 kernel?  The 686 kernel is tuned to run on processors at least pentium 2 class, ie practically everything.  The K7 kernel is tuned for the cpus based on the amd k7 core including, yes, the Athlon XP.  Either way, with an amd64 you'd actually be after a k8 kernel ('cause that's the core the cpu has), but failing that the k7 core is probably closer to the design of your cpu than that of a generic pentium2 class core.

---

### Post by Kirk Wolf on 2005-10-23
Thanks everyone for all of the assistance.  Of course, I will eventually want to use a 64 bit SMP kernel, but initially I want to stick with 32 bit.   For 32-bit SMP, it sounds like the k7-smp kernel is the best option (?)

Thanks.
Kirk

---

### Post by bahbo on 2005-10-23
I'm a bit confused, and had the following question.
If I want a basic i-386 system, can I also use a 64b kernel?  
Can I use a amd64-k8 kernel without upgrading to all the 64 bit libraries?
I was thinking of doing a basic install, and then changing the kernel.
Thanks,
Ric

---

### Post by Sutekh on 2005-10-23
[QUOTE=bahbo]I'm a bit confused, and had the following question.
If I want a basic i-386 system, can I also use a 64b kernel?  
Can I use a amd64-k8 kernel without upgrading to all the 64 bit libraries?
I was thinking of doing a basic install, and then changing the kernel.
Thanks,
Ric[/QUOTE]

Basically no.  If you want to do a basic 32bit installation, from the i386 install CD, you can't later install a 64bit kernel on that installation.  

If you want to use the amd64-k8 kernel you need a separate 64bit installation.

---

### Post by RAOF on 2005-10-24
[QUOTE=Sutekh]Basically no.  If you want to do a basic 32bit installation, from the i386 install CD, you can't later install a 64bit kernel on that installation.  

If you want to use the amd64-k8 kernel you need a separate 64bit installation.[/QUOTE]

Why not?  You could actually build your own 64bit k8 kernel, and that would work with a 32bit install.  It's the other way round doesn't work - you can't have a 64bit install with a 32bit kernel.

I'm not sure whether it would be **faster** or not - it depends how much a 64bit-32bit state change takes on the processor.  Also, you may not be able to trick apt into getting the 64bit kernel for you, but if you built your own...

---

### Post by Sutekh on 2005-10-24
[QUOTE=RAOF]Why not?  You could actually build your own 64bit k8 kernel, and that would work with a 32bit install.  It's the other way round doesn't work - you can't have a 64bit install with a 32bit kernel.

I'm not sure whether it would be **faster** or not - it depends how much a 64bit-32bit state change takes on the processor.  Also, you may not be able to trick apt into getting the 64bit kernel for you, but if you built your own...[/QUOTE]

Hey that's not a bad point.  Have you tried doing this?

---

### Post by RAOF on 2005-10-24
Nope.  I'm running a 64bit Breezy here, and I can't be bothered to install a 32bit version just to try that :)

However, I see no reason why it wouldn't work.  Plus, it'd be harmless even if it didn't.

---

### Post by Sutekh on 2005-10-25
Fair enough, I'll give it a whirl. :)

---

### Post by jecos on 2005-10-25
[QUOTE=RAOF]Um.  In what way is the 686 kernel meant to have more features than the k7 kernel?  The 686 kernel is tuned to run on processors at least pentium 2 class, ie practically everything.  The K7 kernel is tuned for the cpus based on the amd k7 core including, yes, the Athlon XP.  Either way, with an amd64 you'd actually be after a k8 kernel ('cause that's the core the cpu has), but failing that the k7 core is probably closer to the design of your cpu than that of a generic pentium2 class core.[/QUOTE]

with 686 image 
CONFIG_M686=y

with k7 image
CONFIG_MK7=y

Neither one sets CONFIG_MK8=y and running K7 will limit the K8's features to K7's.

---

### Post by RAOF on 2005-10-25
[QUOTE=jecos]with 686 image 
CONFIG_M686=y

with k7 image
CONFIG_MK7=y

Neither one sets CONFIG_MK8=y and running K7 will limit the K8's features to K7's.[/QUOTE]
But will running 686 limit the K8's features to that of a generic 686 processor?  Either way, you're not getting a kernel tuned to the specific nuances of the k8 core :)

---

### Post by casfindad on 2005-10-28
Hi,

I too am thinking about building a system with the X2 3800+ processor, but using the 32-bit version of Ubuntu. As a newbie (I've successfully installed Ubuntu/Kubuntu on an old PC, and Ubuntu on a dual-boot iMac), would someone please tell me how exactly I would install the kernel with multi-core support?  Do I install the x86 distro, then install the K7-smp kernel using Synaptic/Adept? Is the single core kernel overwritten/deleted?

Thanks!

---

### Post by malmjako on 2005-10-29
[QUOTE=casfindad]Do I install the x86 distro, then install the K7-smp kernel using Synaptic/Adept? Is the single core kernel overwritten/deleted?[/QUOTE]
Yes, that is the way to do it.

The single core kernel is a separate deb-package and will be neither overwritten nor deleted. If, after booting from your newly installed kernel, all is working well you can then remove the single core kernel package, but unless space is an issue you might consider keeping it just to be safe (because you know it's working).

On a side note: I'm thinking of getting a 64 bit dual-core system (Dell 5150c, Pentium D 830, 945G Express chipset). Why would you want to run a 32 bit operating system on a 64 bit computer? Is 64 bit Ubuntu not very stable?

---

### Post by RAOF on 2005-10-30
[QUOTE=malmjako]...
On a side note: I'm thinking of getting a 64 bit dual-core system (Dell 5150c, Pentium D 830, 945G Express chipset). Why would you want to run a 32 bit operating system on a 64 bit computer? Is 64 bit Ubuntu not very stable?[/QUOTE]
It's just as stable, but there are a couple of things which don't work as well, most notably flash.  Macromedia have not released a 64bit flash installer, so flash is annoyingly difficult to set up.

Basically, there's a bit more frustration involved in some things.

---

### Post by matw on 2005-10-30
FreeNX is another example. With the i386 install, FreeNX is easy to install and runs fine. With the AMD64 insall, FreeNX must be build from source, and the server crashes when I try to use it.

---

### Post by malmjako on 2005-10-31
Are problems only related to closed source, binary applications, which haven't gotten around to distribute 64 bit Linux versions yet? No problems with open source software?

---

### Post by RAOF on 2005-10-31
[QUOTE=malmjako]Are problems only related to closed source, binary applications, which haven't gotten around to distribute 64 bit Linux versions yet? No problems with open source software?[/QUOTE]
Not quite.  There is still some open source stuff which won't even compile properly on 64bit breezy.  I'm thinking of cedega/wine in particular.  They have a bit of an excuse, though - it would be pointless to build a 64bit wine binary, 'cause it wouldn't actually run anything ;).

---

### Post by casfindad on 2005-11-01
[QUOTE=malmjako]Yes, that is the way to do it.

The single core kernel is a separate deb-package and will be neither overwritten nor deleted. If, after booting from your newly installed kernel, all is working well you can then remove the single core kernel package, but unless space is an issue you might consider keeping it just to be safe (because you know it's working).

On a side note: I'm thinking of getting a 64 bit dual-core system (Dell 5150c, Pentium D 830, 945G Express chipset). Why would you want to run a 32 bit operating system on a 64 bit computer? Is 64 bit Ubuntu not very stable?[/QUOTE]

Hi, I'm back! Thanks for your reply, malmjako. Sorry for not replying sooner, I was swamped at work.

Re: your questions about 32 bit on a 64 bit computer, there are many threads on this issue that discuss this and echo what other posters in this thread are saying. Here are some examples:

[http://ubuntuforums.org/showthread.php?t=82395]("http://ubuntuforums.org/showthread.php?t=82395")
[http://ubuntuforums.org/showthread.php?t=76856]("http://ubuntuforums.org/showthread.php?t=76856")
[http://ubuntuforums.org/showthread.php?t=54557&highlight=64+bit+dual+boot]("http://ubuntuforums.org/showthread.php?t=54557&highlight=64+bit+dual+boot")

In the end it comes down to individual needs and taste. From what I've been reading on these forums, no one has gotten wine to compile successfully in the 64 bit environment. I need wine to run a propietary windows application for my work. I also like having it to try the occasional windows-compatible application (e.g. Picasa). If it weren't for the wine (and flash) incompatibility, I would use 64 bit. I agree with those who encourage early 64 bit adoption in order to  stimulate developers to write applications that run/take advantage of 64 bit processing, and I feel guilty over my plan to use 32 bit. But the bottom line is that there are far fewer applications written for 64 bit, and if you need one of the 32 bit ones you're stuck. (Unless you can install with chroot. From what this newbie understands, that's not possible with wine.)

I am considering a 32/64 bit dual boot system, though, just to see the speed differences. In the end, I think that I'll see the biggest speed boost by using a dual core processor (even with 32 bit ubuntu) in the linux box I'm planning, as I do a lot of multi-tasking.

Regarding installing the smp kernal over the single-processor one, how do I instruct the machine to use the correct one at bootup? Will I be given a choice at bootup or login, similar to choosing kde vs. gnome? How will I know if my machine is actually using the correct kernel?

casfindad

P.S. You have a fine looking kid, malmjako! I'm the proud poppa of a 2 yo girl.

---

### Post by malmjako on 2005-11-02
[QUOTE=casfindad]Regarding installing the smp kernal over the single-processor one, how do I instruct the machine to use the correct one at bootup? Will I be given a choice at bootup or login, similar to choosing kde vs. gnome? How will I know if my machine is actually using the correct kernel?[/QUOTE]
GRUB will give you a list of all (or up to a certain number, as configured in /boot/grub/menu.lst, default is all) kernels installed. To have the kernel last booted automatically selected, edit the first option in /boot/grub/menu.lst (instructions in the file).

That's a shame wine is not working on 64 bit Ubuntu... I need it for Internet Explorer as I'm doing web development and want to see what the web pages look like in the browser that most visitors use. Anyway, getting a new computer is still a bit distant, so maybe things change till then.

Ps. Yea, isn't he a cutey! He's two too.

---

### Post by RAOF on 2005-11-02
Actually, you **can** get wine to run (but not compile) on Breezy64.  You just need to install a 32bit binary .deb.  See [here]("http://http://www.ubuntuforums.org/showthread.php?t=82676&highlight=wine+breezy+force-architecture").  One less reason not to 64bit :)

---

### Post by casfindad on 2005-11-02
[QUOTE=RAOF]Actually, you **can** get wine to run (but not compile) on Breezy64.  You just need to install a 32bit binary .deb.  See [here]("http://http://www.ubuntuforums.org/showthread.php?t=82676&highlight=wine+breezy+force-architecture").  One less reason not to 64bit :)[/QUOTE]

Wow, RAOF, that would be fantastic! I'm assuming that I could then install a non-64 bit windows-compatible application and it would run (assuming it works with wine).

Quick question (off topic, I know): In your estimation, how much harder is it to run 32-bit apps under chroot vs. running 32-bit ubuntu? On the forums, I read conflicting tales about how easy/difficult it is to get chroot running properly. If I do go with chroot and link my 32-bit apps, can I run these apps simply by selecting them from the applications menu? Can I run both 32-bit and 64-bit versions of firefox on the same install (using the former for when I need flash)? Also, will I have both 32-bit and 64-bit versions of synaptic running, in order to install packages for the two different environments?

casfindad

P.S. Your link needs editing. It has one too many "http://"s in it. When I clicked it took me to the M$ home page!

---

### Post by riggsd on 2005-11-02
[QUOTE=casfindad]P.S. Your link needs editing. It has one too many "http://"s in it. When I clicked it took me to the M$ home page![/QUOTE]

Busted browsing the Ubuntu forums with Internet Explorer!  :mad:

---

### Post by casfindad on 2005-11-02
[QUOTE=riggsd]Busted browsing the Ubuntu forums with Internet Explorer!  :mad:[/QUOTE]

Actually, no. I use Firefox or Safari, mainly. I only have IE installed on my linux box for apps (e.g. Picasa) that require it, but I don't use it for browsing. Go ahead and try the link in question from Firefox; I predict you'll end up with M$. I just tried it again in Firefox on my Mac, same result. :D

---

### Post by RAOF on 2005-11-02
[QUOTE=casfindad]Wow, RAOF, that would be fantastic! I'm assuming that I could then install a non-64 bit windows-compatible application and it would run (assuming it works with wine).

Quick question (off topic, I know): In your estimation, how much harder is it to run 32-bit apps under chroot vs. running 32-bit ubuntu? On the forums, I read conflicting tales about how easy/difficult it is to get chroot running properly. If I do go with chroot and link my 32-bit apps, can I run these apps simply by selecting them from the applications menu? Can I run both 32-bit and 64-bit versions of firefox on the same install (using the former for when I need flash)? Also, will I have both 32-bit and 64-bit versions of synaptic running, in order to install packages for the two different environments?...[/QUOTE]
Yup, I've got foobar2000 running and had the iTunes 5 install not complete ;)

I've never used a chroot, but AFAIK the essential idea is that you install an entire 32bit system in parallel with your 64bit one, so yes, you will have both 32bit & 64bit synaptic running, and you will be able to parallel install 32bit & 64bit versions of stuff.

If you're only after flash, though, I've just got the [32bit version of firefox 1.5rc1 running without a chroot]("http://www.ubuntuforums.org/showthread.php?t=84732").  Yay :KS

---

### Post by riggsd on 2005-11-03
[QUOTE=casfindad]Actually, no. I use Firefox or Safari, mainly. I only have IE installed on my linux box for apps (e.g. Picasa) that require it, but I don't use it for browsing. Go ahead and try the link in question from Firefox; I predict you'll end up with M$. I just tried it again in Firefox on my Mac, same result. :D[/QUOTE]

I stand corrected. Firefox executes its action for "keyword:http", which takes me to a [google search for 'http']("http://www.google.com/search?q=http"). Strangely, Microsoft is the #1 hit for 'http'...not the IETF, W3C, Apache, but Microsoft.  :confused:

---

