---
title: "GUI doesnt load after installing nvidia drivers"
date: 2008-12-02
forum: x86 64-bit Users
---

### Post by Anonymous111 on 2008-12-02
I just installed ubuntu and it said i needed to update the drivers for my nvidia card. I installed them, then when i restarted my computer the GUI wouldnt load and it came up with a command line interface or whatever u call it. Is there any way to fix this?

---

### Post by dabl on 2008-12-03
See post #3 here:

[http://ubuntuforums.org/showthread.php?t=992381](http://ubuntuforums.org/showthread.php?t=992381)

---

### Post by NickD-NLUG on 2008-12-06
> **Anonymous111 said:**
> I just installed ubuntu and it said i needed to update the drivers for my nvidia card. I installed them, then when i restarted my computer the GUI wouldnt load and it came up with a command line interface or whatever u call it. Is there any way to fix this?

I had the same problem, but didn't even get to the command line - had to SSH into my desktop :)

Possible solutions for you are to use the "nv" driver rather than an "nvidia" driver in xorg.conf.  That should give you a working desktop, I don't know what the effect is if you're using Compiz or doing anything more than running a few simple graphical programs like a browser.

My solution was to disable Compiz completely and to disable GLX in xorg.conf with the line

Disable "glx"

in the "Module" section.

Then I've got a system which is alright, but doesn't have as high a resolution as it did on one screen, but at least I don't have to SSH into my desktop any more ;)

---

### Post by Anonymous111 on 2008-12-06
First, how do u "ssh" into your desktop?  (im new to ubuntu)

And second, i figured out that it actually is starting my desktop...i just cant see it...lol.

Im pretty sure its a problem with running SLI, (it will boot up into ubuntu fine when i take out one of my cards), but i play a lot of games on vista, so i dont feel like setting up SLI again every time i switch OS.

so is there any way to get this to work, while still letting me have SLI enabled?

---

### Post by Anonymous111 on 2008-12-07
help....?

---

### Post by vgrisham on 2008-12-07
> **Anonymous111 said:**
> help....?

First, let's try and rescue your x-server. After that we'll address the driver problem (what nvidia card do you have by the way?).

Boot your computer and when you get to the command prompt code:

> sudo dpkg-reconfigure -phigh xserver-xorgFollow the prompts and answer the questions. Then reboot or code:
> sudo /etc/init.d/gdm restartAfter you get that going, post back and I'll try to help you pinpoint which driver you should use.

EDIT: Post number two in this thread will kill two birds with one stone and fix you right up. After looking at dabl's post, his solution is better than mine and I would try it first. Of course, you're already at the command prompt, so you won't need to Ctrl-Alt-F1.

---

### Post by Anonymous111 on 2008-12-09
I've sort of given up on this problem and just took out my secondary graphics card...so unless there's a way to get SLI working on ubuntu I dont need any more help.

---

### Post by dagrump on 2008-12-10
It's been a bit, & I've slept since, but I believe this is what I did.
With both cards in & log in @ the command line "sudo nvidia-xconfig", this should give you a basic xconfig, then you use "lspci to determine the busId of your primary video card.
Now you edit your xorg.conf file, I used "sudo nano /ect/X11/xorg.conf", then in the device section you add the bus id of your main card.
It should look something like this:
*** Oh, that should be /etc/X11/xorg.conf not ect, some times I just go brain dead.

---

### Post by Anonymous111 on 2008-12-11
Well, if i still had 8.10, I'd try that, but I installed 8.04 and now everything works fine...except for that I installed the 32 bit version instead of 64 bit and I cant run half of my apps...fixing that now lol

---

### Post by vgrisham on 2008-12-11
Bummer. It's a drag that Intrepid had a bit of a stumbling start (nvidia compatibility being my biggest trip up) because the release really is a big step forward. The network manager has gone from awkward to slick. I love the tabbed browsing within the file manager too. After an glitchy first week or so, Intrepid has really shone on my system.

Good luck with yours Anon 111.

---

### Post by Anonymous111 on 2008-12-13
Well, someone told me that if SLI works on 8.04 and then upgrade it to 8.10, SLI will still work...it didnt.   So now i just clean installed 8.10 again (for some reason when i use 8.04, i cant install applications that have i386 architecture) 

 Is there any way to get programs that have i386 architecture working on 8.04?  

(ive always thought i386 was hardware, like processor or something...why would it change when i use a different distro?)

---

### Post by vgrisham on 2008-12-15
Which program are you trying to get working? If you're running 64-bit Ubuntu, you shouldn't have to do anything special The only program that I wrestled with was the Amazon Music Downloader and [getlibs]("http://ubuntuforums.org/showthread.php?t=474790") took care of installing the 32-bit dependencies it needed (and I don't think one needs getlibs to install Amazon Music Downloader anymore). I haven't needed getlibs with anything else.

---

### Post by Anonymous111 on 2008-12-15
I was trying to get opera to work, for some reason it works for me on 64 bit 8.10 but not 64bit 8.04

---

### Post by punkybouy on 2008-12-15
I have had that happen to me.  I installed the drivers via EnvyNG which work pretty well.  Occasionally, an update will hose the video and then I have to wait a bit for it to come in 800x600 resolution and login and reinstall via Envy again.

---

### Post by travist120 on 2009-01-21
THANK YOU FOR THE X.ORG .TXT FILE!!

It literally fixed EVERYTHING for me. THANK you so much!

---

### Post by dagrump on 2009-01-21
Glad it helped. The first couple times I tried on my machines I botched something, it was a relief when it final booted into X.
But I've borked stuff since & repeated the fix with good results.

---

### Post by NickD-NLUG on 2009-01-23
> **dagrump said:**
> Glad it helped. The first couple times I tried on my machines I botched something, it was a relief when it final booted into X.
But I've borked stuff since & repeated the fix with good results.

Can I just confirm this is the xorg.conf file you have for a system using a dual headed setup, but using a single card for it?

---

### Post by dagrump on 2009-01-23
Nope, 2 cards in SLI, & 1 monitor.

---

### Post by xr440dude on 2009-04-25
> **dagrump said:**
> It's been a bit, & I've slept since, but I believe this is what I did.
With both cards in & log in @ the command line "sudo nvidia-xconfig", this should give you a basic xconfig, then you use "lspci to determine the busId of your primary video card.
Now you edit your xorg.conf file, I used "sudo nano /ect/X11/xorg.conf", then in the device section you add the bus id of your main card.
It should look something like this:
*** Oh, that should be /etc/X11/xorg.conf not ect, some times I just go brain dead.

Dagrump, You're my hero.  I followed exactly what you said and it worked first time!  Thanks so much.  You're a pro!

---

### Post by johnny_pensionner on 2009-06-26
I had the same problem with dual GeForce 9500GTs (in SLI) in Ubuntu 9.04. By using the posted xorg.conf and some manual editing (to comply with my rig) it worked like a charm. However, I did switch from nVidia 180 to 173 at the same time. Conclusion: The combination works.

I will try and upgrade to a more recent nVidia driver release to see what happens.
[COLOR=DarkOrange]
[/COLOR][COLOR=DarkRed]Update:[/COLOR]
[COLOR=Black]Now I've tried both the 180 and the 185 drivers without any look (same xorg.conf). It seems the bug is related to the driver for sure. Of course, this is a bit annoying, but the important thing is that it works.[/COLOR]

---

### Post by Neikos on 2009-07-04
> **dagrump said:**
> It's been a bit, & I've slept since, but I believe this is what I did.
With both cards in & log in @ the command line "sudo nvidia-xconfig", this should give you a basic xconfig, then you use "lspci to determine the busId of your primary video card.
Now you edit your xorg.conf file, I used "sudo nano /ect/X11/xorg.conf", then in the device section you add the bus id of your main card.
It should look something like this:
*** Oh, that should be /etc/X11/xorg.conf not ect, some times I just go brain dead.


I LOVE YOU MATE 

I WAS like trying everything to make this thing to work fine and i didn't till i ffound your post you are the best thanks you very much mate.

---

### Post by mrbaze on 2009-07-11
> **dagrump said:**
> It's been a bit, & I've slept since, but I believe this is what I did.
With both cards in & log in @ the command line "sudo nvidia-xconfig", this should give you a basic xconfig, then you use "lspci to determine the busId of your primary video card.
Now you edit your xorg.conf file, I used "sudo nano /ect/X11/xorg.conf", then in the device section you add the bus id of your main card.
It should look something like this:
*** Oh, that should be /etc/X11/xorg.conf not ect, some times I just go brain dead.

Hi, I also love you dagrump for posting this, worked like a charm!

/baze

---

### Post by dagrump on 2009-07-11
Well now don't I feel all warm & fuzzy, oh wait I haven't shaved for a few days, that would be scraggly.
But, I didn't come up with this, some one told me & I passed it on.
Makes one a bit ticked, after buying that second card & you end up with no GUI at all.

---

