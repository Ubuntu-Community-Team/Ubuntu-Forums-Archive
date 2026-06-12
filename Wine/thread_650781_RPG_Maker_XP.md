---
title: "RPG Maker XP?"
date: 2007-12-26
forum: Wine
---

### Post by l0rdph0enix on 2007-12-26
Ok, I've look here in the forum but still can't find this. I'm somewhat new to the Linux community but no where near new to computers. But I read on an RPG Maker XP forum that they were able to successfully able to install it onto linux via Wine (using the latest version of Wine that's out). So I'm thinking to myself "Sweet now I can leave Winblows since I can work on my game in Linux now" Cuz that's the only reason I've been in windows since I've gotten back into using linux. 
So I restart my computer and go into Linux, let it do it's updates and restart it again for the updates. Then I browse to the folder that has the RPG maker Install in it and open it. I click on the first button (it's a two part install) and nothing happens. So I wait and wait and try a few more times with nothing, so I try the second button, same thing nothing happens. I then go into the installs separate folder and try the setups there with no luck. 

I'd really love to cut my chains from Windblows and migrate fully over to Linux but I can't until I can get this program working for me. Any help would be appreciated.

---

### Post by FranMichaels on 2007-12-26
What OS are you running. Ubuntu? 32-bit version? First off I'd recommend grabbing Gutsy 7.10 if you don't have it.

That said, try a newer version of wine that the one bundled with Ubuntu.

