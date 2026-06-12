---
title: "if you have a iMac Intel..."
date: 2006-05-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by ReviewSpin on 2006-05-21
Do I use the Mac version (the one for PowerPC) or the PC version...since it is built for Intel/AMD processors. Just wondering.

---

### Post by henriquemaia on 2006-05-21
The PC version for Intel/AMD. If iMac can now run windows (compiled for machines with Intel/AMD processors), same applies for Linux.

PowerPC is for the PowerPC family of processors.

Hope this helps.

---

### Post by ReviewSpin on 2006-05-23
Yeppers, that does help. Thanks.

---

### Post by Ptero-4 on 2006-05-23
You need to use the x86 version. But before using it you need:
1) rEFIt to boot your linux (b/c ubuntu doesn't include the elilo bootloader).
2) Your Mac's warranty (ensure your Mac is still on warranty).
3) If you have or can afford it, get yourself AppleCare.
4) Means for calling Apple's technical support/repair center.
 
P.D: the last 3 requirements are because of the suicidal and anti-OSS nature of the Intel CPU found in Intel based Macs.

---

### Post by hyapadi on 2006-05-24
Where can I find a review of imac intel running linux? Thanks

---

### Post by gingerbread_man on 2006-05-26
[QUOTE=Ptero-4]P.D: the last 3 requirements are because of the suicidal and anti-OSS nature of the Intel CPU found in Intel based Macs.[/QUOTE]

How in the world can that be possible? It's a stock intel core duo processor. It sounds a lot more like the EFI tools on linux are still not mature enough to be stable. thats fine, EFI is still quite new and with the lack of proper commercial support these amazing hackers manage to prove workarounds.

but don't spread misinformation accusing a processor of being anti-OSS :S!

---

