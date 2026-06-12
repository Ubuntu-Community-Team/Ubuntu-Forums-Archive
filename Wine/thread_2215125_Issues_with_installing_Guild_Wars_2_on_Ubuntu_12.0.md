---
title: "Issues with installing Guild Wars 2 on Ubuntu 12.04"
date: 2014-04-04
forum: Wine
---

### Post by Daniela-Bianca_And on 2014-04-04
Fellow Ubuntu users that are also into using WINE for some of their games that have yet not received a Linux version, prepare for a "tl;dr"... (Though you will have to read all if you wish to help me.) This has been a true challenge for me and I have officially run out of options... slowly falling into despair. I didn't know what other section of the Forum this would have gone into better than WINE, since it involves trials with installing Guild Wars 2 mainly through it.

Laptop: Lenovo G580
Overview:
Memory 3.7 GiB
Processor Intel® Core&#8482; i5-3210M CPU @ 2.50GHz × 4 
Graphics Intel® Ivybridge Mobile  
OS-type 64-bit
Disk 488.1 GB
(Can provide additional information based upon request.)

My situation went as follows:

I decided that I wanted to install Guild Wars 2 again to play with my boyfriend. The last time I had it installed I used to be a Windows 7 user. But now I am using Ubuntu Linux 12.04. No, I cannot install any other new version. Updating it to 12.10 caused my laptop to fail starting up completely and I had to erase it from BIOS and reinstall 12.04, so it has to stay on this version... I also have no possibility of back-up (hard poor college student life...) and returning to Windows 7 would take me ages and be risky altogether since I would have to (again) do it by myself.

Knowing I could virtually install almost any Windows program or game via WINE, I decided to try that. As stated from the Ubuntu Software Center, my WINE version is 1.4
I proceeded to download the .exe file after logging in at [https://www.guildwars2.com/en/](https://www.guildwars2.com/en/) and then right-clicking it to open it through Wine Windows Program Loader option... It starts the download manager, but surrounded by a black border... and after some seconds, the screen part that it covered went black and stopped at this, while running still... [Here is a screenshot of it]("https://www.dropbox.com/s/eyazat252fq5ltv/Black%20Screen.png"). I cannot verify that it's still running and wasn't able to find reliable data on my Google searches...

However, I stumbled across [this video]("https://www.youtube.com/watch?v=QZQHO7IbvOA") and followed the instructions it said, but without any luck (I also sent a PM to him, but he hasn't responded yet). I have also tried various versions of Wine from the list that PlayOnLinux has while it also performed Wine Mono Installer and Wine Gecko Installer for each before it ran... The result was that 1.5.11 and 1.5.12 display the black download manager issue... And versions that I have tried above that as you can see them [listed here]("https://www.dropbox.com/s/knzzfamhxilu4ht/Wine%20Versions.png"), have resulted in Wine not responding anymore... and no download starting at all...

I thought that maybe it could be an issue with PlayOnLinux... because it tells me to upload it to version 4.2.2. and here its windows look white colored, while on his video they look black... I tried to update it with no success. Could not find any menu option for it and after following or attempting to follow [these instructions]("http://www.playonlinux.com/en/download.html"), I ended up not being able to perform the update to that version... I have no clue why except the possibility that I might have installed the incorrect package wine:i386... I tried installing all the packages I could find from [this link ]("http://packages.ubuntu.com/search?keywords=wine")under that name, all with error except one (which I now can no longer recognize). When I installed it it showed that it finished installing, but then the install button remained there... This is as far as I went till I ran out of ideas, exhausted at 2 in the morning...

Please help...

Kind regards,
Bianca

---

### Post by Kris_Spencer on 2014-04-05
It's been a while since I've played GW2 on Linux...Let's see. Okay, to update your PoL (PlayonLinux), you should add their repo to your system, as the Ubuntu repos do not keep up to date. Here's some code that you'll need to run though terminal:

```

wget -q "http://deb.playonlinux.com/public.gpg" -O- | sudo apt-key add -
sudo wget http://deb.playonlinux.com/playonlinux_precise.list -O /etc/apt/sources.list.d/playonlinux.list
sudo apt-get update
sudo apt-get upgrade playonlinux

```

Note, the above expects that PoL is still installed and will upgrade it for you. Now that we have that taken care of, I believe that I just used the PoL install script for GW2. It'll walk you though installing GW2 in a working condition. It'll grab the wine version you need (I think it's 1.5.x), and it'll grab the older update manager for GW2. That one will keep you up to date, and it works with Wine.

Good luck!

---

### Post by Daniela-Bianca_And on 2014-04-05
> **Kris_Spencer said:**
> It's been a while since I've played GW2 on Linux...Let's see. Okay, to update your PoL (PlayonLinux), you should add their repo to your system, as the Ubuntu repos do not keep up to date. Here's some code that you'll need to run though terminal:

```

wget -q "http://deb.playonlinux.com/public.gpg" -O- | sudo apt-key add -
sudo wget http://deb.playonlinux.com/playonlinux_precise.list -O /etc/apt/sources.list.d/playonlinux.list
sudo apt-get update
sudo apt-get upgrade playonlinux

```

Note, the above expects that PoL is still installed and will upgrade it for you. Now that we have that taken care of, I believe that I just used the PoL install script for GW2. It'll walk you though installing GW2 in a working condition. It'll grab the wine version you need (I think it's 1.5.x), and it'll grab the older update manager for GW2. That one will keep you up to date, and it works with Wine.

Good luck!

What do you mean by adding their "repo" to my system?

After typing: wget -q "http://deb.playonlinux.com/public.gpg" -O- | sudo apt-key add -
it said that I do not have the gpg...

---

### Post by Kris_Spencer on 2014-04-06
A repo (repository) is a list of packages, so to speak. By adding the offical PlayonLinux repo, you can get the most up to date version just by running the Ubuntu system updates. The error may be from making a typo, try copy pasting each line into the terminal. The commands come from the offical website [here]("http://www.playonlinux.com/en/download.html"). If you get an error again, you can always install and update the package manually. Here's a like to the [package itself]("http://www.playonlinux.com/script_files/PlayOnLinux/4.2.2/PlayOnLinux_4.2.2.deb").

---

