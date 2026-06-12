---
title: "UTAU 0.2.77 + Wine 1.4.1 on Ubuntu Quantal 64-bit"
date: 2012-11-16
forum: Wine
---

### Post by ntzrmtthihu777 on 2012-11-16
Hello UTAU, VOCALOID, and/or Ubuntu Fans!

Making this post for the benefit of others, because I always look here first for ubuntu related issues, and I suppose others do too. 

First, let credit be given where credit is due. One, thank you Ameya for creating [UTAU]("http://en.wikipedia.org/wiki/Utau") in the first place.
Two, thank you [Wine team]("http://www.winehq.org/") for creating Wine to help wean us of windows.
And three, thank you [Catgirl/nekomukuro]("http://utauarianna.altervista.org/") for ending days (yes, days) of googling on how to get UTAU to run properly on wine.

Nekomukuro wrote a [tutorial]("http://utauarianna.altervista.org/tutorials/utau-on-linux-wine-how-to/") on how to use UTAU 0.2.77 on wine, and full credit goes to her as far as ending my search goes. Funny thing is after I got it to work a million pages come out of nowhere answering my question, which is pretty funny to me.

I have created an entire wiki on installing UTAU in Wine [here,](http://utau.wikia.com/wiki/Installing_UTAU_in_Ubuntu_linux_with_Wine) complete with screen-shots. Anyhow, I am posting here to speed the search of other ubuntu using UTAU lovers.

[Step 1] Preparation

You need the following software/packages installed/downloaded on your box:

[utau0277inst.exe]("http://utau-synth.com/download.html") Note: it must be version 0.2.77, no others (as of this writing) work with wine
[utau_a5_35.zip ]("http://ux.getuploader.com/utau_a5/download/35/utau_a5_35.zip")(for an English GUI, "&#12480;&#12454;&#12531;&#12525;&#12540;&#12489;&#8221; means download, disregard if you are fluent in Japanese)
It is assumed that these .exe and .zip files are stored in your ~/Downloads directory for the sake of this tutorial, adjust as necessary.

ja_JP.utf8 locale check with ```
locale -a
``` and install via Language Support if you don't have it (this is an absolute must, even if you are going to use the English GUI patch)

Wine 1.4.1 install with
```
sudo apt-get install playonlinux
```[Step 2.] Initial installation
Open a terminal and run
```
LANG=ja_JP.utf8 wine ~/Downloads/utau0277inst.exe
```This will open the install wizard. It will be in Japanese (a good thing, gibberish or no text at this point is a bad sign). The only thing you need to know is "&#27425;&#12408; (_N_)" is the "Next" button, "&#25147;&#12427; (_B_)" is "Back", and "&#12461;&#12515;&#12531;&#12475;&#12523;" is "Cancel". Just go with the defaults and install to the fake C://Program Files (x86) directory. The install progress bar will immediately fill up and seem to freeze, but you will notice the terminal keeps working. At some point it will repeatedly say "Maximum number of clients reached" again and again, all you can do is wait till it finishes.

[Step2.5] Applying the language patch and creating a link to the UTAU folder
Neither of these actions are strictly necessary, but if you are reading this it is likely you speak and/or prefer English to Japanese, and making the link gives you easy access to the UTAU folder, both in terminal (no need to escape characters) and GUI (no need to reveal hidden files)
To create the link, run
```
ln -s ~/.wine/drive_c/Program\ Files\ \(x86\)/UTAU/ ~/UTAU
```Having done this, applying the language patch is far easier:
```
unzip ~/Downloads/utau_a5_35.zip -d ~/UTAU/
```instead of
```
unzip ~/Downloads/utau_a5_35.zip -d ~/.wine/drive_c/Program\ Files\ \(x86\)/UTAU/
```[Step 3] First run
Execute utau.exe with wine just like we ran the installer:
```
LANG=ja_JP.utf8 wine ~/UTAU/utau.exe
```You will notice in the terminal that many *.wav files with hiragana names are generated, this is a good thing. Had we not ran UTAU in Japanese all these file names would have been gibberish and unusable. UTAU will launch, (with an English GUI if you applied the patch) and Notepad will launch (in Japanese) with readme.txt. Before you do anything else, click Tools > Option and check the boxes for either "No batch file for rendering (not recommended)" or "Use resampler.dll for rendering" and the very last check-box, "front end (old wavetool.exe" (it apparently does not display quite right). You can adjust these settings as you get more experienced in using UTAU, but that is another tutorial for another day.

[Step 4.] Clean-up
At this point you need to convert the text files to Unicode (UTF-16 &#12499;&#12483;&#12464;&#12456;&#12531;&#12487;&#12451;&#12450;&#12531;) (big-endian) by opening them in this Japanese Notepad and saving as (ctrl+shift+s) the same file name but with a Unicode (UTF-16 &#12499;&#12483;&#12464;&#12456;&#12531;&#12487;&#12451;&#12450;&#12531;). The most important are in the ~/UTAU/voices/uta directory, readme.txt, oto.ini, and character.txt. If you do not re-save these you will receive an error message every time you run UTAU, and it is quite annoying, not to mention this allows these text files to be opened in Gedit without displaying gibberish (granted these files are all Japanese, but I think it is better to display an actual language, even if you don't understand it, rather than text-blocks).

[Step 4.5.] Creating a launcher Icon
Again, this step is not strictly needed, but I doubt you want to have to launch UTAU via terminal each time you want to use it (although using terminal gives you a real-time readout of what it is doing, useful if you are developing for it I suppose). You can use any image you want, but for the sake of example I will use one provided in the initial install of UTAU.
[EDIT] I have created an icon from a screen capture, you can download it [here.]("http://i.imgur.com/jxXIU.png")
Create a blank text file and paste the following code into it
```
#!/bin/bash
LANG=ja_JP.utf8 wine ~/UTAU/utau.exe
```and save it as "utau.sh" in the ~/UTAU directory. This scrip will automatically launch UTAU in the proper language.

Create a second blank text file and past the following code into it, substituting your username for "username"
```

[Desktop Entry]
Version=0.2.77
Name=UTAU
Comment=Launches UTAU via wine in Japanese
Exec=/home/username/UTAU/utau.sh
Icon=/home/username/UTAU/voices/uta/image.bmp
Terminal=false
Type=Application
Categories=Utility;Application;
```this time saving as UTAU.desktop. (note: if you know how to do this more streamlined, please post and/or pm me!)

Give both files execute permissions with
```
chmod +x ~/UTAU/utau.sh
chmod +x ~/UTAU/UTAU.desktop

```You will notice UTAU.desktop changes into an icon, drag this to the Unity launcher and you are all done! Enjoy your UTAU!

---

### Post by ntzrmtthihu777 on 2012-11-16
Also, it seems I have neglected to add tags to this thread.
Moderators, I know you can move and/or delete threads, but can you add/remove tags?

If this is possible, can you add the following tags to this thread:
UTAU wine ubuntu install

---

