---
title: "[How-to] Neverwinter Nights Diamond Install (xubuntu 64 bit)"
date: 2008-08-03
forum: x86 64-bit Users
---

### Post by zirrush on 2008-08-03
So, before even attempting to install NWN I browsed around the forums to see if it even ran on 64 bit.  Seen a lot of ppl having trouble with the install and having to delete files and what not.  But, after attempting the install myself it only involved one minor fix.  Basically followed a sticky install guide for linux off the bioware forums and just had to make a slight modification to get the game using 32 bit libraries instead of pointing at the 64 bit ones. So, figured I'd post a quick run down of what worked for me on xubuntu 8.04 64-bit.

First off, the files you're gonna need to download:

**_[COLOR="Blue"]NWN Gold Client (7.2 MB)[/COLOR]_**:
[http://nwdownloads.bioware.com/neverwinternights/linux/gold/nwclientgold.tar.gz]("http://nwdownloads.bioware.com/neverwinternights/linux/gold/nwclientgold.tar.gz")

**_[COLOR="Blue"]NWN HotU Client (37.8 MB)[/COLOR]_**:
[http://nwdownloads.bioware.com/neverwinternights/linux/161/nwclienthotu.tar.gz]("http://nwdownloads.bioware.com/neverwinternights/linux/161/nwclienthotu.tar.gz")
[B][U]
[COLOR="Blue"]NWN Update v1.69 (506 MB)[/COLOR][/U][/B]:
[http://files.bioware.com/neverwinternights/updates/linux/169/English_linuxclient169_xp2.tar.gz]("http://files.bioware.com/neverwinternights/updates/linux/169/English_linuxclient169_xp2.tar.gz")

Now, while you're downloading the files above... lets go ahead and pop NWN Diamond into our box and get a directory setup to install to.  I personally just made a directory in my home being as I'm the only person that will be playing it on my comp.  Once the directory is made, we're gonna go ahead and extract some files from our NWN disc to get this baby running:

```

cd /home/whoever
mkdir ./nwn
cd nwn
unzip /media/cdrom/Data_Shared.zip
unzip /media/cdrom/Data_linux.zip
unzip -o /media/cdrom/data/XP1.zip
unzip -o /media/cdrom/data/XP2.zip

```

Once we've got the 4 zip files above extracted to our nwn folder, its time to move on to our clients we just downloaded. Copy or move nwclientgold.tar.gz and nwclienthotu.tar.gz to your nwn folder and extract both as follows:

```

tar -xzf ./nwclientgold.tar.gz
tar -xzf ./nwclienthotu.tar.gz
```

Now, lets move on to the 1.69 update. This part, bioware says to remove all files in the override directory.  However, I didn't bother with it and its been running just fine.  But, if you want to play it by their books... feel free to. Lets go ahead and extract the update as well as run the fixinstall script once the files have been extracted:

```

rm -f ./override/*   (optional)
tar -xzf ./English_linuxclient169_xp2.tar.gz
./fixinstall

```

Now, the moment of truth.  NWN is installed and updated, so lets see if it runs by executing "nwn" in the terminal from our install directory.  If it runs for you, you're done.  Otherwise, this is where I had to do a quick fix dealing with the 32 bit libraries. Open nwn in your preferred text editor and lets change

```
export LD_LIBRARY_PATH=./lib:./miles:$LD_LIBRARY_PATH
```

to

```
export LD_LIBRARY_PATH=./miles:$LD_LIBRARY_PATH
```

Save the file and try executing it again from the terminal, it should (hopefully) work this time. If not, feel free to reply and I'll try my best to help.  I'm making the assumption the most common probs would be not having a particular set of 32 bit libraries installed from the repositories.  Hopefully this saves some ppl a little bit of time and/or trouble : )~

---

### Post by oldrocker99 on 2008-09-23
I tried three different install-nwn.sh scripts and finally went to BioWare's site and followed the instructions to the letter. One small edit of the nwn file (I made a copy of the original line and pasted it in the line following, then edited that copied line. Comment out whichever one doesn't work, and you can get back to the other one quickly if need be) and I was up and running. No movies :(, but everything else is just as delightful as it was 'way back in '02. 

Neverwinter Nights Diamond is, imho, the best commercial game available for Linux, and it is definitely the most gaming goodness you can get for $20. You can literally get years of enjoyment (all for free download) from this gaming masterpiece.

A big thumb's up to BioWare who had a Linux version that would take a purchased copy's serial numbers and run without a disk in the drive. 

Gaming does live on Linux!

:guitar:

---

