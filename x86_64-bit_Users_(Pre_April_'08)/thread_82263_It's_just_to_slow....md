---
title: "It's just to slow..."
date: 2005-10-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by thefaint on 2005-10-26
[http://kubuntuforums.net/index.php?topic=1111.new#new]("http://kubuntuforums.net/index.php?topic=1111.new#new")

---

### Post by drummer on 2005-10-26
You mean firefox is slow? or ubuntu in general?
if it's FF, then yes, it is slow.. you can install the FF version from mozilla.org which is faster than the ubuntu build (some issue specific with the ubuntu build) or even install the beta 2 version which has significant performance increases (i'm using beta 2 right now and it's great).

There's a howto here: [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

---

### Post by thefaint on 2005-10-26
Thanks for the reply,
but not just the firefox is to slow.. the whole system is to slow.. don't know why :( aghr..

Something's wrong.. 
my HDD is ok (i think):
root@yes:~# hdparm -tT /dev/hda

/dev/hda:
 Timing cached reads:   2992 MB in  2.00 seconds = 1493.99 MB/sec
 Timing buffered disk reads:  158 MB in  3.07 seconds =  51.51 MB/sec

My video card is OK .. everything in my hardware seems is perfect with other OS's (Windows is to fast with this configuration!!!)

---

### Post by drummer on 2005-10-26
Your system is similar to mine (same cpu and ram) but mine doesn't feel slow at all. Are there any processes running, constantly using up cpu? (run 'top' in a terminal) maybe something is getting it's knikkers in a knot and needs killing, or reinstalling/configuring.

EDIT - and that hdparm test is quite flakey.. you can get all sorts of results from it, so it isn't a good benchmark.

---

### Post by thefaint on 2005-10-26
no.. it is not from any program or something who's eating my ram.. my load averages are ~00.30.. 
the whole system starts slow
when I want to use some kind of program.. it starts so slow.. i'm waiting around 3-4 seconds to start (not for the first time) firefox or gimp or kcalc!!! :( I'm so disappointed from Breezy :evil:

---

### Post by daveisadork on 2005-10-26
Are you using the NVIDIA drivers or the free ones that are included with X.org?

---

### Post by thefaint on 2005-10-26
[QUOTE=daveisadork]Are you using the NVIDIA drivers or the free ones that are included with X.org?[/QUOTE]
NVIDIA drivers...

---

### Post by thefaint on 2005-10-26
well.. i'm downloading kubuntu breezy for i386 and I'll try this one.. hope it will be faster than amd64 version

---

### Post by sotua on 2005-11-10
[QUOTE=drummer]Your system is similar to mine (same cpu and ram) but mine doesn't feel slow at all. Are there any processes running, constantly using up cpu? (run 'top' in a terminal) maybe something is getting it's knikkers in a knot and needs killing, or reinstalling/configuring.

EDIT - and that hdparm test is quite flakey.. you can get all sorts of results from it, so it isn't a good benchmark.[/QUOTE]

I have a similar problem - I have an AMD64 3000+, a SATA 80GB drive, nvidia FX5200 (nvidia drivers), 512MB RAM, and the system is dog slow. 

I know, I run heavy java stuff :) (software development with eclipse) but I never had this problem running eclipse from a P4 @ 2.8Ghz with the same 512MB of ram, a slower drive, and onboard intel graphics!!! (windows or linux). I'm pretty pissed since I asked my company for an AMD64 machine over an Intel one citing better performance for the $$$, and now I'm stuck with this thing that feels  s l o w w w  w . . . :confused: 

I'm going to try replacing the Sun 64-bit JVM with the 32-bit one and see.

Anybody who can shed any light on this... 

Maybe the KDE amd64 build is dog slow... for example, it takes one or two seconds for kmail to spawn the new message window after I click the button... that's slower than thunderbird! :o

---

### Post by lister on 2005-11-11
I recently installed Ubuntu on an AMD64 laptop and through the install noticed it was very slow.  I found that an APIC error was being written to the syslog very rapidly - hence the slow down.

Try adding [FONT="Courier New"]acpi=off noapic nolapic[/FONT] to your kernel boot line and rebooting.  No problems since doing that for me.

---

### Post by Ribs on 2005-11-13
It's a long shot, check the output of cat /proc/cpuinfo

See if your mhz setting is what you're expecting... If you find it's too low, uninstall powernowd and reboot. That should fix it. I had this problem on my laptop where powernowd would set it to around 70mhz and never increase it...

Regards,

---

### Post by dmxubuntu on 2005-11-25
[QUOTE=lister]
Try adding [FONT="Courier New"]acpi=off noapic nolapic[/FONT] to your kernel boot line and rebooting.  No problems since doing that for me.[/QUOTE]

Would you give the complete command line please? I've been trying to do this for some other similar problem, but I can't seem to turn apic off. Maybe I'm not writing it correctly.

Tks
Denis

---

### Post by dmxubuntu on 2005-11-29
[QUOTE=dmxubuntu]Would you give the complete command line please? I've been trying to do this for some other similar problem, but I can't seem to turn apic off. Maybe I'm not writing it correctly.

Tks
Denis[/QUOTE]

Ok. Found it.

*Linux acpi=off noapic nolapic*

Or whatever other kernel you want to boot. Simple as that.

Thing is, doing that, it doesn't recognize my network and sound cards. Probably more is missing. It's a hassle to dig out the commands to modprobe the correct modules for each device not detected
 :???:

---

### Post by sotua on 2005-11-30
[QUOTE=sotua]
I'm going to try replacing the Sun 64-bit JVM with the 32-bit one and see.
[/QUOTE]

Well, what do you know - it looks like the Sun JDK 1.5 amd64 build has a memory leak somewhere, since I switched to the 32-bit JDK everything's as zippy as it's supposed to be.

---

### Post by Kango_V on 2005-11-30
Have you got the K8 kernel installed?  I'm runing that and it works a treat :)

Also, i see you are an Eclipse user.  We have found that running Eclipse under the IBM JDK 1.4 is rock solid and VERY fast.  Our tests inidacted around 30% improvement.  We then set Eclipse to compile using the IBM JDK 5.0 VM.

Both those VMs are 64Bit btw.

This setup is cool.  I've got Eclipse loading in 7 seconds!! (I have got 2 Fujitsu 15K disks lol).

Hope this helps.

daz

---

### Post by sotua on 2005-12-01
[QUOTE=Kango_V]Have you got the K8 kernel installed?  I'm runing that and it works a treat :)
[/QUOTE]

2.6.12-10-amd64-generic

Will the amd64-k8 kernel run on an Athlon 64 3000+ ?

[QUOTE=Kango_V]
Also, i see you are an Eclipse user.  We have found that running Eclipse under the IBM JDK 1.4 is rock solid and VERY fast.  Our tests inidacted around 30% improvement.  We then set Eclipse to compile using the IBM JDK 5.0 VM.
[/QUOTE]

Running it with the 1.4 jvm is faster than with the 5.0? Interesting!

Will give IBM's JDKs a spin - come to think of it, I don't know why I hadn't tried them before :D

---

