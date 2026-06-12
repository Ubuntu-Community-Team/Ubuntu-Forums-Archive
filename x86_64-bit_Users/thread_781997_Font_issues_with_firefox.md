---
title: "Font issues with firefox?"
date: 2008-05-04
forum: x86 64-bit Users
---

### Post by Nubsauce on 2008-05-04
Alright, first let me say I've searched google and this forum and haven't found any answers..

Pretty much, random websites(this forum included) will have fonts scaling way too large.  I can't even read the forums here because of the issue.

I've tried changing the fonts in the preference and tried a few other things to no avail..  Just curious if anyone has had this problem and had a fix for it?  Is this a firefox3 issue?  Is it an issue with fonts in x86-64?  I've never had this problem before and haven't seen it in any of the other x86-64 distributions I've tried the past few days.

Any suggestions or solutions would be welcomed.  :)

Thanks in advance,
Anthony

---

### Post by jazzman65 on 2008-05-04
I just finished installing Hardy 64 bit in a separate partition and for me, the fonts in Firefox were tall, skinny and generally pretty ugly.  What fixed it for me was enabling the Nvidia restricted graphics driver.  Once I did that, the fonts were beautiful.  I know you said your problem was the fonts were too big, but maybe the cure is the same?

Hope that's at least a little bit of help!  :)

---

### Post by halfhaggis on 2008-05-04
In Firefox, try hitting Ctrl+- (i.e. Ctrl key and the minus key). This is the shortcut for reducing the font size.

Similarly, Ctrl++ increases font size.

---

### Post by Nubsauce on 2008-05-04
> **halfhaggis said:**
> In Firefox, try hitting Ctrl+- (i.e. Ctrl key and the minus key). This is the shortcut for reducing the font size.

Similarly, Ctrl++ increases font size.

Well, it's not an issue with the actual font sizes, I've tried changing the sizes and the actual fonts.

It seems like it's a problem with the nv module?  I thought I tried this already but having the flu maybe I didn't?  heh.

Anyways, using the restricted nvidia drivers fixed the problem but...  is there an actual problem with the nv module under x86-64?  :lolflag:

---

### Post by jman82s on 2008-05-08
Hi,

I'm also having this issue, and I am running on an integrated Intel 8252. I'm not entirely sure whether it's a video driver issue...*shrug* I've had this problem with every single distro I've tried since Suse in '05, but the Firefox fonts in Ubuntu have always been great--till now. :( 

Also, I uninstalled and completely eliminated any trace of Firefox on my system--including my home .mozilla directory--, then installed Firefox 2. No dice.

---

### Post by philinux on 2008-05-08
If you've tried this then fine.

System prefs appearance.

choose lcd smoothing. In details choose hinting none or slight.

---

### Post by CyberLeader on 2008-05-08
I think i'm having the same problem, for some reason fonts on some pages seem to be scaling much bigger than they should, and i have to Ctrl- to get it back, even after changing the default size to something smaller... I'm using firefox 3b5 on hardy 64 as well...

---

### Post by dancresswell on 2008-05-09
I don't recall the post I got this from, but it solved my problem.  I'm assuming some fonts appear correct and some are ridiculously big, even on the same page.  It was something do do with the nvidia driver.  Setting the DPI to 96 no matter the resolution should fix it. (I'm using 1920x1200 using the latest nvidia driver available through envy).

Edit the file: /etc/X11/xorg.conf

Add the following lines to the "InputDevice" section.

    Option "useEdidDpi" "FALSE"
    Option "DPI" "96 x 96"

Restart your x server (or reboot).

Hopefully that will help you as it did me, and thank you for whoever wrote that other post that I forgot!  If it doesn't work, you can just undo your change and restart x again.

Cheers.

---

### Post by dcstar on 2008-06-04
> **dancresswell said:**
> 
..........
Add the following lines to the "InputDevice" section.

    Option "useEdidDpi" "FALSE"
    Option "DPI" "96 x 96"
..........

There are tools to put these things in the right place:

```
sudo nvidia-xconfig --no-use-edid-dpi
```

---

### Post by linux4me on 2008-06-04
> **dancresswell said:**
> I don't recall the post I got this from...

I think this is [the original post you're thinking of]("http://ubuntuforums.org/showpost.php?p=4740128&postcount=8").

I also read somewhere that there might be some issues with Cairo in Hardy that contribute to this, but I can't find where I read that... :)

---

