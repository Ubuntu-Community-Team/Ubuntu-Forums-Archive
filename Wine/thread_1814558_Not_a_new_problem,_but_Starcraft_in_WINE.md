---
title: "Not a new problem, but Starcraft in WINE?"
date: 2011-07-29
forum: Wine
---

### Post by SevenHundred on 2011-07-29
I know this is not a new problem, but I'm trying to run the first Starcraft in Ubuntu 11.04 with WINE. I installed it but when I try to play it tells me that my CD may not be in the drive. The only solutions I've seen to this problem involve using other programs to "crack" it -- I'm not really sure what this means and I don't really want to break the CD, as I use this same CD on other computers to play SC. Is there a better way to get this to work?

---

### Post by sprocket10 on 2011-07-30
I have never used WINE, but I think there's an option to enable CD/DVD communication in WINE which you may not be checking OR the CD is scratched quite badly.

*What I can tell you is the recent patches to SC make it run without the CD, so once you get it to run, patch it, and you won't have to worry about the CD anymore.

*Another alternative that comes to mind: if you attach the game's CD key to a battle.net account, then you can download it anywhere onto any machine.  Of course it's a big download.  I would look up connection settings in WINE allowing it to access the CD/DVD drive.  Unfortunately, I cannot tell you what these options are myself.

---

### Post by disturbedite on 2011-07-30
Just learn to read people. From the Starcraft entry on appdb.winehq.org:

HOWTO: Use StarCraft without the CD.

There is now an official Blizzard patch for StarCraft that allows you to play without the CD. You can find instructions [here]("http://us.blizzard.com/support/article.xml?articleId=21150").

If that does not work, you can still try the old method: 

First, put the CD in! If you've already installed it, great. If not, go do that. Then, do this on the command line: 
dd if=/dev/cdrom of=~/BroodWar.iso 

To mount this image of the CD: 
sudo mkdir /media/iso0 
sudo mount -o loop ~/BroodWar.iso /media/iso0 

Using winecfg, add a new drive that points to /media/iso0, and give it the type CD-ROM. Finally, run StarCraft.exe in your program files and you're done! Whenever you want to mount it again, just do: 
sudo mount -o loop ~/BroodWar.iso /media/iso0 

When you're done and don't feel like keeping it mounted, just do: 
sudo umount /media/iso0 

If you have any issues still with StarCraft complaining about no CD being inserted, make sure the iso mount point you made is configured as a CD-ROM device in winecfg, and make sure you have already mounted it first!

BTW, there is a section for wine-related problems that people apparently keep overlooking. This thread belongs there.

---

