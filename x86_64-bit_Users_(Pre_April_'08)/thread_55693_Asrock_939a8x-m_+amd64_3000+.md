---
title: "Asrock 939a8x-m +amd64 3000+"
date: 2005-08-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by XaRP1Sh87g on 2005-08-09
I'm starting this thread because I just upgraded my system to be 64bit.
I have a Asrock 939a8x-m mobo installed and am currently running the 64bit ubuntu edition.
I would like others with a similar setup to contribute their experiences, especially in regard to, what is most vital to ubuntu's succsess, it's (nearly) fool-profe installation and (almost automatic) configuration.

To start things off, what follows is my experience so far:

Installation goes pretty well, no critical problems*. Only when trying to install in "server-expert" mode, did the installer occasionally hang or even freeze. This did not happen when in plain "server"mode. (So I guess it was my fault...)

*The installer sadly fails to detect the onboard network chip->this means no networking, unless plugging in a 'pci' network-card.
I read somewhere that the 'tulip-driver' that comes with ubuntu is falty, and as a result it fails to detect the network-chip(on my specific board). Supposedly, this can be 'cured' by manually adding the vendor's device drivers to a custom-kernel's source tree and compiling it with those drivers. So far I have not been able to confirm this, mainly because I was not able to find any linux-specific drivers for asrock-mobos. Suggestions?

During boot-up process, the kernel complains about not being able to acess the hardware clock->time settings are messed up. May using a different driver to do this in a custom-kernel would help?

X works, but strange. I never had any problems with X+Ubuntu (except when trying breezy...). Though with the 64bit board, refresh-rates are not set correctly, as they were with 32bit. anyone who sees a relation here? I have also heard that there aren't any 64 drivers availible from vendors such as nvidia or ati yet, that support opengl.

For anyone reading this and wondering, these aren't any real problems that come up when using 64bit hardware. They are Ubuntu64 specific and only concern the installation/configuration process (ease of use) on an asrock 939a8x-m board.
It would be a shame to loose the benefit of the very limited amount of hassle that the Ubuntu installation offered under a 32bit environment, on a 64bit platform. So this thread should serve as a collection of expiriences with a certain system-setup, to ease the process of finding solutions to small but annoing problems people may have, until the devs get round to fixing things proper and making ubuntu64 feel like ubunutu again. :)

---

### Post by DancingSun on 2005-08-10
Well, make sure you report any bugs you encounter!

I also get the hardware clock complaint, but I don't think that's a problem as my times are still accurate.  This is *probably* due to a installation setting that I chose.  Since I dual boot with WindowsXP, I didn't want Ubuntu to access the hardware clock and mess up XP's clock, so I remember selecting something that disables Ubuntu's access to the hardware clock.  I vaguely remember this having to do with how Unix uses the UTC time, and Windows just uses the local time on the hardware clock.

About the graphics card drivers, if you check out NVidia and ATI's site, you will see that they do indeed offer 64-bit drivers.  Ubuntu has both NVidia and ATI (I believe) drivers in its 64-bit repositories, although they are not the latest releases.

When you say "refresh-rates are not set correctly", what do you mean by that?  It defaults to 60 Hz (which was what happened to me, also the default behavior for all of my Windows installations, from 95 - XP), or you cannot correctly setup the refresh rates of your monitor?  There's a thread in this forum where a user could not get X to setup the correct refresh rate range for his monitor no matter what you entered in xorg.conf.  Unfortunately, his case seems to be a rare incident as no one has been able to come up with an explanation.

---

### Post by XaRP1Sh87g on 2005-08-10
yes, i was refering to the 60hz setting. I know how to change that though, I just never had to when installing/running ubuntu (32bit), as it automatically set it to 85hz, which is the optimum for my monitor@resolution. Now I had to change the "HorizSync" option in xorg.conf to reflect my monitors values.

I have also configured X to use the "fglrx-driver" and set the "fglrx-module" to load at boot-up-time. (I found that it is included in the "linux-restricted-modules-package)
I have however not tested opengl yet.

Sadly I have found no solution to the "tulip-driver"problem with my board yet... :-?

---

### Post by DancingSun on 2005-08-10
[QUOTE=hungrigerhaifisch]yes, i was refering to the 60hz setting. I know how to change that though, I just never had to when installing/running ubuntu (32bit), as it automatically set it to 85hz, which is the optimum for my monitor@resolution. Now I had to change the "HorizSync" option in xorg.conf to reflect my monitors values.
. :-?[/QUOTE]
I have found out that if you comment out the refresh rate settings in xorg.conf, X will auto-detect the monitor's refresh rate settings, perhaps by default the 32-bit Ubuntu had that part commented out or deleted.

---

### Post by archimedes1981 on 2008-04-25
do you need to use apm=power-off noapic and acpi=off ?
i got 939a8x-m with 3200+
i used all the above for my system not to hang while using. but now it hangs on shutdown. i had this problem for quite a while now.
i have given up on ubuntu since even the latest release has given me this problem.
i am using mandriva for now which works fine and shuts down tidily as far as the above commands are added to the boot line.
is there any solution for this? i wish to use ubuntu but i'm not changing hardware!
thanks.

---

### Post by XaRP1Sh87g on 2008-04-25
> do you need to use apm=power-off noapic and acpi=off ?

Short answer, no. Never had to, never would want to.
Are you sure that your BIOS setting are correct?
My system has never hung on shutdown, no matter what OS/Linux-Distribution I use.
Very strange that this should only occur with Ubuntu...

On a side note, do you use the onboard soundchip? Does it work correctly?
Cause mine doesn't and I suspect that its down to faulty hardware.
I never used the chip in the past, because I have a 'proper' sound card from creative, so it doesn't bother me that much...

---

### Post by archimedes1981 on 2008-05-20
yes i use my onboard sound and ethernet. i don't know if any of my bios settings are incorrect, but they look fine to me. i thought all asrock motherboards had this problem ?!

---

### Post by XaRP1Sh87g on 2008-05-21
Why do you think that? Did you read it somewhere? If so, where?

Another thing you should do, is to check your logs.
See if you find anything suspicious regarding 'acpi' or 'apic'

Maybe post your findings, as well as your bios settings.
Your logs are stored on your filesystem under /var/log

Hope that helps...

---

### Post by archimedes1981 on 2008-05-21
noapic acpi=force apm=power_off : did the trick
however although the system shuts down completely i did not see the orange bar. How can i be sure that there is no harm done by forcing acpi ? is it safe?

---

### Post by XaRP1Sh87g on 2008-05-21
It depends on how you define 'safe'
I can't imagine it actually 'harming' your hardware, and if everything works, well I guess you can consider it safe...

---

