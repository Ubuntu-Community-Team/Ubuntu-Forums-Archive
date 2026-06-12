---
title: "Creating an ubuntu cd"
date: 2008-10-22
forum: x86 64-bit Users
---

### Post by shattered222000 on 2008-10-22
Ok I downloaded the ubuntu iso, now what? I want to dual boot with windows vista 64 bit and i want ubuntu to be 32 bit so i can have both 64 bit and 32 bit operating systems. I think I have to restart my computer with a cd but i am having trouble mounting ubuntu to cd so I can restart and have it detect it and install it. I have an hp by the way. I also think i have to push f9 when starting up to get it to detect the boot cd but its just not working. PLEASE someone help me, I just want ubuntu :(

---

### Post by panhandle on 2008-10-22
It is unclear from your email if you have actually burned the .iso image to CD. Have you? If not, burn at a relatively slow speed and make sure that Windows does not format the CD.

Next, you will have to boot from this CD--you may have to enable booting from your DVD/CD drive in BIOS for this to happen

---

### Post by Therion on 2008-10-22
[How to Burn an .iso](https://help.ubuntu.com/community/BurningIsoHowto)

[How to Dual Boot Windows & Ubuntu](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

---

### Post by shattered222000 on 2008-10-22
trying it out now ty

---

### Post by shattered222000 on 2008-10-22
getting the same thing, i cant get my hp computer to recognize the start up disc

---

### Post by panhandle on 2008-10-22
So what exactly is happening?

You place the disc in the tray, reboot, and what? The system just boots into XP or Vista or whatever?

Make sure your system has booting from the CD-ROM drive enabled.

Did you read the howtos that Therion posted?

---

### Post by shattered222000 on 2008-10-22
I restart with the burned dvd, I push f9 to get it to look for the ubuntu setup, then it just goes and starts up in vista after a while.

---

### Post by panhandle on 2008-10-22
Since pressing key (whether ESC, f2, f9) during startup for different makes and models of machines has varying results, I don't actually know what pressing f9 does for you in particular.

Does pressing f9 allow you to change the boot sequence? If not or if it does and you haven't done so yet, make booting from CD/DVD the first option.

---

### Post by shattered222000 on 2008-10-22
Yeah it changes the booting sequence, it allows me to choose which device to boot from. In the menu it is the boot device options thats what f9 represents. then i chose my cd/dvd rom drive and it goes to that for like 30 seconds then just starts back up in vista

---

### Post by panhandle on 2008-10-22
Hmmm...sounds like you need to verity the md5 sum.

Read the first howto posted by therion for instructions. Don't worry, it is not difficult.

---

### Post by Therion on 2008-10-23
Take a quick look at the CD you're trying to boot from.  Boot into Windows put the CD in the drive and then go look at the files on the CD.  

If you see ONE file on the CD with a .iso extension, you have NOT burned the CD correctly.  If you see lots of files on the CD and maybe a few folders your CD is bootable and we'll need to look at other things to correct this issue.  

My suspicion is that you did not burn the CD correctly.

---

### Post by shattered222000 on 2008-10-23
Thats what i am thinking, maybe i should just start the cd over. Do you know a way i can get rid of everything on it an start over?

---

### Post by antisa on 2008-10-26
What program did you use for burning the cd? I ask this because some (or maybe all of them - don't know haven't tried them all:)) of them have two options:

1. You can burn the file called *somefile.iso* onto a cd. This process will show you a *somefile.iso* on a cd when you open a cd.

2. You can burn a cd **from** the *somefile.iso* image. This is the option you want if you want to boot ubuntu OS from the cd and when you open a cd you should see some various folders and files which is different from the first case scenario in which only the *somefile.iso* file will be displayed.

---

