---
title: "Some questions about 64 bit migration."
date: 2008-03-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by pearjam on 2008-03-06
Many questions about 64bit.

I know there's a 'read-first' sticky about this, but I'm having a hard time finding answers to some of these questions.

---First, the downloads for the 64 bit say 'AMD' in the file name but mention 'Intel' in the text. Will the AMD64 work for an Intel Core 2 Duo because it's EM64T?

---I use Xampp for PHP development, but there isn't a 64 bit version. I've read that you can install the 32 bit libs and it works fine. Is this true? Is there another package similar to Xampp for 64 bit other than installing server components separately?

---I play Enemy Territory & I know it's an older release for Linux. Is it still playable on 64 bit, & if so - how? (I could lose the game if not possible, I'm just curious about this one.)

---I've read in the forums about Automatix. How does that apply to a 64 bit migration? From their site, it sounds like it installs 'common' software on its' own (and makes backups) but doesn't clean up after itself.

---Some of the forums mention 64 bit repositories, but I can't find them. Do they only show if you have a 64 bit OS?

---I also use K3b, K9Copy, DeVeDe, EasyTag & lightscribe (4L-gui) etc... are they in the 64 repositories or available to download for the 64 bit platform?

---Is there a 64 driver for NVidia 7600GT?

---If you have Ubuntu 64 and you install something like a restricted NVidia driver, will it automatically be for the 64 bit platform? Anything to watch out for regarding installs from the repositories that are only for 32 bit systems, or will a 64 bit system's repositories only show 64 bit apps?

My understanding (from reading the forums and googling the software I use) is that if there is a 64 bit repository then most of the apps I use will be there - if a few aren't, then I would install the 32 bit libs to allow them to be installed and ran. Apps I pull from the internet that aren't 64, will also run on the 32 bit libs. Wouldn't that end me up having a 64 bit OS w/ 64 & 32 bit libs, and a gnome desktop w/ gnome & kde libs (from using K3b & K9Copy)?

Lastly but not leastly, a hardware question. I've heard / read that if you have a 2nd hard drive, you can store your stuff there and if you re-format the OS on the 1st drive, the data on the 2nd drive will still be readable as long as it's the same file system. Is this method comparable to partitioning the same drive? What are the pros & cons of both? (currently if I format, I store backup files on cdrws and in my email, but its' slow and a pain - having a second drive for storage would be fast and easy if it works the way I think I read it does. :) )

Thanks for any help!

---

### Post by Kilz on 2008-03-06
I stongly suggest reading that Sticky,
Yes it will run on EMT64 intel chips.
[Take a look at this page]("http://mjg59.livejournal.com/77440.html") before using Automatix .
[Look here to search the repositories]("http://packages.ubuntu.com/"), but if its in the 32bit repos. It should be in the 64bit.
The 64bit version can run 32bit applications. Yes it may need a few libraries. But the 64bit version has a lib32 directory for them.

---

### Post by pearjam on 2008-03-06
I read the sticky, but couldn't find anything pertaining to Xampp (I could of missed it though). I found info on the net about the 32 libs allowing Xampp to run, but I guess I wanted a verification from here.

Another reason the sticky didn't relate to what I want to do is this:
(note: this may sound really stupid)

My plan was to burn a dvd iso of Ubuntu Studio 64 8.04 Alpha 5 (Hardy) because it comes with studio apps I use like Audacity, Hydrogen & qjack, but more importantly, it DOESN'T come with things I don't use like bluetooth, client side email, palm support etc... which can't be easily removed from regular Ubuntu.

After the install, I was going to remove the included studio apps I don't use (like rosegarden). This would leave me w/ a base OS install without anything I don't use. Then I would install the apps I do use like Xampp, K3b and so on.

The end result is an OS with only the things I've put / kept on there and nothing I don't use. I can't find any info regarding an install like this, so I figured it would be experimental for me - that's why I asked about data being accessible on a different drive as long as it's the same file system - this way I could back out of this 'learning experience'.

The sticky didn't seem to apply (no pun intended), and I couldn't think of where to post the questions I have or if the questions would make any sense.

Is there a striped down version of Ubuntu 64 that I can build on? Is any of this even a wise idea?

---

### Post by firecat53 on 2008-03-07
If I'm understanding you correctly, it sounds like you just want what most of us do: an easy install/removal process for any applications so you customize to your heart's content.

The easiest way to get the important things working right to start with is downloading the standard desktop version and then using synaptic or add/remove programs to add/remove what you like. I don't know much about Ubuntu Studio, so I'm not sure about those applications, but you certainly describe the same process that we all use and is made easy by tools like synaptic and add/remove programs.

When you install Ubuntu, you have the option of setting separate partitions for /home and / (root). This allows you to save your data on /home and then reinstall as necessary your root system without losing or having to recopy your data. /home can be on a separate partition, a separate hard drive, or even a network drive (I think :) ). Do some reading about how to accomplish all that during install. It's pretty easy, but you do need some basic terminology before you start.