[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

You can just download the deb and double click it. If you prefer to add a repo to get the updates

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

Hope this puts you on the right track. :KS

---

### Post by l0rdph0enix on 2007-12-26
Oh yeah sorry forgot to put that. I was using the Ubuntu 7.10 but i just got done installing the next flavor of it, 8.04 Hardy. 

Comp info:

AMD Sep. 2800 1.6ghz
1.5gig Ram
3 hard drives: 
  40gig Windows
  40gig Linux
  320gig Other
Nvidia GeForce 5200

---

### Post by FranMichaels on 2007-12-26
Adventurous huh? I'm still holding off on testing Hardy until they sort out pulseAudio. Or maybe wait until April for the final release.

What version of Wine are they bundling? 

Did you try grabbing a new version, or running winecfg, and changing some settings (you could set it to Windows XP compatibility mode...)

You can also try running from terminal

wine whatever.exe, and see if any useful error messages come up.

---

### Post by l0rdph0enix on 2007-12-27
I'm in Winblows right now finishing up a Torrent Download so I can't see what error messages if any it gives me from running it at a terminal. Off the top of my head I'm not sure what verison of Wine 8.04 comes with but I know my 7.10 ran WINE 0.9.46, and I've been hearing hear say that 8.04 comes with WINE 0.9.50, not sure how true that is.

Yeah I like trying out New OS's as I find them, got a whole 50cd spendle full of different ones, rangeing from Winblows(1/3) to different flavors of Linux(2/3) So far out of the ones i've test drove, the debian series with Gnome interface are the cleanest and worry free for me.

Just wish i could figure out how to use Lilo instead of grub for dual-booting purposes. I've searched so many sites and forums and tried all I could about how to get Grub working right with out any luck, the only way I can get my Grub working write is with iether a Windows XP disk or a Linux live disk in the cd-rom drive at boot up and NOT selecting to boot from the cd to get the OS menu. My computer is strange like that :P. If the disk isn't in the try then an OS can't be found. :lolflag:

---

### Post by FranMichaels on 2007-12-27
Wow. I haven't had a dual-boot in over 2 years :)

Anyway, if WINE doesn't ultimately do the trick, and you want to dump your Windows partition, why not try running Windows within a VM?

If you can handle all those OS's, installing in [qemu]("http://fabrice.bellard.free.fr/qemu/") or [VirtualBox]("http://www.virtualbox.org/")

---

### Post by l0rdph0enix on 2007-12-27
> **FranMichaels said:**
> Adventurous huh? I'm still holding off on testing Hardy until they sort out pulseAudio. Or maybe wait until April for the final release.

What version of Wine are they bundling? 

Did you try grabbing a new version, or running winecfg, and changing some settings (you could set it to Windows XP compatibility mode...)

You can also try running from terminal

wine whatever.exe, and see if any useful error messages come up.

Ok I ran it from the terminal and got this.

```
 wine SetupMenu.exe
Usage:
  Install a product:
    msiexec {package|productcode} [property]
    msiexec /i {package|productcode} [property]
    msiexec /a package [property]
  Repair an installation:
    msiexec /f[p|o|e|d|c|a|u|m|s|v] {package|productcode}
  Uninstall a product:
    msiexec /x {package|productcode} [property]
  Advertise a product:
    msiexec /j[u|m] package [/t transform] [/g languageid]
    msiexec {u|m} package [/t transform] [/g languageid]
  Apply a patch:
    msiexec /p patchpackage [property]
    msiexec /p patchpackage /a package [property]
  Modifiers for above operations:
    msiexec /l[*][i|w|e|a|r|u|c|m|o|p|v|][+|!] logfile
    msiexec /q{|n|b|r|f|n+|b+|b-}
  Register a module:
    msiexec /y module
  Unregister a module:
    msiexec /z module
  Display usage and copyright:
    msiexec {/h|/?}
NOTE: Product code on commandline unimplemented as of yet

Copyright 2004 Vincent B&#65533;ron



```

Hope that helps.

Oh and 8.04 comes bundled with Wine 0.9.51.

---

### Post by FranMichaels on 2007-12-27
Okay, that's way over my head.

Have you run

```
winecfg
```

at least once?

Also, what version of RPG Maker XP is it?

It seems that people have gotten [1.02a]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=5206") mostly working.

> What works

    * Starting new projects, opening projects and saving projects
    * Managing maps
    * Managing events
    * Database management
    * Materialbase management
    * Script editor (buggy when searching/jupming [sic] into lines)
    * Playtesting games from the editor
    * Playing existing games (in non debug mode) 

---

### Post by l0rdph0enix on 2007-12-28
> **FranMichaels said:**
> Okay, that's way over my head.

Have you run

```
winecfg
```

at least once?

Also, what version of RPG Maker XP is it?

It seems that people have gotten [1.02a]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=5206") mostly working.

Yeah ran winecfg, and got it to act like WinXp that still didn't get it working. And it is the 1.02a version of RPG Maker XP. I also posted a post at the forum where they posted that it works in Linux now, to ask what flavor of linux they tested it in, no responds yet. So I'm still bouncing back and forth between winblows and linux.

---

### Post by GGLucas on 2007-12-28
If you're trying to get anything at all to work in wine, it's a good idea to check the Application database first, there's an entry for RPG Maker XP in it, they got it working, but it doesn't seem like it works well enough to use yet, which means it's very buggy.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=5206]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=5206")

---

### Post by l0rdph0enix on 2007-12-28
> **GGLucas said:**
> If you're trying to get anything at all to work in wine, it's a good idea to check the Application database first, there's an entry for RPG Maker XP in it, they got it working, but it doesn't seem like it works well enough to use yet, which means it's very buggy.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=5206]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=5206")

Well that just sucks, Ubuntu isn't in the list as one of the OS's they tested it on. I have an Open Suse 7.1 pro. Disk set, are they any options on if it's worth it or not for me to start all over and install Suse instead of using Ubuntu? Pros and Cons iether way would be helpful.

---

### Post by GGLucas on 2007-12-28
You can see that:

> What does not [work]

    * Menu bar
      (Critical error C0000005 at address 004749BS)
    * Using the HTML help works but crashes when the help window is closed after browsing help
      (Critical error C0000005 at address 00000000)
    * Listening to BGM/BGS while editing/playing (they still basically work though, others can hear them when releasing a game)
    * Playing encrypted games
    * Compressing/encrypting games
      (can't access from main menu since it doesn't work)


So even if you get SuSE, it would still be far from usable. It rarely matters which distribution you use for how apps work in wine, wine is the same on all distros (though you could have different versions on them), so changing distros shouldn't do you much good.

---

### Post by FranMichaels on 2007-12-28
A new version of wine is out.

[http://winehq.org/?announce=0.9.52]("http://winehq.org/?announce=0.9.52")

There is a slim chance they fixed the problem, right? ;)

Anyway, I still recommend [qemu]("http://fabrice.bellard.free.fr/qemu/"). If this is the only app you need, why boot into Windows to use it? You can make it seamless with [rdesktop]("http://www.rdesktop.org/") (run the app without seeing the windows desktop)

There are plenty of how-to's floating around. If you can handle so many OS installs, you won't have much trouble making a disk image and installing Windows. :)

