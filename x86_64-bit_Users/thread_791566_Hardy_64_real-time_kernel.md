---
title: "Hardy 64 real-time kernel?"
date: 2008-05-12
forum: x86 64-bit Users
---

### Post by knife_party on 2008-05-12
hi, i've been wondering..does the 64-bit hardy has a real time kernel? if not, should i use the binaries like those described in the wiki.ubuntu.com/realtime/hardy page? because i can't find the rt patch for the 2.6.24-16 kernel in the kernel.org page. Thanks before..

---

### Post by StefAndrew on 2008-05-12
Well, I know that UbuntuStudio, both 32 and 64 bit, *uses* a RT kernel, but 64 bit doesn't use RT by default.  I had forgotten how much I missed UbuntuStudio.  I'm loving it so far.

---

### Post by CheShA on 2008-05-12
its as easy as 
```

apt-get install linux-image-rt

```

you might also want to 
```

apt-get install linux-restricted-modules-rt

```

---

### Post by Julius on 2008-05-12
> **knife_party said:**
> hi, i've been wondering..does the 64-bit hardy has a real time kernel? if not, should i use the binaries like those described in the wiki.ubuntu.com/realtime/hardy page? because i can't find the rt patch for the 2.6.24-16 kernel in the kernel.org page. Thanks before..

What's real time kernel? I mean I've read a few things about it but if you had to describe it in one sentence? :p

---

