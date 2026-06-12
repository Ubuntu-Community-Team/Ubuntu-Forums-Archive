---
title: "Help Wine Please just read"
date: 2007-10-21
forum: Wine
---

### Post by -gabe-noob- on 2007-10-21
I was playing around with the wine cfg and I set it up for virtual desktop but set the resulition very low. now when I try to edit the winecfg I cannot get to the apply button so I cant do anything on wine now. Please help

---

### Post by -gabe-noob- on 2007-10-21
Help *bump*

---

### Post by -gabe-noob- on 2007-10-21
Any one know anything bout this? *bump*

---

### Post by ElEdwards on 2007-10-21
The only thing that I can think of is for you to temporaily increase your regular screen resolution enough so that all of the **winecfg** window can be seen.  Then you can correct the Wine resolution, apply it,close **winecfg** and then return your regular resolution to the previous setting.

---

### Post by deadlydeathcone on 2007-10-22
Enter the following into a terminal:

```
wine explorer /desktop=desktop,1024x768 winecfg.exe
```

---

### Post by Zylar on 2007-10-22
I've done the same thing before.  I just used Tab and Enter to hit the Ok key.  Took some trial and error.

---

### Post by cogadh on 2007-10-22
You can also manually edit the user.reg file found in your.wine directory to either change the virtual window resolution or remove it completely. Just open the file with a text editor and scroll all the way down to the bottom. You'll see a section that looks something like this:
```
[Software\\Wine\\X11 Driver] 1192840363
"Desktop"="640x480"
"DXGrab"="N"
"Managed"="Y"
```
Either change that 640x480 to something different (I recommend nothing lower than 800x600) or remove the "Desktop" line completely.

---

