---
title: "nVidia 64 bit drivers"
date: 2008-01-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by Ck.asdf on 2008-01-29
As a preface, let me inform you all that I'm used to Fedora, so Ubuntu is slightly different with its package manager and such.  But I wanted to try Ubuntu Studio, so here I am.

I got drivers from nVidia, but when I tried to run the program (.run extension), it told me I needed to have some development packages and such installed, so I could compile the drivers.

I looked at the "Add/Remove" option in the Applications menu, but none of the categories included development, so ... suggestions?
I did try installing the nVidia drivers using that same Add/Remove app, but after trying to enable effects it still denied me with "Desktop effects could not be enabled" (I did do "sudo apt-get install compiz before that").


Suggestions? Thanks in advance!
-Chris

---

### Post by Kilz on 2008-01-29
> **Ck.asdf said:**
> As a preface, let me inform you all that I'm used to Fedora, so Ubuntu is slightly different with its package manager and such.  But I wanted to try Ubuntu Studio, so here I am.

I got drivers from nVidia, but when I tried to run the program (.run extension), it told me I needed to have some development packages and such installed, so I could compile the drivers.

I looked at the "Add/Remove" option in the Applications menu, but none of the categories included development, so ... suggestions?
I did try installing the nVidia drivers using that same Add/Remove app, but after trying to enable effects it still denied me with "Desktop effects could not be enabled" (I did do "sudo apt-get install compiz before that").


Suggestions? Thanks in advance!
-Chris

In Ubuntu there are a few ways of installing the packages. Add/Remove programs only handels the easy common applications in a friendly way. [Synaptic ]("http://www.monkeyblog.org/ubuntu/installing/#installing_with_synaptic")is for power users. Another thing you will need to know is that development packages usually have -dev added to them. 
But there is an easy way to install the nvidia drivers, you might want to look at [Envy.]("http://albertomilone.com/nvidia_scripts1.html")

---

### Post by Ck.asdf on 2008-01-29
um, I believe I have run into a problem ... before I posted the first question, when I booted Ubuntu Studio the first time, X wouldn't start.  I figured "okay, whatever, I'll delete xorg.conf & let Ubuntu create a new, generic one."

The problem is, ever since I did that, there isn't an xorg.conf in /etc/X11 anymore, though it must be SOMEWHERE, because I'm using X right now.

Anyway, I went and did all that Envy stuff, and after restarting, it said I was using the "restricted video driver" which I read to mean proprietary (not a problem for me), so I do have nVidia something or other installed ...
When I try to run "nVidia Settings" (Applications -> System Tools), it tells me:
> You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

I suppose I'll try that, and risk messing up even more ... hah.

Any more suggestions? Thanks so far. :)

How about copying the xorg.conf file from Fedora, on my other partition?


/EDIT/
Okay, I ran that command, and awesomely enough, it said:
> root@ck-buntu:/home/ck# nvidia-xconfig

WARNING: Unable to locate/open X configuration file.

New X configuration file written to '/etc/X11/xorg.conf'
So, it created a new one for me ... yay!  (Is it my birthday already? heh)

I restarted X to allow for it to use the xorg.conf in the correct directory, and was pleased to see the pretty full-screen nVidia logo previous to the login screen.  I now have compiz working, too, :D

I'm not sure I have compiz fusion, though when I did "apt-get install compiz," I saw something about compiz-fusion during the download...

I do know that I have wobbly windows, nifty windows-tab (better than Aero's version), and such.

One thing I don't like, though, either in Compiz or Aero - the now-huge alt-tab view.  It shows a huge thumbnail of each window, which is counter-productive to me, as I only want the program icons and text of each window just like without compiz/Aero.
In Vista, I did a registry hack to get rid of the "updated" alt-tab ... how can I get rid of it in Compiz?

---

### Post by Ck.asdf on 2008-01-29
Hello, I've gotten the video drivers completely working, I do believe ... and I have dual monitor KINDA working.

I say "kinda" because I cannot drag windows from one window to the other, though I can use both monitors independently like two separate computers (though I'd rather have one).

I've tried "xinerama" but apparently with that on, I don't get any fancy graphics.  Not on either desktop ...

So I guess I'll stick to the first desktop with fancy effects and the second without, though it'd still be helpful if I could drag across ...

any suggestions towards the best of both worlds?

thanks again!

/EDIT/
okay, so non-xinerama dual monitor mode (two desktops) leaves me with:
screen 1 = fancy compiz graphics
screen 2 = NO TITLEBARS

This has happened in the past on single monitor systems with weird compiz errors ...
it DID say that the secondary monitor wouldn't have 3D support, but I didn't think it would take away my title bars!

What to do in such a situation??

---

### Post by Victormd on 2008-01-29
> **Ck.asdf said:**
> um, I believe I have run into a problem ... before I posted the first question, when I booted Ubuntu Studio the first time, X wouldn't start.  I figured "okay, whatever, I'll delete xorg.conf & let Ubuntu create a new, generic one."

Some Nvidia cards require you to edit the xorg.conf file after installing the restricted drivers otherwise X won't start.

In your xorg.conf (if you get it back :) ) under Section Device, add the line:  Option	"NvAGP"	"1"

The "1" is an instruction address for the AGP. In my case, I had to use "2" and from what I've read, 1 is the most common and sometimes 2... not sure of any other alternatives.

Hope this helps

---

### Post by Ck.asdf on 2008-02-03
Does mail notification not work here?  It's enabled in my settings ...

You mention "AGP" in your reply ... do you mean the AGP slot? Because I'm using PCI Express, not AGP.

But yeah, I got xorg back and working, then when I tried dual screen, got some strange happenings, as mentioned previously.  Perhaps I should ask about that in another thread, maybe another forum? It's pretty much off-topic by now.

---

### Post by enbuyukfener on 2008-05-02
> **Ck.asdf said:**
> Hello, I've gotten the video drivers completely working, I do believe ... and I have dual monitor KINDA working.

I say "kinda" because I cannot drag windows from one window to the other, though I can use both monitors independently like two separate computers (though I'd rather have one).

I've tried "xinerama" but apparently with that on, I don't get any fancy graphics.  Not on either desktop ...

So I guess I'll stick to the first desktop with fancy effects and the second without, though it'd still be helpful if I could drag across ...

any suggestions towards the best of both worlds?

thanks again!

/EDIT/
okay, so non-xinerama dual monitor mode (two desktops) leaves me with:
screen 1 = fancy compiz graphics
screen 2 = NO TITLEBARS

This has happened in the past on single monitor systems with weird compiz errors ...
it DID say that the secondary monitor wouldn't have 3D support, but I didn't think it would take away my title bars!

What to do in such a situation??
I doubt you are still looking for an answer but for anyone else who comes here through Google or something:

What you want is TwinView so your screens act as one instead of being separate X screens. The nvidia-settings application can manage this.

Also, nice to see you got it all working, gutsy/nvidia/dual screen was a pain for me too. Hardy has been an improvement in this area.

---

