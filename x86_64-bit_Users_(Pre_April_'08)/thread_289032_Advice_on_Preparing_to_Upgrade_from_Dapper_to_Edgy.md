---
title: "Advice on Preparing to Upgrade from Dapper to Edgy"
date: 2006-10-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by bper on 2006-10-30
Hi,

I'm a Dapper 64bit user getting prepared to upgrade to Edgy 64bit.

The first thing that I want to do is to clone my disks. From the Windows world, I used Norton Ghost. 

Is g4u the way to go to back up my drives or would you recommend something else?

Next, I plan to upgrade using dist upgrade. 

Are there any advantages to using the CD method over this one?

Has anyone done the upgrade, and can you tell me of your experience? Pro or Con, Yea or Nay, Happy or Unhappy?

Thanks.

---

### Post by fabertawe on 2006-10-30
I use Acronis True Image to clone, running from a CD.

I upgraded from Dapper from a CD. It went extremely smoothly apart from an error from MythTV due to mySQL being stopped during the upgrade. I was very impressed how smoothly it all went really. Not everyone's upgrade went smoothly it would seem but I only have good things to say about it!

EDIT: [upgrade info]("https://help.ubuntu.com/community/EdgyUpgrades").

Paul

---

### Post by kuja on 2006-10-30
I think partimage can do a full partition backup for you.
A lot of people have been having trouble with "upgrading". Unless you're prepared to deal with any problems that may crop up, you should do a clean install.

---

### Post by fabertawe on 2006-10-31
Well if your upgrade does have problems you could always do a fresh install then ;) 

Paul

---

### Post by markmark on 2006-10-31
My impression is that a lot of the people who had problems upgrading had either a) non-repo software installed or non-official repos in their sources.list, particularly related to xgl and compiz, which caused conflicts with the new stuff being installed or b) when asked whether they wanted to overwrite an existing config file with the new one from the package they overwrote, hence screwing up things like their xorg.conf.

An example: I had installed a .deb that had libdbus-1-2 as a dependancy. But edgy wants to uninstall that and install libdbus-1-3. I didn't have any trouble sorting that out, but others just go "stupid Ubuntu can't upgrade" not realising that it is non-standard stuff they have done. Same with people compiling the nvidia drivers from scratch while following a guide, but not realising that their X will break with every kernel upgrade.

---

### Post by kuja on 2006-10-31
No, that's not true with all the cases. If I remember right, even python gave trouble during the upgrade, and it's installed by default.

---

### Post by rplantz on 2006-10-31
1. Don't do an upgrade until you can find some time when you can live without your computer for a while and deal with any possible upgrading problems.
2. Back up all your data onto another disk, CD, DVD, etc.
3. Partition your disk with /home in a separate partition. Perhaps you have already done this. If not, you will need to do a fresh install. This makes it easier to do future upgrades. You should still back up your data in case something goes wrong, but the installer should allow you to do a fresh install without changing /home if it's in a separate partition.

Oh, I like Edgy, amd64 version, very much.

---

