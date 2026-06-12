---
title: "LapTop Pismo400 Breezy Live CD Install Files???"
date: 2005-10-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by bgotori on 2005-10-14
Hey All

I've been going through this since Hoary 5.04(Same Problem)...

I've just DownLoaded Breezy 5.10(ISO File)Newest File Used Toast 6 to Burn a CD as an ISO 9660 and a Disk Image... The ISO CD comes out as a File, the Disk Image come out as some Folders and a md5sum.txt and a README.diskdefines file... But NO BOOT FILES or and Files to Load the LIVE CD... I've heard that People have used this(Breezy 5.10)but I CAN'T SEEM To Find ANYONE Thats Really Done This(Loaded Breezy Live CD)...

So Whats Up with this ISO File... I've Burned many ISO Disk so I know thats NOT the Problem(Burning ISO Disk). Burned Debian PPC and Gentoo PPC both worked first time.

What are the Files that are Needed at the ROOT Directory to Boot the Breezy 5.10 LIVE CD???


Thanks!!!

Brad

---

### Post by Rxke on 2005-10-15
I (long time ago) burned the ISO with the free Firestarter FX, (search for missingmediaburner, IIRC)  since other programs seemed to be unable to deliver a valid boot-CD... There's some voodoo going on with the Ubuntu ISO's, from the looks of it ;)

---

### Post by bgotori on 2005-10-17
Hey Rxke

Thanks I'll try that, Missing Media Burner and Firestarter FX.

Why would they do that, Non-Standard ISO format... I guess Linux Over Thinking...hahaha

Its Funny all the Computer guys I know at UCLA tried downloading it and same Problem. Funny How Lots of Linux Mags say how easy and straight forward install is, yet None of the Linux guys at UCLA can get it to work with Toast... I'll let them know about using the other Media Burners after I try it out first.

I thought I downloaded a Bad Copy, but since at least 10 of the Linux guys couldn't get it working I didn't feel that Bad.


Thanks!!!

Brad

---

### Post by bgotori on 2005-10-17
Hey Rxke

Well I tried with MessingMediaBurner, Buffer Over Runs...

DownLoaded Firestarter FX, But that won't Burn... NO Burn Button HighLighted... I guess you have to make a Donation before you can Try It Out...
But I WON'T Do That until I see It WORKS FIRST!!!hahaha

Guess I'll just have to Pass on this version of Linux, too many Problems!!!


Thanks Anyway!!!

Brad

---

### Post by Ptero-4 on 2005-10-17
have you tried disk utility in OSX? I have been succesful in burning ubuntu isos with that (in 10.3.9)

---

### Post by div3rg3nt on 2005-10-17
Had a similar issue on my MDD G4. I found a process to make it work though:

1 - Boot into Open Firmware (hold Option-Command-letter O-Letter F)
2 - Not sure if this was necessary, but type 'dev cd', press enter and it should come back with 'ok'
3 - Type 'shut-down', press enter and the system will power down
4 - Hold down the 'C' key and turn your system on

FWIW I am running Open Firmware 3.

Let me know if it helps.

---

### Post by Rxke on 2005-10-17
*slaps head quite hard*

Ouch.
I suddenly remember.... pismo is old world, no? That'd be the problem, then...

(googles)

[http://www.ubuntulinux.org/wiki/InstallOnOldWorldMacs](http://www.ubuntulinux.org/wiki/InstallOnOldWorldMacs) (edit: blind link)


Ah: [http://ubuntuforums.org/archive/index.php/t-34765.html](http://ubuntuforums.org/archive/index.php/t-34765.html) :(

---

