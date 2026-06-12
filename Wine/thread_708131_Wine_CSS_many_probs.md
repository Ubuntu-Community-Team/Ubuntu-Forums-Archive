---
title: "Wine CSS many probs"
date: 2008-02-26
forum: Wine
---

### Post by The_Real_Bacon on 2008-02-26
Sorry to start the thousandth thread on this buuut I'm confused as all heck. I got steam and everything installed correctly, I even waited the huge amount of hours it took to download Counterstrike (campus network that requires authentification every 10 min or so. The DL kept hanging)

It was working. Perfectly. I added a reg key for directx and suddenly *poof* I get crappy fps. I undo that, still crappy. I do everything and anything to try to fix it and nothing. Finally I uninstall steam and everything (a task in itself) and reinstall steam. I borrowed my friend's HL2 disc to try and install. I launched via terminal "wine /media/cdrom0/setup.exe" When I get to the next disc promp it won't come out. I tried every way I could think of..

"wine eject"
Wine says I don't have a cd drive....

I tried unmounting via GUI and It gives the cd drive in use error.

I  have tried installing by moving the counterstrike files from my other partition and steam tells me the game needs updated and starts the update at 7%, which will take a good day to DL...

How am I messing this up? I've done everything posted in any forum I can find. Here, linux-gamers, the winehq site. I know other people with very similar setups who can get this all working fine. Am I an idiot. I am very close to just giving up and gaming on windows. Games are the only reason I even have an XP partition and I'd honestly like to at least mostly quit using it.

I pretty much expect 0 replies, but oh well.

---

### Post by The_Real_Bacon on 2008-02-26
Sooo...I'm gonna try mounting the disc's on a virtual drive. Is it possible to install this way?

edit: @##$@#$@#$@$#$@$#@$@$# AKA, no......trying extracting all the files to one folder and running it from there...


and again nope, I pushed all the files into one folder. I ran setup.exe with  Wine, but it asked for a cd. I'm tired. I can't figure this out. I'm going to bed and I'll probably just redownload via steam, cause it worked once. It just takes roughly 15 hours...

---

### Post by Roryking on 2008-02-26
Sorry about that. Here is what I would do:

1. In order to fix your registry problem, we're going to use a brute-force method. PLEASE NOTE!!! This will also remove any OTHER registry entries you've made, other stuff you've installed under Wine, etc... First, uninstall wine:
```
sudo apt-get remove wine
```

Then, delete your wine settings folder. It is a folder called ".wine" (dot-wine) in your home folder. (Folders and files prefixed with a dot are usually hidden to normal directory listings.) [COLOR="DarkRed"]**This is the part where you will lose all your wine settings, so see below on how to make a backup**[/COLOR]

```
cd ~
rm -rf .wine/
```

To backup your wine stuff, BEFORE running the above code, run:
```
cd ~
cp -rf .wine/ winebackup
```
which will create a visible folder called "winebackup"

2. Now, we need to reinstall Wine.
```
sudo apt-get install wine
```

3. Do the thing to get the Gecko extensions for IExplore, necessary to get Steam working.
```
wine iexplore http://www.winehq.com
```
and say "yes" when it asks to download/install something.

Now, we have to make a choice. Do you want to download the Steam installer and just have it grab what it needs for CS:S? Or do you want to install from CD?

In any case, download the steam installer, go ahead and do so, and save the file in ~/.wine/drive_c/. (That is, in the drive_c folder of your newly re-created .wine folder, in your home directory). Then start it like so:
```
cd ~/.wine/drive_c/
wine start SteamInstaller.msi  [or whatever it is named]

```

If you want to install from CD, what you'll need to do is install the Steam client first (using the method above), and pop in the CD. Do not start anything on the CD; it is not reccommended to run files from locations outside of the above-described drive_c folder. Be sure Steam is exited when you start this process. From here, you can either:

1. Copy the contents of the CD(s) to a subdirectory in your drive_c folder, and run the installer from there. This may ask you for a CD key, which may be a problem as this is your friend's copy. I don't know if there's a way for it to get the key from Steam, so I don't know what happens when you try this.

2. (Reccommended) Try to locate some .gcf files on the CD, and copy those to your .wine/drive_c/Program Files/Steam/Steamapps/ folder. These Game Content Files are what Steam will download. When you next start steam, it will almost certainly need to download a sizeable amount of updates, but the point is to get "the big stuff" (the GCF files) in to that Steamapps directory. Alternatively, you could copy the GCF files from a working Steam installation on another computer.

---

### Post by naz37 on 2008-03-01
To get wine eject to work wine needs to know about your cd drive.

open winecfg and under the drives tab, add the mount point of the game cd/dvd.

---

