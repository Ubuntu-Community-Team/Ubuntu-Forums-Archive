---
title: "font super-small after updates? wtf"
date: 2006-08-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by Anything Generic on 2006-08-04
I'm using Xubuntu 6.06, XFCE.
I let update manager run a sleugh of updates last night, and I recall them being gnome/theme related.  I know I'm not using Gnome, but I'm new to linux, and figured they were required and let them proceed.

Upon reboot, my fonts for Windows, icons on desktop, programs, etc.. were all so small.  It's unbearable!

I've mucked around in the User Interface panel, Window Manager Settings and increased font sizes to 10 (default is 9 which was fine for me before) and the fonts seem to be back to normal for desktop icons, the top of windows, and the "Application" button.

However, programs such as Skype, Conky, XChat, Firefox, etc.. are all still messed up.  Firefox fonts are huge. Skype, Conky, Xchat, etc. are so small they're almost illegible.

I manually set the font in XChat to 10, and this helped.  But how on earth do I fix all of this globally/universally?

I've been satisfied with Xubuntu thus far, but this problem is really really urking me.  I tried getting help on IRC #xubuntu & #ubuntu, but with no cigar.  

Is this a bug?  Seriously, what is going on?  One should be able to do updates without fear of font-size changes...

I would appreciate any responses given.  Thanks!

---

### Post by Kilz on 2006-08-04
> **eric.ws.anderson said:**
> I'm using Xubuntu 6.06, XFCE.
I let update manager run a sleugh of updates last night, and I recall them being gnome/theme related.  I know I'm not using Gnome, but I'm new to linux, and figured they were required and let them proceed.

Upon reboot, my fonts for Windows, icons on desktop, programs, etc.. were all so small.  It's unbearable!

I've mucked around in the User Interface panel, Window Manager Settings and increased font sizes to 10 (default is 9 which was fine for me before) and the fonts seem to be back to normal for desktop icons, the top of windows, and the "Application" button.

However, programs such as Skype, Conky, XChat, Firefox, etc.. are all still messed up.  Firefox fonts are huge. Skype, Conky, Xchat, etc. are so small they're almost illegible.

I manually set the font in XChat to 10, and this helped.  But how on earth do I fix all of this globally/universally?

I've been satisfied with Xubuntu thus far, but this problem is really really urking me.  I tried getting help on IRC #xubuntu & #ubuntu, but with no cigar.  

Is this a bug?  Seriously, what is going on?  One should be able to do updates without fear of font-size changes...

I would appreciate any responses given.  Thanks!

It sounds to me like the screen resolution was changed. Not the font size. Font wont effect icon size. Put the font back and adjust the screen resolution.

---

### Post by Anything Generic on 2006-08-04
Thanks for the response!

The icon sizes haven't changed, but the font-sizes for the names of icons.  The resolution is still at 1280*1024 and hasn't changed.

However Firefox appears generally larger, and so does Openoffice..

hrmm.  any other suggestions?

---

### Post by Adrian_b on 2006-08-04
I think your DPI got messed with..
Try issueing this in a terminal:
echo "Xft.dpi: 96"  | xrdb -merge

---

### Post by Anything Generic on 2006-08-06
Adrian, great suggestion!  That works!!!  Buuut, as soon as I log-out or reboot, it's gone again.  Where can I save that setting permanently?

---

### Post by jimmygoon on 2006-08-06
You can adjust the DPI under System -> Preferences -> Font -> (Advanced Tab/Button maybe)

---

### Post by Anything Generic on 2006-08-06
I don't have that option... this is XFCE.

---

### Post by Anything Generic on 2006-08-06
sudo pico ~/.config/xfce4/Xft.xrdb

thanks everyone, here's what I had to edit ^

---

### Post by dank1176 on 2006-11-20
sudo pico ~/.config/xfce4/Xft.xrdb

thanks everyone, here's what I had to edit ^



heyguys, im having this same problem.
would you be able to give me a walk-through on what you edited in that config, im still learning my way around xubuntu/linux. any help would be appreciated.

---

### Post by Anything Generic on 2006-11-20
dank1176,

I haven't used Xubuntu since Edgy destroyed my RAID volume, thus I don't have that configuration file anymore.  If you'd paste the contents of the file though, I'll try to jog my memory?

---

### Post by godfree2 on 2007-02-15
does anyone have a fix for this yet?
I run a nVidia card have read elsewhere it could be the culprit.
my session res is 1024x768 which is not the default 1600
I've tried xfce fonts of many families and sizes and yet my terminal, skype (I guess all GTK1 apps)
have a very small font.
Have not been able to find where the GTK font size is stored

edgy about edgy

---

### Post by father time on 2007-03-02
dank1176,

Go ahead and run pico by issuing the following command from a terminal:

```
sudo pico ~/.config/xfce4/Xft.xrdb
```

Enter your password if there is a prompt.  Next we need to add the line that Adrian_b specified.  You should move all the way to the bottom and if it is not specified, add the following:

```
Xft.dpi: 96
```

Hit Ctrl + O and then hit Enter.  The file will be saved with the new changes.  Then you need to restart or logout for the changes to be read back in again.

I am using Xubuntu 6.10 Edgy on a cheap laptop (Presario 2100) and I had the same problem these guys had.

Hope this helps you if you have not already fixed the problem.

~Father Time~

---

### Post by grumpymole on 2007-03-02
This is a common Xubuntu experience.  See [here for more details.]("http://grumpymole.blogspot.com/2006/12/xubuntu-more-on-fixing-fonts-problems.html")

Regards

---

