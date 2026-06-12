---
title: "The Sage"
date: 2008-11-14
forum: Wine
---

### Post by cpgos on 2008-11-14
I have recently installed a package called The Sage, this is basically a dictionary and thesaurus, see [www.sequencepublishing.com/thesage.html](www.sequencepublishing.com/thesage.html),
using Wine with Ubuntu 7.10. This package is written for Windows and works correctly when installed in an XP PC. The installation steps in Ubuntu were as follows :

       1. Extract the .zip file that the package downloads in.
       2. Right click TheSage.exe in the extracted folder and select "Open with "Wine Windows Emulator".
       3. A message is displayed saying that the speech API could not be emulated, clicking OK clears this.
       4. The main screen of the application then appears where words are entered for definitions or alternatives.

However, even though the software seems to do some checking it is unable to find any any words at all, even simple words like dog, cat, hedgehog etc.

It seems to me that the file holding the packages database in the
extracted folder is called tsd.hbb, I think this because it's size is 13.3 Mbytes. Is it neccessary to tell Wine something about this file?

Also, a Linux version of The Sage is planned but has not been implemented as yet.

Any suggestions or comments on how this package may be got to operate correctly would be much appreciated.

Best regards,
cpgos

---

### Post by cogadh on 2008-11-14
Try running it from the terminal to see what happens:
```
cd /extracted/Sage/directory
wine TheSage.exe
```
Obviously, change that "cd" path to match where you actually have extracted The Sage.

If it works, then the problem is Wine was not aware of the directory where you have The Sage extracted. To fix that, just copy it into a directory Wine is aware of, like /home/<username>/.wine/drive_c/Program Files.

If it doesn't work, then post the terminal output from Wine. It may contain some error messages that explains what is going on.

---

### Post by cpgos on 2008-11-16
Thank you for your response and my apologies for not responding before now.

The directory containing the extracted files was copied to ~/.wine/drive_c/Program Files and TheSage.exe was then executed using Wine with the results shown below. Also, the attached file shows the user interface that TheSage presents and the response to searching for a word.

Any comments that you may have on how to interpret the error messages below would be appreciated.

Best regards,
cpgos

[email]coastal@coastal-laptop:~/.wine[/email]/drive_c/Program Files$ ls
Common Files  Internet Explorer  TheSage.3.0.16.1718.RC1

[email]coastal@coastal-laptop:~/.wine[/email]/drive_c/Program Files$ cd TheSage.3.0.16.1718.RC1/

[email]coastal@coastal-laptop:~/.wine[/email]/drive_c/Program Files/TheSage.3.0.16.1718.RC1$ ls
fhb.bbh      lkt.hbb     msvcp60.dll             TheSage.exe  tsd.hbb  tsl.hbb
history.txt  mfc42u.dll  phonsearchpatterns.txt  TheSage.ini  tsi.hbb

[email]coastal@coastal-laptop:~/.wine[/email]/drive_c/Program Files/TheSage.3.0.16.1718.RC1$ wine TheSage
err:ole:CoGetClassObject class {96749377-3391-11d2-9ee3-00c04f797396} not registered
err:ole:CoGetClassObject class {96749377-3391-11d2-9ee3-00c04f797396} not registered
err:ole:create_server class {96749377-3391-11d2-9ee3-00c04f797396} not registered
err:ole:CoGetClassObject no class object {96749377-3391-11d2-9ee3-00c04f797396} could be created for context 0x7

[email]coastal@coastal-laptop:~/.wine[/email]/drive_c/Program Files/TheSage.3.0.16.1718.RC1$

---

### Post by dankegel on 2008-11-18
They forgot to include msvcp60.dll.

To fix this, do
  wget [http://kegel.com/wine/winetricks](http://kegel.com/wine/winetricks)
  sh winetricks vcrun6

Then the app starts.  It complains that MS Speech isn't installed, and it complains about some missing fonts, but it does at least put up its UI.

---

### Post by cpgos on 2008-11-18
Thank you for your response.

I have done as you suggest but the problem as described in my previous post remains, this being that the user interface is presented but the software does not seem to be able to access its database, with the result that even simple words are not found.

Is there some way to tell Wine about the file tsd.hbb as this may be where the database is held?

Originally msvcp60.dll as you say was not included, so I manually copied it into the installation directory, as shown in my previous post.

Best regards,
cpgos

---