### Post by millie95 on 2008-05-12
[http://rt.wiki.kernel.org/index.php/Main_Page](http://rt.wiki.kernel.org/index.php/Main_Page)

---

### Post by eluminx on 2008-05-12
i read it and call me stupid but, what would be the purpose of using a real time kernel?  I have no clue as to what it is btw, even after reading the wiki page.  I've been using linux for quite some time, but i by no means consider myself and advance linux user.  A more laymens terms would be nice, if someone doesn't mind.

---

### Post by millie95 on 2008-05-12
Normally, user processes are preemptible, which is why you can run multiple programs simultaneously: Linux quickly switches between them.

A preemptible kerenl means that the kernel can also preempt sections of itself (in addition to regular processes). This allows responsiveness with delays (latency) under <1ms.

One thing this good for is recording music. If you have a synthesizer and you are playing it with a MIDI piano, you want to hear the sound as soon as you hit the key on the piano. It becomes more and more difficult to play piano as the latency rises. Generally, above 20 milliseconds is unplayable.

Another application of real time is industrial control things, where e.g. a valve needs to be opened or closed at a precise time.

I think just about everyone should run the RT kernel.

---

### Post by CheShA on 2008-05-13
> **millie95 said:**
> I think just about everyone should run the RT kernel.

Yeah I couldnt understand the point of *not* running an RT kernel either but it turns out you get a perfomance hit on other more "normal user" things, like watching video, which apparently takes up to a 20% performance hit.

Also I have found this time round that he RT kernel is buggy as hell, I've had to revert to the standard kernel the last week or two until i can get round rolling my own to resolve the issues I've been having. 

EDIT: I appreciate that if everyone ran the RT kernel, then it would be better tested and more stable, etc.  Just chucking in my 2p: the RT patches seem to be affecting something very badly for me on default kernel.

---

### Post by knife_party on 2008-05-13
@chesha: wow, is it that buggy? i've just installed the rt-kernel this afternoon, haven't really give the system a whole test. Could you give me information about which applications that have problems? And, by not using a rt-kernel, is there any problem recording music and so on?

BTW, i've heard that the latest kernel, 2.6.25 is already a rt by default? is it true? since there are no patch for that kernel version

---

### Post by CheShA on 2008-05-13
> **knife_party said:**
> @chesha: wow, is it that buggy? i've just installed the rt-kernel this afternoon, haven't really give the system a whole test. Could you give me information about which applications that have problems? And, by not using a rt-kernel, is there any problem recording music and so on?

I've not even managed to get that far, I  found with the RT kernel that the whole system just KOs after a few minutes. Something happens with the file system and it all collapses, even commands like *ls* stop working and weird error messages, keyboard goes weird etc. This could be down to the way it interacts with dmraid or something but it definitely kills my PC in minutes after a boot, even if I'm just booted into single user or whatever. Reverting to generic kernel fixes it immediately. I haven't yet found anyone else with the same issue but then again, I haven't really had a proper look yet - put it this way, I'm happy enough to post the instructions how to get it (above) without thinking it needs a warning , probably just a quirk on my system that needs ironing out, but for me it's 100% unusable at the minute.

I haven't had time to try and trace it yet, Its taken me about 10 days to get a successful clean install for one reason or another (including kernel issues)  and I was finally up and running the day before yesterday.

Recording is possible with generic kernel but if you're mixing (or playing midi) on the fly then don't bother, your knob-tweaks and midi notes  will be, like, 100ms out :(

---

### Post by CheShA on 2008-05-13
> **knife_party said:**
> BTW, i've heard that the latest kernel, 2.6.25 is already a rt by default? is it true? since there are no patch for that kernel version


Cant really comment on this, but a quick google turns up [this link]("http://www.linux-watch.com/news/NS7627355459.html") which says:

>  "real-time improvements are prominent, but Linux's big "real-time patch" still remains outside the mainline tree, as do several things that have to be merged first"

---

### Post by knife_party on 2008-05-16
Mm..i've already installed the rt-kernel using synaptic, and as u said before, it's as easy as choosing to install linux-rt packages. And so far i haven't met any problems, in fact im on a rt kernel at the time i type this reply :D

---

### Post by CheShA on 2008-05-17
Yeah I have actually just reinstalled the rt kernel packages today and everything seems fine. Weird... but at least its sorted :) Glad you are too.

---

### Post by knife_party on 2008-05-17
ah, gud for u then.. So maybe it's time for me to start making another ambient stuff :D

---

### Post by Kapitan on 2008-05-26
But i've red that the real time kernel
doesn't work with compiz, is it real?

In the 7.01 was true, but i'haven't try
with 8.04.

Before It hangs the x server.

---

### Post by Yellow Pasque on 2008-05-26
> **Kapitan said:**
> But i've red that the real time kernel
doesn't work with compiz,.
The real-time kernel should be used for low-latency applications like audio synthesis. It is not a good kernel for daily usage or desktop effects.

---

### Post by Kapitan on 2008-05-26
I know. but i use my pc for both.
I cannot switch the xorg conf any time.
(can i?)

So by now i have the generic, and audio
has ticks...and desktop has cube.

I only ask for a solution.

---

### Post by CheShA on 2008-05-27
I had no problem running  Compiz with realtime kernel on either 7.04, 7.10 or 8.04, but as Temuljin said, it's not really an ideal "every day" kernel.

---

### Post by Kapitan on 2008-05-27
but do you have an nvidia or an ati video card?

And have you installed the standard ubuntu packages
or built something from sources?

---

### Post by CheShA on 2008-05-31
> **Kapitan said:**
> but do you have an nvidia or an ati video card?

And have you installed the standard ubuntu packages
or built something from sources?

Realtime kernel (linux-image-rt) installed from Ubuntu repo every time and got GLX desktop working over twin monitors :guitar:
[LIST]
[*]On Feisty, I used Envy to install nvidia drivers and then ran Beryl + Emerald which was installed from Beryl's own .deb repo. I also had this same setup running on my HP laptop with Intel 915 graphics using 915resolution package from Ubuntu repo.
[*]On Gutsy I used Envy to install nvidia drivers and then ran Compiz Fusion  as installed by default plus compizconfig-settings-manager from Ubuntu repo.
[*]On my Eeepc (intel 915 graphics again) I installed Linux Mint Daryna then added linux-image-rt and it worked fine with Beryl as installed by default.
[*]On Hardy I installed nvidia-glx nvidia-settings and linux-restricted-modules-rt from Ubuntu repo and ran Compiz Fusion as installed by default plus compizconfig-settings-manager from Ubuntu repo - couldn't be easier!!:)
[/LIST]

---

### Post by Kapitan on 2008-05-31
How can i tell to the kernel to boot without
launching gdm?

Because my system fail to start it and hangs all
the computer (no CTRL-ALT-F1,F2,F3),this happens
with rt only, so i want to understand the
problem.

I'll search wiki :)

Thanks for your answers.

---

### Post by CheShA on 2008-06-02
> **Kapitan said:**
> How can i tell to the kernel to boot without
launching gdm?

What I would do is boot into the standard kernel and then rename the gdm init file so that it doesn't trigger (because this breaks the symlinks in /etc/rc?.d )

```
mv /etc/init.d/gdm /etc/init.d/gdm_nostart

```

You can then reboot into your RT kernel and it will drop straight to a shell login. you can start and stop gdm to test 
```

/etc/init.d/gdm_nostart start 
/etc/init.d/gdm_nostart stop

```

Then when you are finished you move the init file back
```
mv /etc/init.d/gdm_nostart  /etc/init.d/gdm

```

If you're completely unable to boot with any kernel, you could also use a Live CD to boot and then mount the local hard disk to rename the /etc/init.d/gdm file

---

### Post by Kapitan on 2008-06-06
Yes and another solution
i have found is removing
the symbolic link from
/etc/rc2.d and then readd
it.

Manually or with updaterc.d 
(or is a similar command).

The problem of the rt kernel
reamains on my machine with the
restricted modules packages.

All works with the compilation
of the nvidia driver (nvidia-numbers_run.sh)

Thanks

---

### Post by Anduu on 2008-06-06
I figured I would try out the real time kernel and the oddest thing happened...suspend/hibernate works for me now...go figure :p

Maybe I'll keep it around for a while.

---

