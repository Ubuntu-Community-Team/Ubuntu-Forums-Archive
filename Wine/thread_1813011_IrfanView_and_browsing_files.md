---
title: "IrfanView and browsing files"
date: 2011-07-27
forum: Wine
---

### Post by stephenhau on 2011-07-27
Hi all,

I've managed to set up IrfanView in Wine, and have also set up file association according to [this]("https://help.ubuntu.com/community/Wine#Creating%20file%20associations").

When running in Windows, I can press the arrow keys in IrfanView to step through media files in the same directory.
Does anyone have any advice on how to make that same feature work in Ubuntu/Wine?

Set up:
IrfanView 4.28
Wine 1.3.25
Winetricks
Ubuntu 10.10

Stephen.

---

### Post by TransitMan on 2011-07-27
> **stephenhau said:**
> Hi all,

I've managed to set up IrfanView in Wine, and have also set up file association according to [this]("https://help.ubuntu.com/community/Wine#Creating%20file%20associations").

When running in Windows, I can press the arrow keys in IrfanView to step through media files in the same directory.
Does anyone have any advice on how to make that same feature work in Ubuntu/Wine?

Set up:
IrfanView 4.28
Wine 1.3.25
Winetricks
Ubuntu 10.10

Stephen.

I have IrfanView installed on my machine via WINE but I have not set file associations like you pointed out.
I have no problem using IrfanView browsing my media files.
Also, I am using an older version of IrfanView, 3.60 as the newer one just bork themselves in WINE. You might want to consider dropping down to 3.60 and see if that helps.

---

### Post by stephenhau on 2011-07-28
Hmm, that's a good point there.

So, if I drag and drop an image to IrfanView, I can browse through the directory using the arrow keys.
BUT, if I open an image using the file-association script, I can't browse the directory – it shows file 0/0.

Anyone have any idea how I can make it work through file-association?

---

### Post by TransitMan on 2011-07-28
> **stephenhau said:**
> Hmm, that's a good point there.

1. So, if I drag and drop an image to IrfanView, I can browse through the directory using the arrow keys.
2. BUT, if I open an image using the file-association script, I can't browse the directory – it shows file 0/0.

3. Anyone have any idea how I can make it work through file-association?

1. Yes
2. Correct
3. Why are you making this more complicated than it needs to be?

---

### Post by stephenhau on 2011-07-31
> **TransitMan said:**
> 
3. Why are you making this more complicated than it needs to be?

Curiosity and learning, that's all.

---

### Post by John-B on 2011-07-31
stephenhau, I am using IrfanView 4.20 and with wine 1.2 the arrows work fine for selecting the next or previous file.  
In wine configuration do you have the drive where the files are listed as a windows drive letter under the drive tab? If not, add one with the partition with your photos on and it should work...

---

### Post by stephenhau on 2011-08-01
> **John-B said:**
> …
In wine configuration do you have the drive where the files are listed as a windows drive letter under the drive tab? If not, add one with the partition with your photos on and it should work...

Awesome, that fixed it! Thanks so much :)

---

### Post by frncz on 2011-08-01
I can't figure out how to install irfanview from Wine.
I open iview430_setup.exe with wine after changing permissions, but nothing happens.
On the other hand, Xnview seems to do a lot of what irfanview does, and runs fine in Natty.
I just had to extract Xnview and open xnview.sh

Mike

---

### Post by stephenhau on 2011-08-02
> **frncz said:**
> I can't figure out how to install irfanview from Wine.
I open iview430_setup.exe with wine after changing permissions, but nothing happens.
On the other hand, Xnview seems to do a lot of what irfanview does, and runs fine in Natty.
I just had to extract Xnview and open xnview.sh

Mike

IrfanView needs a certain DLL file. Install WineTricks, then in WineTricks, go to 
> Install an app
> IrfanView
It will then get the DLL, and automatically download and install IrfanView for you.

---

