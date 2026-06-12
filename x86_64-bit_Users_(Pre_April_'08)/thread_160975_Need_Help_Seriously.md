---
title: "Need Help Seriously"
date: 2006-04-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by mrmime00 on 2006-04-16
My son inserted the wrong cd of ubuntu instead of the live cd and has completely erased my hard drive on my ibook g4 and installed ubuntu. how can i reinstall mac os x or 9. i have tried booting from the cd by pressing c and it doesnt boot. can anyone here help me :O(.

---

### Post by imacQ on 2006-04-16
good luck...:twisted: 
boot into Open Firmware (hold down command-option-O-F while the computer starts up).  Then at the prompt type

boot cd:,\\tbxi

---

### Post by mrmime00 on 2006-04-16
That really didnt do anything do you have any more options?

---

### Post by 3rdalbum on 2006-04-17
An OS 9 or OS X CD should boot if you hold down the C key while starting up. You've got to hold it down as soon as you possibly can. Does the computer seem to wait a little while with a grey screen before going into Yaboot?

---

### Post by coolowlBrisbane on 2006-04-17
Except that now it's a Linux machine, not a Mac! It's possible that if you turn off the machine (and remove the battery for the time being) *then* put in the Mac CD you want to re-instal from *then* hit the power button to start up that it might startup from the CD. That system worked on a Compaq laptop with linux. Alternately, download Dariks Boot and Nuke [DBN is 'dban' - download the ISO and burn it as a ISO, it will work just like that] and totally wipe the disk, overwriting with zeros and start from a relatively clean disk. Then the Mac CD should startup normally.
Elaine

---

### Post by mrmime00 on 2006-04-17
Okay guys i would like to thank all of you for trying to help me here but i am unable to fix the problem. you see when the system loads up Bootstrap loads up and gives me two options load up from cd or start ubuntu. when i clicked c to start from cd it doesnt respond, but after countess attemps trying to start up from the cd i got a happy face with a ? mark. i have also tried the erasing the hardrive procedure. i burned dariks boot and nuke and pressed c to load it up and gave it the erase all comman and then tried booting up the mac os 9 and i am still unable to boot from it.

---

### Post by spencer on 2006-04-17
Hi,

Don't know if this will work for you but it's worth a shot. Try holding down the option/alt button as soon as you start up your machine with whatever mac disk you are trying to boot from and from the menu select your startup CD. Maybe that will get your cd to boot for you. 

-spencer

---

### Post by kadymae on 2006-04-17
Have you tried zapping your p-ram?  I don't know why, but this usually solves a bunch of problems when Macs just won't do what they're told.

[http://www.cit.cornell.edu/helpdesk/mac/macos/resetpram.html](http://www.cit.cornell.edu/helpdesk/mac/macos/resetpram.html)

---

---

### Post by aimislame15 on 2006-04-17
Insert the CD, restart the computer. Once the startup sound sounds, hold the option key. This will show all bootable media, including external HD's, CD's, and partitions on the internal HD. This should allow you to boot from the CD. If all else fails, zap the PRAM, and it should/will default boot to OSX (the CD).

---

### Post by mrmime00 on 2006-04-17
Thank you guys very much , but i have finally figured out what was the problem , you see the mac os x restore cd is not booting because is completely scratched (thanks to my dear son whom i am groundin for life) does anyone have the restore cd or can give me a image of it so i can burn it and get rid of this predicament.

---

### Post by aimislame15 on 2006-04-17
We have hundreds at my work but I can't snag any, sorry.

---

### Post by mrmime00 on 2006-04-17
No need to snag them just make a image of them and put them on a ftp or something so i can access it.

---

### Post by mrmime00 on 2006-04-26
Well i finally got me a mac os x tiger , pressed c and deleted the linux partitions and reformated the harddrive to hfs . i thank you all for helping and teaching me new things . i think i would probably try ubuntu on my old pc i have collecting dust and leave it to my son since he is just so curious about this  operating system.

---

### Post by diogo.delgaudio on 2006-04-26
test

---

### Post by ottojschlosser on 2006-04-27
[QUOTE=mrmime00]Well i finally got me a mac os x tiger , pressed c and deleted the linux partitions and reformated the harddrive to hfs . i thank you all for helping and teaching me new things . i think i would probably try ubuntu on my old pc i have collecting dust and leave it to my son since he is just so curious about this  operating system.[/QUOTE]

I recommend this course highly. Instead of traumatizing your child and building enormous resentments which can only be aired on Jerry Springer :rolleyes:, give the kid something less precious to play with (and an old PC is about as non-precious as one can imagine). Great way to jump into Linux - that's how I got started. :-k

---

