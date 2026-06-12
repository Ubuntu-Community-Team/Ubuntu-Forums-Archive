---
title: "Wine + MS Office 2003 + &quot;bold bug&quot;: how to apply patch?"
date: 2008-05-16
forum: Wine
---

### Post by dolor on 2008-05-16
Hi,

this is a beginner's question.

I am on xubuntu gutsy and running wine 0.9.59.

I managed to install MS Office 2003 but I have the "bold bug" that was recently fixed:

[http://www.winehq.org/pipermail/wine-patches/2008-April/052863.html](http://www.winehq.org/pipermail/wine-patches/2008-April/052863.html)

However, I don't quite understand how to apply this patch, as I cannot find the "freetype.c" file anywhere on my system. 

Do I have to compile Wine from source to do this (which would be terrible), or can I apply it any other way?

Thanks a lot in advance!

---

### Post by Iehova on 2008-05-17
You'll have to compile from source, but it isn't so painful!

You'll have to uninstall your current version of wine from synaptic, I believe.

The latest wine release (well, release candidate ;)) is [here](http://downloads.sourceforge.net/wine/wine-1.0-rc1.tar.bz2) (although if it's a while before you see this message check winehq.org for the latest release.

Download it and extract it somewhere (I have a Sources directory in my home folder for this). You'll want to keep the source folder, so put it somewhere safe.

In a terminal run "sudo apt-get build-dep wine". That'll install a whole load of stuff and fix your dependency issues. 

Download your wine patch. Last time I patched, I saved it in the same folder as the files needing patching. I'm not sure if that's required.

Now navigate in a terminal to the folder where the patch file is.

You'll need to run "patch -p1 < ./name-of.patch"

You can make sure it'll work first by doing "patch -p1 --dry-run < name-of.patch"

Then run */path/to/wine/source/*tools/wineinstall/

If everything has thus far gone to plan, compiling will take a while. That should work, if it doesn't, I'm not an expert on the matter so I might not be of much use.

---

### Post by the dsc on 2008-06-19
[sorry, wrong topic]

---

