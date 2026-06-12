---
title: "bundled ati driver not working well with WoW. Proprietary causes different issues."
date: 2011-08-28
forum: Wine
---

### Post by europa on 2011-08-28
So it's about that time for my annual 'i have a problem running wow in ubuntu' post. 

I'm running Ubuntu 11.04 standard install but I have replaced Unity with GNOME-shell.  Everything appears to work just fine without any changes to the video settings. I'm currently utilizing the radeon kernel module that comes packaged.

However, it appears that this driver is unable to correctly display the textures with World of Warcraft.  Here is a screenshot.

[IMG]http://img692.imageshack.us/img692/2036/screenshot9t.png[/IMG]
[click here for un-resized image]("http://img8.imageshack.us/img8/530/screenshot9sh.png")

Switching to the fglrx kernel module appears to fix this issue. Unfortunetly, I'm hitting the below bug with fglrx and gnome3.

Bug 99 - Graphical corruption with gnome-shell
[http://ati.cchtml.com/show_bug.cgi?id=99](http://ati.cchtml.com/show_bug.cgi?id=99)

This makes the machine very unstable, even when not playing video games. It also makes all desktop environment related icons corrupt.

[IMG]http://img690.imageshack.us/img690/1392/342410.png[/IMG]



I guess my real question here is, is anybody aware of a fix for the original issue with the open source radeon driver?  If I could get this up and running, it would be awesome.

Also, if anybody has any tips to avoid the problems I'm hitting in the bug, that'd be great too.

Thanks,

Jack

---

### Post by Dlambert on 2011-08-29
Did you switch wow to open gl rendering?

> Find the file wtf/Config.wtf in your main WoW directory. By default it is found in /home/<username>/.wine/drive_c/Program\ Files/World\ of\ Warcraft/, where <username> is you computer login name.

Open config.wtf using a text editor and add or change the following line:

SET gxApi "opengl"
Note: If config.wtf does not exist, run the game and log into a character, then exit WoW. The game should then have created the file.

---

### Post by Dlambert on 2011-08-29
And did you "additional drivers" your card?

---

### Post by Dlambert on 2011-08-29
> ui corruption edit
if you experience corrupt icons or interface textures, you then you may need to set the uifaster parameter in wtf/config.wtf
use it like this:

Set uifaster "x"
where x equals:
0 – this turns off all ui acceleration
2 – enables partial ui acceleration only.
3 – enables all ui acceleration.
Example:
Set uifaster "2"
the value 2 usually corrects this problem.

try this

---

### Post by europa on 2011-08-29
> **Dlambert said:**
> try this

Hi Dlambert. I appreciate the effort but I have already switched to opengl and even attempted d3d, both experience the same issue. 

The icon corruption I am getting is within GNOME-shell, and not WoW. I'm not sure that adjust my config.wtf file we help with this issue. I will give this a try and let you know if I get any results.

---

### Post by europa on 2011-08-29
no luck. :(

```
$ grep uifaster Config.wtf 
SET uifaster "2"
```

---

### Post by Dlambert on 2011-08-29
Do you still have Gnome classic installed? Try under that?

---

### Post by Dlambert on 2011-08-29
Maybe try PlayOnLinux?

---

### Post by Dlambert on 2011-08-29
> If you experience poor performance, graphical glitches, or the game does not run at all, then add the following options as well:
SET ffxDeath "0"
SET ffxGlow "0"

If you experience a problem with missing character and object models, and/or the login windows background is black, add:
SET M2UseShaders "0"

Here is more ideas.


> 
a. Find this key HKEY_CURRENT_USER\Software\Wine\
b. Highlight the wine folder in the left hand pane by clicking left on it. The icon should change to an open folder
c. Right-click on the wine folder and select [NEW] then [KEY]
d. Replace the text New Key #1 with OpenGL
e. Right-click in the right hand pane and select [NEW] then [String Value]
f. Replace New Value #1 with DisabledExtensions (Notice it's case sensitive!)
g. Then double click anywhere on the line, a dialog box will open.
h. In the value field type GL_ARB_vertex_buffer_object

---

### Post by Dlambert on 2011-08-29
ok, i disabled shaders:
> Code:
SET M2UseShaders "0"
SET Pixelshaders "0"
and the texture distortion is gone!

***_Copied from other site_***

---

### Post by europa on 2011-08-30
Tried all of the above suggestions. Still no improvement. :(

Thanks for your help.

---

### Post by jwaterwo on 2011-08-30
just as a note, i've changed my username.
-europa

---

### Post by Dlambert on 2011-08-30
Manually install the AMD driver

---

### Post by Perfect Storm on 2011-08-31
Moved to Wine Section.

---

