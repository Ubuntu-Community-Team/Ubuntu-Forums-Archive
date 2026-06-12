---
title: "64 bit hangs on install"
date: 2006-01-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by WindowWasher on 2006-01-23
I've tried to scan the forum for similar posts but with the frequent "server is too busy" error it's been frustrating. hopefully I'm not being repetitive.

I've been using Ubuntu for several weeks and thought I'd install the 64 bit version on a new desktop. I downloaded the ISO from ubuntulinux.org and did the checksum thing. On install it hung at 72% while setting up the file system. After a restart it hung at 54%. A third try made it to 100% and then froze on a blue screen right after that. I burned a new copy of the CD and tried again with similar results.

I have a feeling it might be related to a lack of drivers for my motherboard but that is just a theory. If I can't get in to install I can't update the drivers.

I have an Asus A8N-VM CSM motherboard with NVIDIA GeForce 6150 + nForce 430 and Integrated GeForce6 GPU with an Athlon 64 3700 CPU.

I haven't tried the 32-bit version on this box yet but given the comments in other forum maybe I really don't want the 64 bit.

Any suggestions?

---

### Post by skylark on 2006-01-23
[QUOTE=WindowWasher]On install it hung at 72% while setting up the file system. After a restart it hung at 54%.[/QUOTE]

As a first step I'd run some diagnostics on your new system to rule out any hardware issues... at least test the integrity of your hard-disk since the install seemed to be having issues when creating your filesystem. You might want to check out something like [http://www.ultimatebootcd.com/]("http://www.ultimatebootcd.com/") which has a range of diagnostics to choose from. A memory test never hurts either (eg through memtest86).

---

### Post by chindii on 2006-01-24
I had trouble with the ISO I downloaded from [www.abuntulinux.org](www.abuntulinux.org). When I burned the iso using nero I would get a non-fatal error dealing with block size, so I resorted to bittorrent and got a distro which seemed good.

I also had to burn the cd at 8x, because at a faster speed, there were problems reading the cd. That sounds like a  media or hardware problem, but you might be experiencing something similar.

I am running the 64bit version on a celeron-based machine, the only problems I am seeing now are some artifacts on my video display. Other than that, I've had a good experience.

---

### Post by dsierpin on 2006-01-24
I had this same problem when installing.  I passed noapic nolapic as boot options and that solved it for me:cool:

---

