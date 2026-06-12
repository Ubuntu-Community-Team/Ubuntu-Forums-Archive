---
title: "iMacG3 Dapper-upgrade report."
date: 2006-04-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by Doobie9 on 2006-04-23
[FONT=Garamond][COLOR=Black]I've upgraded the iMacg3 700mhz/768 Ram machine of mine to Dapper Drake Beta, which has fixed about 2 problems, while making about 8 news ones. 
These are the steps I went through and the problems they caused:

[/COLOR][/FONT][LIST]
[*][FONT=Garamond][COLOR=Black]I upgraded to Dapper via 'gksudo "update-manager -d"[/COLOR][/FONT]
[*][FONT=Garamond][COLOR=Black]I got an error regarding a CD-based repository, had to update using apt-cdrom. It worked after this.[/COLOR][/FONT][/LIST][LIST]
[*][FONT=Garamond][COLOR=Black]The update ran for a few hours, restarted. Then Open-Office Writer wouldn't start (Gave an error of "ooffice2' not found, something like that.) I fixed this by forcing a reinstall.[/COLOR][/FONT][/LIST][FONT=Garamond][COLOR=Black]Some things work better. The new Firefox is great, but there are some issues with this machine:

[/COLOR][/FONT][LIST=1]
[*][FONT=Garamond][COLOR=Black]Sleep mode still is not fixed (They have to fix this!) in this version. I press the sleep buttons, nothing happens. Even activating suspend in the Power Control preferences doesn't work.[/COLOR][/FONT]
[*][FONT=Garamond][COLOR=Black]The sound volume can no longer be adjusted by using the volume control buttons or the gnome-panel gui. I must upen alsa-mixer and use that to adjust the volume. This is rather annoying. And the headphone bug is still active, it seems.[/COLOR][/FONT]
[*][FONT=Garamond][COLOR=Black]My mac partition used to mount rw, now it mounts root and locked, and there's no change to my fstab file so I don't understand what's going on here. So my fstab didn't fstab me in the back! :-k
[/COLOR][/FONT]
[*][FONT=Garamond][COLOR=Black]Built-in CD Burner doesn't burn. It's recognized, and most burning programs go through the preparations but they always return an error, just as in breezy.[/COLOR][/FONT]
[*][FONT=Garamond][COLOR=Black]Sometimes windows lock up and need to be force-quit.[/COLOR][/FONT]
[*][FONT=Garamond][COLOR=Black]And last, but certainly not least, my big, beautiful trash icon has been squished! It doesn't look as nice as the old gnome trash-can. And when I replace it looks alright for a little while, then it gets squished again!
[/COLOR][/FONT][/LIST][FONT=Garamond][COLOR=Black]That said, more things work than don't. Divx playback is better than in the mac-os. There's less memory footprint, and Firefox is a [COLOR=Red]lot [COLOR=Black]faster. So, G3 iMac users want to use Dapper, expect some frustrations](*,).

That's my report. Share some of your experience if you know how to fix some of these issues. And, if there is no fix for them currently, should I make a bug-report?
[/COLOR][/COLOR][/COLOR][/FONT]

---

### Post by ssam on 2006-04-24
for number 6, maybe you could try a different theme or icon set. system -> prefs -> theme.

number 3, could it be that the hfs disk has been uncleanly unmounted? could you attach the output of
```
dmesg
```

i'd file 1,2 and 4 as seperate bugs. for 5 have a look at [https://wiki.ubuntu.com/DebuggingProgramCrash](https://wiki.ubuntu.com/DebuggingProgramCrash) and file individual bugs for each program that is effected.

also see [https://wiki.ubuntu.com/ReportingBugs](https://wiki.ubuntu.com/ReportingBugs)

---

### Post by Rxke on 2006-04-24
during install, do you see pbbuttonsd 'failed'? (I have that, and from the bugreports, pbbuttons is still in some tinkering state, which makes it potentially interfere w/ powersettingsstuf and of course volume/eject etc. keys...

---

### Post by Doobie9 on 2006-04-24
[quote=Rxke]during install, do you see pbbuttonsd 'failed'? (I have that, and from the bugreports, pbbuttons is still in some tinkering state, which makes it potentially interfere w/ powersettingsstuf and of course volume/eject etc. keys...[/quote]

No, I did not. As far as I can tell pbbuttonsd installed correctly. It's even running right now. From top:

 3709 root      15   0  3480  768  584 R  1.9  0.1   0:01.39 pbbuttonsd

It's really baffling. The only thing I feel like doing that would fix it is enough people make bug reports. I'm kind of new to all this, so I'm learning as-I-go. Once I figure out how to make a proper bug report I surely will. :-k

It's a bit embarrassing to be new to Linux. Kind of like being new to quantum physics. Although, probably a lot more enjoyable :).

---

### Post by Doobie9 on 2006-04-24
[quote=ssam]for number 6, maybe you could try a different theme or icon set. system -> prefs -> theme.

number 3, could it be that the hfs disk has been uncleanly unmounted? could you attach the output of
```
dmesg
``` 
[/quote]

Alright. This is a little embarrassing, but I'm not all that experienced with Linux. I'm enthusiastic about it, I learn an awful lot about it every day. I like it. But, some of this stuff still flies right over my head. It doesn't once I learn it, however. :-k

So could you explain to me more about how to attach the output of dmesg?

---

### Post by Doobie9 on 2006-04-24
Alright, I did do an dmesg and grepped it for 'mount' and this is the line I got:

[ 4032.343771] HFS+-fs: write access to a jounaled filesystem is not supported, use the force option at your own risk, mounting read-only.

Could it be that the newer version of the HFS system for Linux doesn't support journaled? If so, how come it could write perfectly fine in breezy?

---

### Post by farruinn on 2006-04-25
[quote=Doobie9][ 4032.343771] HFS+-fs: write access to a jounaled filesystem is not supported, use the force option at your own risk, mounting read-only.

Could it be that the newer version of the HFS system for Linux doesn't support journaled? If so, how come it could write perfectly fine in breezy?[/quote]

What exactly does the line for this drive look like in your fstab? As far as I know, hfs+ journaled is still very experimental in linux. I'm able to mount my hfs+ partition with 'mount -t hfsplus /dev/hdaX /mount/point'

Also, before filing bug reports it's a good idea to search for any similar bugs. Filing duplicates won't get things fixed any faster :)

---

### Post by Doobie9 on 2006-04-25
Well now it looks like:

/dev/hda3       /media/mac      hfsplus defaults,rw,user,auto           0       0

But it used to be:

/dev/hda3       /media/mac      hfsplus rw,user,auto           0       0

Because I'm trying all kinds of different shit to get this to work. I checked malone for some of these bugs and they don't show up, so either they're not filed yet or I'm not searching correctly.

---

### Post by Ptero-4 on 2006-04-25
My breezy can easily read and write to my just installed Panther partition which uses hfs+ journaled. It's probably a regresion bug in dapper's hfs+ fs module.

---

### Post by Doobie9 on 2006-04-25
Hmm. That sounds like something I ought to report.

---

### Post by Doobie9 on 2006-04-27
Yahoo! Yayayayayya. I fixed the CD-burning issue! Hell yea!

:-D:D:KS\\:D/\\:D/=D>8-)[-o<

If you can't burn CDs, try enabling force in gnomebaker, and changing the size of the disc you burn to 650mb!

---

