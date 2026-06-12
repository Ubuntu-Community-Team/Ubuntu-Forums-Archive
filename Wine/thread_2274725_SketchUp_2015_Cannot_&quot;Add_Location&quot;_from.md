---
title: "SketchUp 2015: Cannot &quot;Add Location&quot; from Google Earth"
date: 2015-04-21
forum: Wine
---

### Post by MetroPietro on 2015-04-21
SketchUp Make 2015 now works well under WINE. However I cannot figure out how to add a Google Earth background into my SketchUp model.
In SketchUp, I go to: File > Geo-Location > Add Location...
This opens an additional, blank dialog box in SketchUp, and then a tab within FireFox (my default browser) that shows Google Earth imagery.
In this browser window I navigate to the area I want to focus on, and then click the "Select" button on the upper right.
This places a mask over everything in the browser window, other than the target area I want to bring into SketchUp.
Then I click the "Grab" button that has appeared on the upper right, and Firefox returns this error message:
> Firefox doesn't know how to open this address, because one of the following protocols (skp) isn't associated with any program or is not allowed in this context.
After Googling for solutions, I tried the following in Terminal:
```
sudo gconftool-2 -t string -s /desktop/gnome/url-handlers/skp/command "/home/pietro/.wine/drive_c/Program Files (x86)/SketchUp/SketchUp 2015/SketchUp.exe"
sudo gconftool-2 -t bool -s /desktop/gnome/url-handlers/skp/needs_terminal false
sudo gconftool-2 -t bool -s /desktop/gnome/url-handlers/skp/enabled true
```
This made no difference. When I try to "Add Location..." in SketchUp, it still sends me to Firefox, and though I can navigate to the desired area, when I try to "Grab" the masked target-area, Firefox returns exactly the same error message.
Ubuntu version: 14.04 LTS
Firefox version: 37.0.1
Wine version: 1.7.34
SketchUp Make 2015 version: 15.3.330 32-bit

---

### Post by anand17 on 2015-06-18
Hi MetroPietro,

Were you able to resolve this?

I'm facing the same issue. Tried with Chrome and Firefox. Only difference is Chrome doesn't throw up the error. The blank window remains as is.
Interestingly, it used to work when I first installed it, the popup (which is now blank) used to be populated with a google map from which I made the selection. Don't know what changed.

CORRECTION: Add Location never worked on linux (through wine). I was working on a mac when I first tried out Add Location (it worked then).

---

