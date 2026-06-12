---
title: "FLASH FOR 64bit USERS - HOW TO"
date: 2005-10-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by hammett111 on 2005-10-18
Okay K/Ubuntu users some helpful advise from the friendly team of SuSe 10 users. This is how you get flash to install for 64bit Linux:

STEP 1: Download the linux(32bit) flash installer from Macromedia [http://www.macromedia.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.macromedia.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

STEP 2: In "flashplayer-installer", edit line 249 from "i[3456]86)" to "i[3456]86|x86_64)"

STEP 3: Run the installer and install into your mozilla compatible browser.

STEP 4: Open Firefox or Thunderbird and YES!!! She works.

BEAWARE!!! This doesnt work for all setups, works on mine, so have fun!!

---

### Post by ikrylon on 2005-10-19
Hey bud.  I tried your fix, and after that, firefox didn't load.

---

### Post by hammett111 on 2005-10-19
What does the console say when you run firefox from the command?

---

### Post by RAOF on 2005-10-19
I'm pretty sure this will only work if you are using a 32bit firefox binary - 64bit binaries don't like linking to 32bit libraries.  This will certainly get the installer to run, and copy the libraries into the appropriate places, but apart from that... Have you tested this on an ubuntu install at all?

---

### Post by hammett111 on 2005-10-19
I have tested it on the 64bit SuSe 10 I am running and Firefox loads flash fine

---

### Post by eph on 2005-10-19
i also get those errors.

```
(firefox-bin:12463): Gdk-WARNING **: locale not supported by Xlib

(firefox-bin:12463): Gdk-WARNING **: cannot set locale modifiers
LoadPlugin: failed to initialize shared library libXt.so [libXt.so: cannot open shared object file: No such file or directory]
LoadPlugin: failed to initialize shared library libXext.so [libXext.so: cannot open shared object file: No such file or directory]

[1]+  Segmentation fault      firefox

```

---

### Post by RAOF on 2005-10-19
[QUOTE=hammett111]I have tested it on the 64bit SuSe 10 I am running and Firefox loads flash fine[/QUOTE]
It is entirely possible that they ship a 32bit firefox binary, precisely so you can do this trick.  You could check this by running readelf on the firefox binary.  That will tell you what architecture it's compiled for.

---

### Post by rplantz on 2005-10-19
I tried this approach. Firefox loads, but as soon as I go to a site that uses Flash, Firefox dies.

With Hoary, I used a chroot to run 32-bit Firefox. That worked fine, although I didn't do a thorough test.

Without the chroot on Breezy, I've found glpflash to sorta work. When I use some Flash features, my keyboard no longer responds. Reload the page, and the keyboard comes back.

Fortunately, my Macintosh is here. When I really need to use Flash, I simply "cheat" and move to the Mac.

Bob

---

### Post by toujours on 2005-10-19
How about libflash-mozplugin in Synaptic ?

It's not compatible with the latest version of flash I believe, but works with more basic flash buttons and effects...

---

### Post by hammett111 on 2005-10-20
Yip my suse firefox is compiled for AMD64. Imma total SuSe convert now, all our Pcs here have switched to it.

---

### Post by zekolas on 2005-10-21
That is because suse uses a 32bit version of firefox, and you can install the 32 bit compiled version of firefox in ubuntu 64 and use the flashplayer plugin if you want.

---

### Post by xthaparian on 2005-10-22
Yes guys I Can confirm that the suse uses the 32 Bit Firefox by default. 

I was also surprised when I saw the Flash working out of the box in my suse.

Lets not waste time on this thread anymore.

---

### Post by rplantz on 2005-10-23
[QUOTE=xthaparian]Yes guys I Can confirm that the suse uses the 32 Bit Firefox by default. 
[/QUOTE]

Does this imply that we can install 32-bit Firefox without doing a chroot?

I already had to install various ia-32libs for openoffice and some of my own work. Perhaps I could just replace my 64-bit Firefox with the 32-bit version?

Has anyone tried this?

Bob

---

### Post by Snifffurt on 2005-10-26
Hi

[QUOTE=rplantz]Does this imply that we can install 32-bit Firefox without doing a chroot?

I already had to install various ia-32libs for openoffice and some of my own work. Perhaps I could just replace my 64-bit Firefox with the 32-bit version?
[/QUOTE]

I don't know how to install a 32 Bit FF on Ubuntu and I don't know if it will work with ubuntu breezy badger.
On my Gentoo installation I have done so. But it seems that Gentoo linux has better improved ia32libs. Eg on my Gentoo installation acroread 7 works without chroot in the 64bit environment, on ubuntu i did not get it working jet.

Regards

Sniff

---

