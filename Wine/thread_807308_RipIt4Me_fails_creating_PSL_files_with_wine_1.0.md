---
title: "RipIt4Me fails creating PSL files with wine 1.0"
date: 2008-05-25
forum: Wine
---

### Post by anjilslaire on 2008-05-25
Has anybody else noticed any problems with RipIt4Me since upgrading to Hardy and/or wine 1.0?

I just noticed that it fails while trying to create the PSL files for the dvd, with 
```

Failed to load the IFOs!!! 
```

Then ```
There does not seem to be a dvd in your selected drive
```

There's a work around posted on th wine AppDb with bug 9864, but its not working for me. Note that on GUtsy, and older versions of wine, it ran flawlessly. Even installing and older version if wine doesn't solve this.

Any thoughts?

---

### Post by mc4man on 2008-05-26
I didn't ck. out the db so I hope this isn't repeat
First go to /home/username/.wine/drive_c/windows/profiles/username/Application Data/RipIt4Me and in the .ini change the AutoImportPSL=1 to 0
Then somewhere accessible create a folder named OriginalIFOs (exactly)
Open ripit and in settings ck. include  Video_TS
Open ripit in wizard mode run until create psl comes up
Go to home/username/.wine/drive_c/windows/temp/TempIFOs and copy everything but the ripit4me file and paste into the OriginalIFOs folder you created
Paste that folder into the VIDEO_TS folder in your working dir. (typically drive_c -> movie name. 
Now click create psl - should do it
Go to next step and when dvdd opens -> file -> psl list -> import and browse to it (in your video_ts) and import
just tested hardy, wine 1.0rc

Edit : just checked db - same method though i just did the above, nothing with finalifos ect.  Are you naming OriginalIFOs exactly as shown and are you having ripit create the video_ts?

---

### Post by anjilslaire on 2008-05-26
Yup, I include ripit creating the video_ts folder, but the wine db doesn't mention pasting the OriginalIFOs folder into the VIDEO_TS folder. I'll need to try that.

In th meanwhile, DVDFab HD Decrypter (freeware) still works flawlessly under the latest wine...

---

