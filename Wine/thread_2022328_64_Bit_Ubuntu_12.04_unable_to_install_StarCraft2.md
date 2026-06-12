---
title: "64 Bit Ubuntu 12.04 unable to install StarCraft2"
date: 2012-07-10
forum: Wine
---

### Post by stevemav on 2012-07-10
Attempting to install SC2 with Wine and PlayOnLinux, however no matter what attempt I make to install it on a virtual drive etc it comes up with a box saying "No installer data found, please contact Blizzard Customer Support"

None of the tutorials or other searches I've done have made any headway, I've tried to search/figure it out on my own for three days so I thought that would be enough time to ask a direct question.

I had Wine 1.4 preinstalled, attempted to install the second to latest Wine with the same result. 
As mentioned in the title, I've got a 64bit Ubuntu 12.04 LTS OS.

---

### Post by oldos2er on 2012-07-11
Moved to Wine.

---

### Post by stevemav on 2012-07-13
I've still got no idea how to proceed with this, I've managed to go almost the whole way through installing the game, but it still says there is no install file.

---

### Post by stevemav on 2012-07-15
I've tried things such as right clicking the install .exe file and saying open with wine, tried a number of commands to unhide items on the CD, both with no effect.

---

### Post by ergo-proxy on 2012-07-16
Did you mount it with unhide options?
mount -o ro,unhide,uid=1000 /dev/cdrom /mnt/cdrom
 
If ita fails tru to copy all files on a hard risk, if everything faiils try to download the client.

---

### Post by stevemav on 2012-07-16
> **ergo-proxy said:**
> Did you mount it with unhide options?
mount -o ro,unhide,uid=1000 /dev/cdrom /mnt/cdrom
 
If ita fails tru to copy all files on a hard risk, if everything faiils try to download the client.

It says this:


mount: mount point /mnt/cdrom does not exist

---

### Post by ergo-proxy on 2012-07-16
Then try:
 
sudo mount -o remount,unhide /dev/sr0

---

### Post by stevemav on 2012-07-17
> **ergo-proxy said:**
> Then try:
 
sudo mount -o remount,unhide /dev/sr0

Great, it loads almost all the time now! No sound, but I'll try and work that out for now as well. I've added the mmdevapi exception to in an attempt to get sound working, no luck so far.

---

### Post by stevemav on 2012-07-19
Ok so I've been entering 

 echo 0|sudo tee /proc/sys/kernel/yama/ptrace_scope

every time I want to play SC2, however the options I've found for restoring sound are all several years old. 

Any ideas for how to get sound working on win 1.4, ubuntu 12.04?

Using an AMD APU

---

### Post by vladdy on 2012-07-19
Try the wine 1.5 ppa if you care about sound, wine decided to reject all my improvements so I'm keeping them in the ppa instead. :-)

---

### Post by stevemav on 2012-07-20
> **vladdy said:**
> Try the wine 1.5 ppa if you care about sound, wine decided to reject all my improvements so I'm keeping them in the ppa instead. :-)

I gave that a try, however nothing has changed.

---

### Post by vladdy on 2012-07-22
What exception to mmdevapi? What if you just remove it..

---

### Post by stevemav on 2012-07-23
@vladdy

Sorry if that doesn't notify you, I'm unsure if markup works in here. 

I tried to use wine out of the box, and it didn't work. Then I added mmdevapi and disabled it, following instructions I saw on tutorials. Neither has improved the sound. I'm currently using wine 1.5.9

Just to update, I was on the winehq IRC channel, and the member there pointed out that I don't have a driver listed in the Audio settings- there should be a file called winealsa.drv but I have none. 

Looking at my wine regedit

and there were a number of folders missing- under HKEY_CURRENT_USER>Software>Wine all I have listed are AppDefaults, Debug, Dlloverrides, FileOpenAssociations, Fonts, MenuFiles, MSHTML, and Temporary System parameters

I used this link they provided me to see that I'm missing a lot of things. Not really wanting to edit it myself until I've spoken to someone about it more though.

[http://wiki.winehq.org/UsefulRegistryKeys](http://wiki.winehq.org/UsefulRegistryKeys)

Advice wanted! :)

---

### Post by vladdy on 2012-07-24
Remove the mmdevapi override, it is now harmful to keep it.

---

### Post by stevemav on 2012-07-25
Ok, done- why is that?

---