### Post by WindowWasher on 2006-01-24
Thanks for the feedback. I'll try the *nolapic *option when I get home - although I don't know what that means. Anyone able to explain what it does? I did verify my hardware (by installing Windows xp 64 - hope that isn't a taboo word here). The system runs fine but just can't get Ubuntu installed. I did manage to get Suse 10.0 installed but it won't boot - just freezes. IMHO, it really shouldn't be this difficult to get a viable GNU/Linux install. Although, to be fair, I have been using a 32 bit install with little difficulty (unless you want to use wireless - but that's another story).

UPDATE: I tried the nolapic and noapic options and it made it much further. There were some errors related to drivers (sorry I didn't copy them down) I think but it kept loading. However, in the end it said the xserver failed to load and then froze. I also tried Dapper thinking it might have more up to date drivers but it too failed to install. I've got Breezy on several laptops and my old desktop running fine but it doesn't seem to like my new computer at all.

---

### Post by dsierpin on 2006-01-25
WindowWasher-

Check out [LinuxQuestions.org]("http://wiki.linuxquestions.org/wiki/APIC") for answers to just about anything linux.  I had no idea what apic / lapic were until I went here.  I just knew that disabling them helped me.  As for the xserver failing to load, that's beyond me.  You might want to get the install cds from ShipIt.  

I installed the 32-bit version on my machine and it's been working great.  I hear tell that the performance increase with the 64-bit kernel is negligible, and it seems to me that the packages for it and the support are not at the level of the 32-bit ubuntu yet.  Good luck!

---

### Post by WindowWasher on 2006-01-25
Okay, I retried installing with the 32-bit version. It hangs unless I use the nolapic and noapic. It installs the base and then restarts. While installing packages I get this error several times...

[4294763.870000] drivers/usb/input/hid-core.c: can't resubmit intr, 0000:00:0B:04/input 0, status -19

They are all similar but with different numbers in the []. After it finishes installing the packages I get an ubuntu login but before I can I get more of the same error text and then a message that the xserver failed to start and that it is likely it is not set up correctly and then more repeats of the text above. It askes if I want to view a log and then says the x server is now disabled. Restart GDM when it is configured correctly and then the error text continues to repeat.

Any one able to solve this mess will certainly build good karma.

---

### Post by skylark on 2006-01-25
I agree that this just shouldn't happen with new hardware.

Have you googled for A8N-VM and linux? I came across a few pages, this one looked promising: [http://quaggaspace.org/a8nvm/](http://quaggaspace.org/a8nvm/)
It looks complicated but check out the first section about ACPI, it might be related to your issue.

I'd still personally run this hdd diagnostics just in case as it only takes an hour or so (even if win64 was running stable).

---

### Post by dsierpin on 2006-01-26
Just a guess here, but the problem might be your video card.  The "nv" driver doesn't always work for everybody.  I got that same message when I was working on my video card and installed a bad driver:

> After it finishes installing the packages I get an ubuntu login but before I can I get more of the same error text and then a message that the xserver failed to start and that it is likely it is not set up correctly and then more repeats of the text above. It askes if I want to view a log and then says the x server is now disabled. Restart GDM when it is configured correctly and then the error text continues to repeat.

So, you might want to try [tseliot's HOWTO]("http://www.ubuntuforums.org/showthread.php?t=75074&highlight=HOWTO+nvidia+driver") for the latest NVIDIA driver.

In the meantime, you can install the "vesa" driver to get you into Ubuntu fairly easily.  Just boot into the recovery mode, and

```
dpkg-reconfigure xserver-xorg
```

I followed the prompts, choosing mostly the defaults.  But when it asks you to pick the driver you want, choose vesa.  Hope this helps!

---

### Post by WindowWasher on 2006-01-27
[QUOTE=dsierpin]Just a guess here, but the problem might be your video card.  The "nv" driver doesn't always work for everybody.  I got that same message when I was working on my video card and installed a bad driver:[/QUOTE]

I'm using the onboard video at the moment rather than an actual video card (one reason I bought this board). Still, assuming the video card (or possible the NIC - thanks Skylark for the link - that does sound a lot like my problem) is the problem, how do I solve it with different drivers if I can't get Ubuntu to even install. Sorry if this is a dumb question but don't I have to install Ubuntu first before I can start to tweek it? I've tried all the tricks I've been able to find and everytime I get a unusable computer. It's kind of sad but at the moment Windows is the only OS I can get to run.

I thought perhaps Dapper might have newer drivers and be a better shot at a successful install but it too just crashed my system.

Thanks for all the advice but for the moment I think I'm stuck with a Windows only system. Hopefully when Dapper realeases I can once again start using Ubuntu again. On the bright side I do have it on my laptop...

---

### Post by dsierpin on 2006-01-28
> It installs the base and then restarts.
> After it finishes installing the packages I get an ubuntu login
> don't I have to install Ubuntu first before I can start to tweek it?

It sounds like you already have Ubuntu installed, you just can't get the GUI working.  Have you tried the vesa driver?  It's really easy to install (probably takes about 2 minutes) and you could at least discount the video card as a problem if it doesn't work.

---

### Post by S.nazari on 2006-01-28
I have exactly the same motherboard and the same processor. I did try the install with the options #boot # linux noacpi nolacpi, and I managed to install ubuntu. But now I can't access the gdm since xserver-xorg is unable to detect a video card. This is also the same case in live cd.

---

### Post by jim-fwb on 2006-01-28
I had the same issues with the live and install CD's (ATI 200 express onboard video) . dpkd-reconfigure and selection vesa does work.  What has worked even better (as I learned from another post elsewhere, and have used) is to install as a server, followed by "sudo apt-get update" and "apt-get dist upgrade" at the CLI.  Lastly, "apt-get install ubuntu-desktop" yields a functional desktop without having to reconfigure the x-server. Had to use it after fritzing things up playing with Etch for AMD 64 (which yielded a glorious 320 by 240 desktop. O joy).

---

### Post by WindowWasher on 2006-01-30
[QUOTE=dsierpin]It sounds like you already have Ubuntu installed, you just can't get the GUI working.  Have you tried the vesa driver?  It's really easy to install (probably takes about 2 minutes) and you could at least discount the video card as a problem if it doesn't work.[/QUOTE]

Well, not any more. I ended up frying my dual boot and nothing worked so I reformatted the whole thing and started over. Windows is working again and I'm leery about installing Ubuntu as I don't want to fry everything again.

However, you are probably right in that I did get it installed and just couldn't get the GUI (is that the xserver?) working. It certainly didn't install nicely. I had to restart it several times, but eventually did force it with the nolapic noapic options (still not sure what that did) but got all the errors I previously mentioned.

For the record I did try the server install but it too failed. Although that might have been before I learned about the nolapic options. I guess I'll just have to try again with some combination of the suggestions given. BTW, thanks for all the help. This is a great community. I'm anxious to get Ubuntu running on this machine as that was the main reason I bought it. I don't particularly hate Windows but I'd like to use Linux as my primary OS.

---

### Post by Stereotypical Rage on 2006-01-30
WindowWasher: Just out of stupid curiosity, have you tried to boot into recovery mode with Breezy or Dapper? I do believe I had the same problem as you do/did with AMD64 as I am. I moved over to 32 bit Breezy, then later 32 bit Dapper.

I'm currently running in recovery mode, nearly flawlessly. (No clue what I'm doing really. :lol:)

---

### Post by WindowWasher on 2006-01-30
[QUOTE=Stereotypical Rage]WindowWasher: Just out of stupid curiosity, have you tried to boot into recovery mode with Breezy or Dapper? I do believe I had the same problem as you do/did with AMD64 as I am. I moved over to 32 bit Breezy, then later 32 bit Dapper.[/QUOTE]

No, I did not try the recovery mode option. I'm not even sure I know how to do that. Assuming I can get something to install again and at least get a prompt, what would I do to run in recovery mode? Would that allow me to update the drivers that may be the root of my problems or are you pretty limited in that mode?

---

### Post by Stereotypical Rage on 2006-01-30
[QUOTE=WindowWasher]No, I did not try the recovery mode option. I'm not even sure I know how to do that. Assuming I can get something to install again and at least get a prompt, what would I do to run in recovery mode? Would that allow me to update the drivers that may be the root of my problems or are you pretty limited in that mode?[/QUOTE]
Upon boot up, you'll see "Press the ESC to enter the GRUB menu". Hit the ESC key and you can't miss the option of "recovery mode" in there.

So far, from what I've noticed, it's not that limited.(Still a newbie, I be.) Though a lot of services are bypassed.(Apache, mySQL, Update-Notifier) So I don't know the specifics of what is being run during recovery mode. However being this newbie that I am. I use this mode daily/whenever my machine needs a reboot. I can't boot Ubuntu normally without it freezing at the GDM screen. I know I really need to figure out why it freezes. I did finally get around to asking (in a new topic) what loads in Recovery Mode vs. a Normal Mode.

---

### Post by WindowWasher on 2006-02-02
Oh, that recovery mode. Yes, I know what it is. Unfortunately I have reformatted my drive and tried to start over. Still no luck. Using the install as server option I can get as far installing base packages but upon reboot it gives a bunch of errors and then drops to a shell and I don't have a clue what to do from there. It's not even a regular prompt but a #. I've never seen that before.

I'm about to give up on this. I got Windows installed so I can use the computer. Maybe I'll just wait for Dapper and see if it solves my problems. Still, I'm stubborn and would like to solve this.

Thanks to all who have provided so much helpful feedback. I'm sure the anwer is here somewhere, I just have to figure out how to make it work.

---

### Post by janie on 2006-02-03
I am in the process of trying to get a fully functioning Linux desktop and I am just about to start trying to get the breezy badger going but I read your thread and I may have part of the answer. If you go to the NVIDIA website and download the appropriate Linux driver (There is a 64 bit one) and then when you get to the command line, switch to being a superuser, you follow the directions in the README file and it loads the right kernal interface. I have had to do that for SUSE before it worked properly (I have a 6600 Geforce NVIDIA card).
I hope that helps
Janie

---

### Post by ruudiculus on 2006-02-04
Exactly Janie, and for the ATI video card users such as *jim-fwb* use the 64 bit installer from the ATI site (you can also use the zv6251EA howto I wrote: click the link below this message).

And for the noapic and nolapic options: these are options that tell the bootloader not to boot linux with the Advanced Power Interface Controller (APIC) enabled. I guess if you do this you *might* not be able to use CPU speed throttling, hibernation modes etc.

As for the original error WindowWasher encountered: it was something with the usb driver right? I don' t see any connection with the APIC, but if it works with those boot options (noapic, nolapic) just use them ;) Maybe you' ll find out afterwards (in graphical mode, aka GUI (Graphical User Interface) run by GDM (Gnome Desktop Manager) using the xserver) :D 

Good luck!

---

### Post by ruudiculus on 2006-02-05
Let me correct myself before others do :rolleyes: :

APIC means Advanced Programmable Interrupt Controller
LAPIC means Local Advanced Programmable Interrupt Controller
[I]
source: [http://en.wikipedia.org/wiki/Intel_APIC_Architecture]("http://en.wikipedia.org/wiki/Intel_APIC_Architecture")[/I]

What I thought it was is called Advanced configuration and Power Interface or ACPI, which take care of the power management of a computer.
*source: [http://www.acpi.info/]("http://www.acpi.info/")*

So, no confusion anymore :-D

---

