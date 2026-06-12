---
title: "MS Word on Wine"
date: 2008-02-22
forum: Wine
---

### Post by TheSeb on 2008-02-22
Does MS Word work well under Wine, what is the most stable/best version of MS Word to use w/ Wine?

---

### Post by agim on 2008-02-23
I don't know about using word on wine, but I can tell you the OpenOffice.org is great, and its compatible with word.

---

### Post by superzorro on 2008-02-23
Well, MS Office 2K works flawlessly with Wine, and using Crossover office I'm able to run office 2003, with 2003 there still are some glitches, for example Visio runs very slowly, but apart from that it runs well.

However I recommend 100% Openoffice.org, it's a great app!!

---

### Post by adam0509 on 2008-02-24
I made word 2003 work on linux, seems to run well...


check [www.playonlinux.com](www.playonlinux.com)

---

### Post by leg on 2008-02-24
What is the point of moving to a Linux distro and then using Wine to use Office?

---

### Post by Cyberponcho on 2008-02-24
Don't get me wrong but, why in the world would someone want to use microsucks word on Linux when you have open office??:confused:

---

### Post by GioF_71 on 2008-02-24
> **Cyberponcho said:**
> Don't get me wrong but, why in the world would someone want to use microsucks word on Linux when you have open office??:confused:

well 4 example to open complex word files that won't be open correctly by OpenOffice (thanks to ms for the closed format).

---

### Post by Whiffle on 2008-02-24
Word, Excel and Powerpoint 2003 work fine for me under Wine-0.9.54

I run word because Openoffice gives me formatting headaches, feels slower, and just doesn't work the way I want it to.   And I get MS Office for free.

I use this script for launching word that I found somewhere on the internet, it helps with compatability with konqueror and such.  I just save it as a file called word, make it executable, and then point konqueror at it whenever it wants to open a doc file.
```

#!/bin/sh
# Launch Microsoft Word either by itself or with the provided file name to open.

# Fully qualifies pathname of the Windows Application to launch
PROGRAM="C:\\Program Files\\Microsoft Office\\OFFICE11\\WINWORD.EXE"

# If launched with no parameters, just run the application and exit.
if [ $# = 0 ]; then
    wine "$PROGRAM"
    exit 0
fi

# Get the file to open and the directory where it resides.
FILE_NAME=`basename "$1"`
DIR_NAME=`dirname "$1"`

# Convert directory from relative to fully qualified path.
if [ `echo $DIR_NAME | cut -c 1` != "/" ]; then
    DIR_NAME=`pwd`/$DIR_NAME
fi

# Change to the directory, run winepath to see if the directory maps to a fake
# windows drive.  WINEPATH_ERRS is 1 if not and 0 if yes.
cd "$DIR_NAME"
winepath "$DIR_NAME" > /tmp/winepath.chk 2>&1
WINEPATH_ERRS=`cat /tmp/winepath.chk | grep "Warning" | wc -l`

# If we cannot edit the file, show error box and terminate.
if [ $WINEPATH_ERRS -gt 0 ]; then
    kdialog --title "WINE/Microsoft Office Error!" --error \
  "ERROR:
  Attempting to open a file using a Windows Application where the file is not in a location accessible b$
  - Move the file ($1) to a valid location.
  - Ensure that ($DIR_NAME) is accessible to WINE.
  Fake Windows drives are configured as softlinks (ln -s) in the directory (~/.wine/dosdevices).  The cu$
    $(ls -l ~/.wine/dosdevices | tr -s " " | cut -d " " -f 9-) "
    exit 1
fi

# Finally run the application.
wine "$PROGRAM" "$FILE_NAME"

```

---

### Post by Cyberponcho on 2008-03-02
I understand the need of some people to run ms word under Linux, my wife is a teacher and she does a lot of text work and yes, she gets upset whenever she has to open a word file with open office and it's not the way she had it before, i myself don't do enough office work to have to use ms word, open office has work flawlessly for me all this time, gee i think i even use abiword more often than any other text application :lolflag:

---

### Post by GioF_71 on 2008-03-03
> **Cyberponcho said:**
> I understand the need of some people to run ms word under Linux, my wife is a teacher and she does a lot of text work and yes, she gets upset whenever she has to open a word file with open office and it's not the way she had it before, i myself don't do enough office work to have to use ms word, open office has work flawlessly for me all this time, gee i think i even use abiword more often than any other text application :lolflag:

Don't get me wrong, I am completely favourable to open formats...

---

### Post by Cyberponcho on 2008-03-03
> **GioF_71 said:**
> Don't get me wrong, I am completely favourable to open formats...

No worries pal, i am as well 100% with open source and Linux is my main OS since years, windows is my 'game slave', and that until i can get to run those old games of mine under wine :)

---

