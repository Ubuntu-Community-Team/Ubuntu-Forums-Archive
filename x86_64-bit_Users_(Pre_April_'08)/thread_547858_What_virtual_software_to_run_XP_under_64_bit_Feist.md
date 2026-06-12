---
title: "What virtual software to run XP under 64 bit Feisty?"
date: 2007-09-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by the_nite_owl on 2007-09-10
I want to setup a virtual machine so that I can run the occasional instance of Win XP.
Any recommendations on software that will run under 64 bit install of Feisty?

---

### Post by John.Michael.Kane on 2007-09-10
virtualbox. seems to be liked by forum members.

64bit ("Feisty Fawn") deb can be found at the link below.
[VirtualBox]("http://virtualbox.org/wiki/Downloads")

---

### Post by stmiller on 2007-09-10
Yep Virtualbox is great. Doing a couple of benchmarks with LAME inside Virtualbox, the CPU encoding speeds are identical to the native OS. Pretty amazing stuff.

---

### Post by the_nite_owl on 2007-09-10
Thanks guys I will look into it.
I have never setup a virtual machine app before and am still somewhat new to Linux but getting by.
I figure if I can get that damnable cheapo wifi card working I can do just about anything.  Except for getting Flash working 64 bit but that's another story.  :)

---

### Post by brharri1 on 2007-09-10
I've been using vmware server with very few problems (just have run vmare-config.pl when i update my kernel). You guys think virtual-box runs better?

---

### Post by dabl on 2007-09-10
VMWare Player,which is a package in the repos, works great for me.  :guitar:

---

### Post by the_nite_owl on 2007-09-11
With VMWare Player dont you need an already created virtual file to use?  Or does it allow you to create one?

I installed VirtualBox and it seems to be doing well so far.  Have gotten XP installed though not fully configured yet but it loads and gets an internet connection.

---

### Post by dabl on 2007-09-11
> **the_nite_owl said:**
> With VMWare Player dont you need an already created virtual file to use?
 

Yes, but it wasn't hard. This guy has some that you can just download: [http://www.penguin.ch/dokuwiki/doku.php/virtual:vmware:model](http://www.penguin.ch/dokuwiki/doku.php/virtual:vmware:model)

I needed to tweak the Win XP Pro machine to change the CD ROM drive to /dev/scd0, and to enable the sound card.  It's not rocket science -- it's just a text file and you can see what to do.

Then of course you have to have a proper MS Windows installation CD to install Windows with.

:guitar:

---

### Post by tolstoyboy on 2007-09-11
there is a sticky post concerning Flash for Firefox on 64bit.   Kilz has written a useful install script which works well.

---

### Post by SteveHoffmanUK on 2007-09-11
brrhari1 wrote:
> I've been using vmware server with very few problems (just have run vmare-config.pl when i update my kernel). You guys think virtual-box runs better?

Yes, definitely. I had VMWare running a Windows XP Home guest on my Ubuntu Dapper (6.04) host machine. It was OK to a point, but I had recurring and random problems accessing USB devices: sometimes (mostly) I could, but sometimes I couldn't or else I'd have to unplug/replug them to work. It finally got borked when I installed a kernel upgrade, so I thought I'd try Virtualbox.

There were some initial "challenges" getting the USB devices to work, but eventually they all installed, and I have to say that Virtualbox works better for me than VMWare. Everything works and it's **fast**, faster than under VMWare. I can also use the clipboard across the two applications, which I couldn't in VMWare.

---