Both qemu and rdesktop are in the Ubuntu repositories.

I have done it once, but I deleted it as I didn't need XP :) Just wanted to see how it worked. Although it is a neat and painless way to test other OS's. :KS

---

### Post by l0rdph0enix on 2007-12-29
> **FranMichaels said:**
> A new version of wine is out.

[http://winehq.org/?announce=0.9.52]("http://winehq.org/?announce=0.9.52")

There is a slim chance they fixed the problem, right? ;)

Anyway, I still recommend [qemu]("http://fabrice.bellard.free.fr/qemu/"). If this is the only app you need, why boot into Windows to use it? You can make it seamless with [rdesktop]("http://www.rdesktop.org/") (run the app without seeing the windows desktop)

There are plenty of how-to's floating around. If you can handle so many OS installs, you won't have much trouble making a disk image and installing Windows. :)

Both qemu and rdesktop are in the Ubuntu repositories.

I have done it once, but I deleted it as I didn't need XP :) Just wanted to see how it worked. Although it is a neat and painless way to test other OS's. :KS

ok i'll try qemu/rdesktop in a few minutes to see how well they are. I'll let you know how smoothly it goes over, this may just be the "file" i need to break out of winblows shackles.

---

### Post by l0rdph0enix on 2007-12-31
Well i tried out the qemu and that "worked" loaded up Win2000 SP4 on it, installed the RPG Maker XP and DirectX 9c (required for the program) It opened my Game up for working on ok, but when I go to test it out, it's slower then moving glaciers. I gave the qemu 365mb of ram to work with but that still didn't do it. It only let's you work with a "cpu" that's 333mhz strong and I can't find a way to increase the strength of the emulations CPU. So then I tried Virtualbox, that was a headache to install properly, then once I had it installed it throws up nothing but errors, last batch dealed with the USB modal and what not. Couldn't find a place in the settings to disable USB or how to fix it so for now, i'll just work with my dual-booting. Thanks everyone for your help with this. I'll keep looking for (free) ways to get this working, and post my findings incase someone else has my problem.

---

### Post by artir on 2007-12-31
An open source version of it is being developed: Easy Rpg

---

### Post by Peyton on 2007-12-31
Link:

[http://easyrpg.sourceforge.net/](http://easyrpg.sourceforge.net/)

---

### Post by FranMichaels on 2008-01-02
> **l0rdph0enix said:**
> Well i tried out the qemu and that "worked" loaded up Win2000 SP4 on it, installed the RPG Maker XP and DirectX 9c (required for the program) It opened my Game up for working on ok, but when I go to test it out, it's slower then moving glaciers. I gave the qemu 365mb of ram to work with but that still didn't do it. It only let's you work with a "cpu" that's 333mhz strong and I can't find a way to increase the strength of the emulations CPU...

Nice job. Did you try using kqemu with qemu? I personally haven't as I started using kvm by the time the kqemu was GPL'd. That should give it a serious speed boot.

[http://fabrice.bellard.free.fr/qemu/kqemu-doc.html](http://fabrice.bellard.free.fr/qemu/kqemu-doc.html)

There is a kqemu package in the Ubuntu repositories. If it's slow to do to software rendering doing the directx work... It's going to be slow no matter what :(

---

### Post by randavance on 2008-02-03
I too happen to be a big RPG maker fan and was real bummed out when I finally decided to drop windows for Ubuntu (it was worth it though). And yeah, RPG Maker XP doesn't have much Wine support, but RPG Maker 2003 does. It's lesser graphics by far, but it's not bad at all and even has a side veiw battle system that's way cooler than the one in RPG Maker XP. Just hunt it down, install, and enjoy.

---

