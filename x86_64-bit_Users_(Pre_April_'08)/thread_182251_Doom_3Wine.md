---
title: "Doom 3/Wine"
date: 2006-05-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by StimpE on 2006-05-25
im totally new to linux and at a lan i saw a guy (with a fresh install of 5.1) pop in doom 3 and the installer loaded. i downloaded the same thing (5.1) and pop in doom 3 and nothing happens cept for the icon on the desktop and the directory of the cd opens too. im also having trouble setting up wine. i do what the site says, it downloads, but does not install and i cant find where it downloads to either. plz help cant go much longer without doom 3...

---

### Post by kingmonkey on 2006-05-25
You dont need wine to run doom3.

[ftp://ftp.idsoftware.com/idstuff/doom3/linux](ftp://ftp.idsoftware.com/idstuff/doom3/linux)

[http://zerowing.idsoftware.com/linux/doom/](http://zerowing.idsoftware.com/linux/doom/)

---

### Post by StimpE on 2006-05-25
i know. those links helped a bit but not completely so i went on google and found some instructions:

Installing Doom 3 and Resurrection of Evil was easy, but then again, it really should be easy installing native applications.

To install it do this:

Fetch doom3-linux-1.1.1286-demo.x86.run or get the file from their bittorrent tracker: [http://zerowing.idsoftware.com:6969/](http://zerowing.idsoftware.com:6969/). Getting the file from the tracker is way faster than using their ftp server so if you know what a torrent file is I would recommend that.

Make the installer file executable and execute it. It can be installed as root in /usr/local/games/doom3 or as a regular user in /home/username/doom3. Both works just fine.

After the installer completes you need to get some files of your legally purchased Doom 3 CD/DVD. To be specific you need to copy the following files into installdir/doom3/base directory:

pak000.pk4
pak001.pk4
pak002.pk4
pak003.pk4
pak004.pk4

When these files have been copied you are ready to run Doom3 with the command:

/home/username/doom3/doom3 

now i just need to figure out how to make the file executable...looking on the ubuntu site but if someone knows how...

---

### Post by kingmonkey on 2006-05-26
> now i just need to figure out how to make the file executable...looking on the ubuntu site but if someone knows how...

chmod 755 yourfilenamehere

---