### Post by Ptero-4 on 2006-05-26
ginger. What I said is that the TCPA thing (look for TCPA and Ptero-4 and you'll find a thread where I explain and put a link about what is TCPA according to richard stallman). Basically ginger, TCPA means "Trusted Computing Platform Alliance" and in plain english it is a protocol consisting of a central piece of hardware embedded in all the modern x86 processors made by Intel and AMD connected to special versions of the common hardware devices in the computer and connected through a special link to several "policy servers". This protocol allows M$, the RIAA, the MPAA, Disney, Intel, AMD, Dell, HP and some other companies to remotelly control your computer and define what you're allowed or forbidden to do, run, view, post, scan, print, etc on the computer you have. The TCPA was initially meant to be only used as an anti-piracy measurement, but because M$ arranged things in such a way that gives them preferential positions in the decision making/taking, it's not only possible but also obvious that M$ WILL use the TCPA to destroy opensource by putting rules in the "policy servers" that would forbid installation and use of opensource apps, and every TCPA complaint computer will obviously begin forbidding users from installing/running opensource apps. Now as for Macs. when Macs where in the PowerPC side they were safe from the TCPA, but when Apple changed to intel, they got caught in the middle of this TCPA shit. In the end, Apple isn't a participant of TCPA, but their decision of going to the x86 architecture got them in the middle of something quite nasty that PC users have endured for long but Mac users have never seen before.

---

### Post by gingerbread_man on 2006-05-27
[QUOTE=Ptero-4]it's not only possible but also obvious that M$ WILL use the TCPA to destroy opensource by putting rules in the "policy servers" that would forbid installation and use of opensource apps, and every TCPA complaint computer will obviously begin forbidding users from installing/running opensource apps.[/Quote]

Thanks for the info on TCPA, quite informative! I've read about initiatives like palladium but you've summed it up nicely. However, you could have made your point a lot clearer by mentioning the TCPA instead of the processor.

anyway, I agree with you. the potential for TCPA to do all those things you just listed exists. it's dangerous and very bad for consumers. However, I don't see the link between the possiblities you just described and the real world implementation of Trusted Computing on intel macs.

[QUOTE=Ptero-4]Now as for Macs. when Macs where in the PowerPC side they were safe from the TCPA, but when Apple changed to intel, they got caught in the middle of this TCPA shit. In the end, Apple isn't a participant of TCPA, but their decision of going to the x86 architecture got them in the middle of something quite nasty that PC users have endured for long but Mac users have never seen before.[/QUOTE]

You're conclusion is based on the possibility of TCPA evolving into the worst case scenario you described earlier. But this is a far cry from the implementation of the TPM chip on intel macs. The sole reason for that chip as apple has publicly stated is to ensure OS X only runs on Apple hardware. Considering that we're talking about an intel mac, it is hardly a restriction. Any other restriction is completely counter to Apple's direction in terms of openness. The lower levels of their OS is completely open source alongwith important technologies, Web: Webkit, Driver model: IOKit.

The intel mac TCPA implementation maybe cause for worry but i see no evidence to support your theory that the mac implementation is "anti-OSS". Especially considering that the significant percentage of mac apps, the underlying kernel and some higher level apple technologies are all open source.

---

### Post by Ptero-4 on 2006-05-27
> 
anyway, I agree with you. the potential for TCPA to do all those things you just listed exists. it's dangerous and very bad for consumers. However, I don't see the link between the possiblities you just described and the real world implementation of Trusted Computing on intel macs.

The conection ginger, is that M$ has precedence over the other companies in the alliance. This means that a decision by M$ can overrule anything by every other company in that group. It may seems far-fetched, but knowing the hatred M$ has against the opensource software (specially considering the "halloween documents" that leaked from M$), and the fact I mentioned earlier about the M$ position in the TCPA group, it's quite obvious when puting both facts together that M$ IS PLANNING to use the TCPA to break OSS. The conection to intel macs is simple. Intel Macs are as affected by this as are all other brands of x86 computers. As I said earlier, Apple didn't intend this to happen to their users, they just didn't saw it coming and got caught in one of the many nasty trick of M$.

> 
 But this is a far cry from the implementation of the TPM chip on intel macs. The sole reason for that chip as apple has publicly stated is to ensure OS X only runs on Apple hardware.

ginger. The restriction you're talking about isn't done by a TPM chip. It's done in the EFI/firmware which is totally different, and it isn't what I was referring to. The restrictions I was referring to are the ones imposed by the actual TCPA which are the ones you read about earlier. The TPM chip isn't put there or aproved by Apple. It was put there by Intel without Apple's knowledge.

> 
 The lower levels of their OS is completely open source alongwith important technologies, Web: Webkit, Driver model: IOKit.

The intel mac TCPA implementation maybe cause for worry but i see no evidence to support your theory that the mac implementation is "anti-OSS". Especially considering that the significant percentage of mac apps, the underlying kernel and some higher level apple technologies are all open source.

Although I'm not 100% sure about this. My theory is that since Apple can give M$ a hellish battle, and M$ knows it. M$ made a exception for the OSX internal and core files/apps when designing their anti-OSS plan, they did that to keep the TCPA hidden from Apple and their users, and eventually reveal it when Apple no longer have TCPA-free options (hardware-wise).

---

### Post by amitofu on 2006-05-28
First off, I just want to say that Linux runs great on my new MacBook. Even Aiglx and compiz run beautifuly. Sleep and sound are the only things that don't work right now.

As for trusted computing, I think it is cause for great concern. My understanding of TPM modules, however, is that they are microcontollers embedded in the hardware that store secure information. But they have no way of executing code by themselves and rely on software to take advantage of them--which is why I run Linux on my MacBook instead of Mac OS X.

There is of course the danger of subversive updates taking control of my machine, but that is the risk of using technology. I say this not to disregard the threat posed by trusted computing, but I do think it marginalizes it. It would be very difficult for Apple to get away with such subversive actions--unless they're actions are secretive a la AT&T and the NSA. And such actions would soon be detected and the public outrage that would (I hope) ensue should scare Apple away from ever trying such things. Free Software is too big to silently kill in the night.

For now I sit comfortably with my purchase. But I will of course stay vigilant, as we all must do, TPM or no.

---

### Post by cromestant on 2006-05-29
Wow you are my hero...
I am deciding to buy a new laptop, and since there was the efi thing going on I just cast away my much desired Macbook... But since you did it I might take the plunge ( since the dualcore dell that I was eying just went up about 350$)...

May I ask you which distro you installed on your macbook? I read that gentoo can be installed no prob since you choose the boot loader, but I just recently moved away from gentoo because I got fed up with all the maintenance it required, i'd love to install ubuntu...

Now , as far as the booting, is it posible to get linux/macos/ win booting at the same time ( I love linux, like macosx, and need windows for work, they use an app that only works on IE 6 so I HAVE to have it..)

Thank you

---

### Post by amitofu on 2006-05-29
cromestant: I ran Gentto for two years, and while it is a great distribution, I too got sick of maintaining it all of the time.

I have an intel Mac Mini and a MacBook. I run Dapper on both of them.

I posted in [another thread]("http://ubuntuforums.org/showpost.php?p=1060679&postcount=22") how I installed Ubuntu from the stock LiveCD which should get you started. There are still things missing from that post like how to get native resolution and sound working. I will maybe start a new howto thread soon.

You most definitely can [triple boot]("http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp") Linux, Max OS X and Windows. These are great machines. You won't regret the purchase :D.

---

### Post by cromestant on 2006-05-29
Thank you for the reply, I read on the tripple boot link you sent, that the winxp partition can only be 32gb , is that true for Dapper also?

What about the sound, did you get that working?
minidvi output? sorry for the nagging, but it's just you got me excited again with this

---

### Post by amitofu on 2006-05-30
If you format your Windows partition as fat32 then I guess there is a 32gb limit. It sounds like you *can* use ntfs, but you might run into trouble (and if you want to share files between linux and windows, fat32 is the way to go). Keep in mind that this is limited to the case of THREE operating systems on ONE hard drive. With a default drive size of 80gb, 32gb is well over a third. I would guess that large ntfs partitions would work just fine--they're just not supported by Apple and haven't been tried by the author of the triple boot article. And again, there is no question it would work on a separate hard drive. It is only when combining EFI and legacy partition tables that this might be a problem.

As for sound: the internal speaker on my MacBook works. But I had to patch the kernel to make it function. It is the only thing on the MacBook that required kernel futzing. It is easy to do and no doubt will be supported by default in newer kernels.

---

### Post by cromestant on 2006-05-30
I really apreciate the input, it's not easy deciding how to cough up 1500 -> 1800 $ specially if you come from a government controled foreign exchange rate .. I'd be using almost half of my allowed $ for this year, and , my salary beeing of about 200$ per month, i really have to think about it...

Have you tried Parallels?
[http://www.parallels.com/](http://www.parallels.com/)
It's another option, but I can't ssem to figure out how this works exactly ( bootloader on virtualization? how do they handle kernel upgrades? I tried asking them, but all I got is, well it works, no 3d, please buy... so... not very helpfull...

Well again thank you, i'll keep you updated on what I buy and my expiriences with it.

---

### Post by amitofu on 2006-05-31
Hey cromestant,
I appreciate how important it is to make well thought out and informed decisions. I have used Parallels. It is nice if you occasionally need to use an app from another OS (such as that ONE Windows app you need for work or whatever). I did not find it comfortable to work in for long periods of time, however. It is virtualization software and uses a software BIOS to boot the guest operating system into a virtual machine. Because it isn't a CPU emulator it does execute code at nearly native speed. But all hardware interaction by the guest OS is done through virtual software devices and is slow. In particular, all parallels exposes to the guest OS is a virtual VGA graphics chip and so graphics are very slow.

And while the new MacBooks are really nice. I think they are definitely not worth the cost in all situations. My sister has an iBook that runs Mac OS X and Linux just fine. Unless it is really worth it to you to run Mac OS X and Windows and Linux on the same machine instead of using multiple, much cheaper computers to do the same, the McBook is just a pretty box that will be available for half the price used in a couple of years. The MacBook doesn't allow you to do anything new, it just allows you to do it in a smaller package. I just thought I'd throw that out there to balance all of the hype.

Good luck. I'd like to hear what you decide and let me know if you have any other questions.

---

### Post by cromestant on 2006-05-31
Well it's true what you say, but my point of view when buying a computer is that you should buy a top of the line ( or near) since the evolution of the hardware is so rapid that you'll be outdated very soon if you bought a lower end machine. For instance I bought this dell 34 months ago, for 1600$, I have it almost sold for 1000$ which is not bad considering the prices some 2 year old laptops are selling these days.

Buying an ibook is out of the question since apple did hint that the support for the powerpc machines will not last very long.

The small package is what I'm looking at, with this one i'm hauling about 8.3 pounds, and it's not really nice.

Since I am a computer science student, I really need to have a good computer to develop on, and for work, I usually have so many apps open that on any of the other computers that i've worked on,  they just lag the hell out of my work.

i also like playing some Counter strike ( usually on weekends unless i'm on vacation..) so I kind of can't go with windows virtualization.
Linux on the other hand I can't live without... 

I suppose that ubuntu WILL release a good installer for these intel /macs soon, since they are selling quite well.

Looked at other laptops :
There is a dell I could buy for about 1600, fujitsu toshiba sony and hp just rob the **&( out of people with core duos, acers site is so nasty that I never got a price, alienware is out of the question, lenovo the good thinkpads are very expensive, the 3000 series looks kind of cheap manufactured.
Also the new turion 64 x2 chips aren't yet for sale so, if I want a dual core, i have to go with core duo.
So I guess it's apple or dell..
since dell is heavier and ( yes let's say it) uglier, i think I 'll go with apple.. It all depends on when I sell this one, and what my father in law likes and dislikes about the macbook in the next few days ( it's not here in venezuela yet, and he is going to the states..) , since I am kind of worried about the glossy screen.

Do you think you can install ubuntu on a macbook but on an externat firewire or usb drive? maybe bootcamp can handle that booting?

Well thanks again. will post back.

---

