---
title: "RAM troubles"
date: 2006-09-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by StandardBlueCaboose on 2006-09-13
So I bought my third GB of RAM from newegg.com and popped it in, everything boots up like normal, until grub tries to boot kubuntu. It starts booting and just kind of freezes when it says "booting OS" (or whatever it says, I don't recall exactly) Then it just hangs. Then I disabled quick boot and I see that my motherboard is recognizing 3040 GB and memtest is recognizing 3039 GB. Memtest ran successfully for 8 hours with absolutely no errors. So I'm just wondering, does anybody have any idea what's going on? I'm typing up this post using 32-bit knoppix. 

Asus K8V SE Deluxe | AMD Athlon 64 3700+ | 3 GB Corsair RAM | Nvidia GeForce 6200 | 500w Ultra X-Connect PSU | 2x 300 GB SATA Seagate | 1x IDE drive of some sort

Thanks in advance for any help.

---

### Post by kuja on 2006-09-13
You say it freezes in the boot process? Seems to be an awfully popular problem lately. Try booting into recovery mode and see if that gives you any trouble. If it doesn't, Try removing the splash option from the kernel line for your ubuntu kernel in the /boot/grub/menu.lst file. That might work.

---

### Post by StandardBlueCaboose on 2006-09-14
I tried booting into recovery mode (I have no idea why I didn't think of that before) and it still didn't work. I did get some more useful messages... Kind of. Anyway, when in recovery mode it hangs when it says "loading essential drivers" or something to the likes of that. 

So, what's the next step?

---

### Post by tappad on 2006-09-14
try editing your kernel boot options.

Add "acpi=off nosmp noapic nolapic" at the end.
Solves the problem for me (temporarly)

Without the noapic my comp freezes at boot.
Without nosmp my comp acts crazy with sudden reboots now and then however it disables use of dual-core :(

Iv'e gotten sick of theese problems..
I had problems recognizing 4 gig ram, a bios upgrade took care of it.
BUT, theese stupid problems occured. Everything worked perfect before..

Anyone with more info?

---

### Post by a-musing amazon on 2006-09-14
Is this a dual channel or single channel M/B? Adding a third RAM module would force it to go into single channel mode.

There are always liable to be some issues when you have lots of RAM modules, especially if they are not identical and maybe not matched.

One thing you might try is relaxing your RAM timings in bios - what works fine with 1 or even 2 sticks may not work with 3, especially when you have that amount of RAM, and especially if the timings are set to auto, and the default timings on the RAM sticks differ.

---

### Post by StandardBlueCaboose on 2006-09-14
I am upgrading from 2.5 gigs to 3.0 gigs, initially I had 2x 1GB Corsair Value Select sticks and one crappy 512 stick from dell. I'm upgrading to a third Value Select stick. They are not completely identical, but all the timings are the same. Two of the sticks have corsair modules, and the third has nanya modules. If any of that helps solve the problem.

Anyway, I'm going to go do my best to figure out how to edit my kernel boot options. I'll post again whether or not it works.

(Btw, my mobo already dramatically reduces the speed from DDR 400 to DDR 200 when there are three double side sticks in, I hope I don't have to make it even slower :-/ )

---

### Post by StandardBlueCaboose on 2006-09-14
Ok, I did my best to edit my boot options, from what I gathered I just edit the boot commands from grub. I added it like this

savedefault
acpi=off nosmp noapic nolapic
boot

which resulted in grub saying "error 27 invalid boot option" (or something) and then I tried putting tappad's command after the boot line, and the exact same thing happened as before, where it just hangs.

Is that what I was supposed to do, and where I was supposed to put it?

---

### Post by a-musing amazon on 2006-09-16
Going back to your RAM issues.

As you have pointed out if you have 3 sticks in a dual channel M/b the M/b will switch from dual channel to single channel i.e. DDR400 to DDR200. So your RAM is then daisy-chained - it uses one and when that is used up tries the next and so on. 

In theory you would be better to have added 2 matched sticks (i.e. 2 x 500kB), assuming that you do have 4 slots, as you would still then be able to work in dual channel mode.

If you haven't set the RAM timings in bios then the motherboard may try and pick these up automatically from the 1st RAM chip it finds. So as as long as this is the slowest you should be OK - though with memory on 3 different sticks there may well be additional latency issues and you may not be able to achieve the latency one stick can achieve on its own.

So things may have worked OK when you has the slowest stick (the dell?) first but not when you put your brand new one there - when the boot sequence tries to load the OS may well be when it tries to access the second (slower) stick to fast and gets stuck (though it should all load quite happily within 1 Mb).

I suggest you check what the latencies of your 3 sticks are and then go into bios and manually set them slower than the specs for all three. If it still doesn't work then it isn't what I'm suggesting. If it does then work you can then try tightening the latencies.

---

### Post by StandardBlueCaboose on 2006-09-20
My motherboard only has three slots. It's kind of strange, but whatever. I'm kind of glad it only has three, otherwise I would have to buy another stick.

Anyway, I am using three Corsair ValueSelect sticks of RAM, and I gave my Dell stick to a friend because I don't need it anymore. (Two sticks of RAM is enough to last until I get the third working, I suppose.)

I have tried my RAM in every possible combination, so I doubt it's the latencies that's causing the problem. Also, because I was able to boot Knoppix, I don't think that it's actually a problem with the RAM or the motherboard. I think this is a problem with Kubuntu. I remember reading somewhere a few days ago (for a completely unrelated problem) that a person had to edit some file somewhere and input their amount of RAM manually. If this sounds familiar to anybody, let me know.

I would test to see if Windows boots with my RAM but I'm having some troubles with it right now. If anybody could help me get GRUB to chain-boot with XP, it would also be appreciated.

---

### Post by StandardBlueCaboose on 2006-10-05
Window boots with three gigs of RAM installed, so it's not a problem with my computer or my latencies, it's with Linux/GRUB.

Just to be more specific, I'm going to run through what happens again, with more accuracy.

I select my kernel from the GRUB list, and press enter. It runs fine until it says

```
Decrompressing Linux...Done.
Booting the kernel...
_

```

The underscore then blinks indefinitely. It doesn't stop blinking, and it doesn't do anything better.

Any ideas? Anything else I need to add?

---

### Post by StandardBlueCaboose on 2006-10-09
I hate to nag, but...

I'm running windows here... It's tough.

Does anybody have any idea whatsoever? I mean... Anything at all.

---

### Post by kuja on 2006-10-09
I've got a pair of ideas, since most of this conversation seems to be focusing on RAM anyhow.

Try running Memtest86... it should still boot fine anyway, I would think.
Another thing to try would be to try running Prime95's torture test. If either of them throw errors at you, or locks up your system, it's a hardware problem. Period. Otherwise, it's a software problem, which makes things significantly less costly, but significantly more time consuming and difficult to work out.

---

### Post by /carlito on 2006-10-09
You should ditch the third RAM modules as it will always reduce your performance. Use the 2 sticks you have installed now so you can use the full 128bit memory bus.

If you're really peristent on using the third module, you could always check your kernel config or try another kernel wich has 4G memeory support built in.

---

### Post by StandardBlueCaboose on 2006-10-09
I am persistent on using the third gig. *shrug* I'll probably switch it in and out, who knows. I'll probably end up buying another motherboard in the end. 

Anyway...  Uh... Kernel config? I have no idea where to access that, or anything of the sort. If my kernel doesn't support the 3 gigs, that would definitely be the problem. I just downloaded the uh.. normal one. Where can I find a better kernel, and where can I find out how much RAM my kernel supports?

---

### Post by /carlito on 2006-10-10
You should check out [this](http://ubuntuforums.org/showthread.php?t=217657) thread.

---

### Post by StandardBlueCaboose on 2006-10-10
(Btw Kuja, I have already run memtest successfully for 31 hours (23 + 8 ) so I don't think that's the problem. I'll try the torture test if need be.)

Ok, so I check out the kernel recompiling and I noticed something. You need large memory support if you have more than one gig? If that's the case then I already have it, because Kubuntu boots fine with 2.5 gigs. Should I still try it? I know that recompiling my kernel will present me with a lot of problems that will frustrate me, so I just want to be fairly sure that I'm not doing it for no reason.

---

### Post by kuja on 2006-10-10
I would recommend still running the torture test. It seems to be much more intensive in my experience. I'd recommend running at least overnight if nothing else, though most severe problems would pop up within the first hour or so.

---

