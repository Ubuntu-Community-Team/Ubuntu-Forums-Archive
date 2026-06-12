---
title: "Wine and Ubuntu 8.0.4"
date: 2008-04-01
forum: Wine
---

### Post by jeremy04 on 2008-04-01
I recently installed Ubuntu 8.0.4 beta

and i'm trying to get Wine to work.
It installs and appears to install ok.. (i think)

but when i try to do the config or run it , i get:

wine: creating configuration directory '/home/jeremy/.wine'...
Could not load Mozilla. HTML rendering will be disabled.

fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for c000013a

Somebody said to download gecko-0.1.0.cab and put it: 
/usr/local/share/wine/gecko/wine_gecko-0.1.0.cab

that did nothing i tried uninstalling/reinstalling.. no idea how to fix this..:confused:

---

### Post by FrozenFox on 2008-04-01
You do not need the html rendering engine for wine to work with most of your programs. I couldn't tell you how to install it, because i don't need it for anything and thus of course never bothered. I must ask what you need it for, though, and how you installed wine (specifically, what version). What are you trying to run in it, for that matter?

---

### Post by jeremy04 on 2008-04-01
Well I want to run Steam, Starcraft and possibly some other programs.

i have the latest 0.9.4 i believe.. I updated my repositories as well..

the thing is.. it installs wine and it appears in my menu in gnome, when i click on anythign it just doesnt do squat..

so i tried the console and it just gives me that error message for any command wine-related... "winecfg" "wine" , "wine setup" etc...



btw are the forum colors always like this, or is this an april fools joke lol ???

---

### Post by YokoZar on 2008-04-02
It seems like wineprefixcreate is failing.  Try nuking ~/.wine and then rerunning winecfg.

---

### Post by h4mx0r on 2008-04-02
run this command to install gecko engine:
wine iexplore [http://www.winehq.org](http://www.winehq.org)

Taken from the stickied master guide:
[http://ubuntuforums.org/showthread.php?t=497332](http://ubuntuforums.org/showthread.php?t=497332)

---

### Post by carusoswi on 2008-06-15
Any progress on getting wine to work in 8.04.  I upgraded to 8.04 from the previous Ubuntu version, and, since then, a perfectly running installation of both Wine and Crossover is broken.  I deleted Crossover, reinstalled it, no go.

As the OP explained, both programs install fine, but, then, will not function at all.

. . . and, while some find no need for wine, some of us need it in order to make using linux practical . . . for instance, OpenOffice simply doesn't hold a candle to MSOffice.  Not knocking the Open Source ap, but, there are features in MS Access, for instance, that just are lacking in the OpenOffice offering.  MSOffice was working fine in all previous versions of Ubuntu that I have used.  In 8.04, it will not run.  Nothing happens.

Same goes for Adobe PS7.  As it turns out, I no longer have a need for PS7, as I now use Lightzone and Gimp to process all of my photos.

I am all for the advancement of open source, not above paying for a good Linux ap (like Lightzone - which somehow runs in wine - don't know how that works, because you start LZ from its own icon within its directory - doesn't appear on your Applications list - and LZ must install its own version of wine, 'cause wine ain't workin' on my machine, either with or without LZ installed).

. . . but, although I like Linux and Ubuntu, my main concern when using a computer is to get my work done.  For me, it's not fun and games, but my income producing work for which I need the computer.  So when things don't work for me in Ubuntu, I fall back to XP where, like MS or not, most all my applications work most all the time.

Caruso

---