Good luck!
Scott

---

### Post by Kilz on 2008-03-07
> **pearjam said:**
> 
My plan was to burn a dvd iso of Ubuntu Studio 64 8.04 Alpha 5 (Hardy) 

I dont recommend installing an Alpha operating system to anyone. They are for testing, and things break when updates happen.

As for the striped down version of Ubuntu, yes there is such a thing, its the server install disk. It doesnt even have a gui.

---

### Post by pearjam on 2008-03-08
Kilz, Firecat

It's done now... I did install Ubuntu Studio 64 Hardy (Alpha 6), & it's gone past what I originally hoped it would do! Not only did I have a choice not to install audio, graphic and video suites, but I could install just the Ubuntu Studio Desktop - which is what I did.

For instance, the plain Desktop install had only Open Office Word (which I use), but no spreadsheet or any of the others which I don't use. In short, it had everything I needed, and none of the stuff I don't. Turns out, Lightscribe was the hardest thing to install, and it wasn't so bad.

Kilz, your right about bugs in pre-releases... I can't get 'numlock' to stay on automatically after reboot. It's already listed as a known bug - so I won't panic. I do know about the Ubuntu server install disk, & I've had my hands in a few unix servers before - but this isn't a production box, it's my home machine - you know, for fun. I use Xampp to learn more about PHP development & to see my results in a simple environment, but that's it. I'll keep work stuff - at work. (PS to Kilz: you seem bummed... I checked out your website, you're a Christian, me too! Smile man!)

Firecat53, when I've used add/remove or synaptic to remove something like 'palmOS', it says it will remove the desktop too - same with the floppy formater (I don't have a floppy drive), evolution etc., so I've never tried. That's why I like this install, the only extras it has that I don't use is the palmOS support and the floppy. I can live with that :) Oh yeah, I was able to move everything over on a usb flash drive so I didn't need a partition or an extra drive. I'm used to wiping a drive when formating - a habit from a different OS I won't mention - to avoid complications. I'm positive it's easier with Ubuntu.

Side note: nvidia-settings is a package now. It even shows up in the menu!

All in all, Ubuntu Studio 64 Hardy looks sleek, is clean, fast & fun. Right on.

---

### Post by firecat53 on 2008-03-24
FYI, the Ubuntu-desktop package is something that can be safely removed. It's just a meta-package that points to a bunch of other packages included in a default ubuntu installation. The only time it would cause problems is if you tried to do a distribution upgrade without it being installed .... which is easy to reinstall before you upgrade (e.g. gutsy to hardy)..... you just have to remember to reinstall it first :)

Scott

---

### Post by pearjam on 2008-03-24
> **firecat53 said:**
> FYI, the Ubuntu-desktop package is something that can be safely removed. It's just a meta-package that points to a bunch of other packages included in a default ubuntu installation. The only time it would cause problems is if you tried to do a distribution upgrade without it being installed .... which is easy to reinstall before you upgrade (e.g. gutsy to hardy)..... you just have to remember to reinstall it first :)

Scott



I will have to remember that, that is great info!

---

