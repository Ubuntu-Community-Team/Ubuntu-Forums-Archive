---
title: "Burn to DVD files &gt; 4GB"
date: 2007-03-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by John Jason Jordan on 2007-03-18
I made a lot of coasters before I figured out what was wrong. Evidently you cannot include a file > 4 GB when you burn a DVD. GnomeBaker burned all the rest of the files and left out the file that was over 4 GB. So did Nautilus; neither gave a warning or error message. K3b gave me a warning, so at least I didn't make a coaster.

The problem seems to be mkisofs, with or without growisofs. I'm not clear what these two files do, but they are at the root of the problem.

This is kind of lame. Does anyone know how I can burn a DVD that contains files over 4 GB in size?

---

### Post by ViperKnight on 2007-03-19
You have to specify the DVD format as "UDF" for it to burn files larger than 4GB.  It's the same in Windows.

I think K3B has this option somewhere....but I haven't tried it.  There's a "Add UDF Structures" option available under "FileSystem" from the Burning window in K3b.  But as I said....I haven't personally tried it so I can't confirm that it works.  But I'm pretty sure it has to do with burning the DVD as a UDF instead of standard ISO due to the filesize limit.

Hope that helps.

---

### Post by stoer on 2007-03-19
> **John Jason Jordan said:**
> I made a lot of coasters before I figured out what was wrong. Evidently you cannot include a file > 4 GB when you burn a DVD. GnomeBaker burned all the rest of the files and left out the file that was over 4 GB. So did Nautilus; neither gave a warning or error message. K3b gave me a warning, so at least I didn't make a coaster.

The problem seems to be mkisofs, with or without growisofs. I'm not clear what these two files do, but they are at the root of the problem.

This is kind of lame. Does anyone know how I can burn a DVD that contains files over 4 GB in size?

Hi,
Sorry but i cannot offer you  much in the way of help.
But i do use K3b as my burning software of choice.  I've never had to alter the settings from default since installing the program and i burn on average 2 or 3 dvd's per week, both iso format and ripped.  
I have a dual boot system, winxp-ntsc and ubuntu with a 10 gig fat partition for shared data.   I did make the mistake in the beginning of trying to copy/rip images to the fat partition which of course cannot be done due to file size limitation of the fat32 system (4 GiB minus 1 Byte). But other than that no problems at all with burning dvd's.
I asume you're burning using "new dvd video project?".

Go to "File" >

"New Project" and select "New DVD Video Project." It will lay out the DVD project for you with the VIDEO_TS and AUDIO_TS folders.

You just drop the corresponding contents into them.

Success.

---

### Post by stoer on 2007-03-19
Hi again...
i'm working but had a little time to Google your problem.
Seems there is a known bug, depends on whether you're burning data dvd's or film dvd's.
Some people don't have it and others, like your self do. :confused: 

see [http://ubuntuforums.org/showthread.php?t=352386&highlight=k3b](http://ubuntuforums.org/showthread.php?t=352386&highlight=k3b) which is possibly related.

Also there is a new release, 1.0  where this problem has been addressed. [http://k3b.org/](http://k3b.org/)

Like i said, success. :)

---

