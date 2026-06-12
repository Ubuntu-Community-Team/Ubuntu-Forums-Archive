---
title: "Gaah -- new fonts don't appear correct"
date: 2007-03-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by Anaximander Thales on 2007-03-15
First, running XFCE -- so, no nice font manager like KDE and Gnome have.  Nautilus is on here, and I attempted to copy my fonts in under Nautilus (fonts:///).  They did not copy and did not show up under any programs.

So, I looked through several posts on here and finally figured out that once I move my fonts under /usr/share/fonts/truetype/<my folder(s)>, I need to run fc-cache -vf.  Once fc-cache runs through, a reboot and opening Gimp (or OOo) or any other program and the font should appear.  

And it does.  I can see the font in the list, however, when I choose the font, the font that is being used is not what I selected.  I've looked at 40 or 50 of the 854 fonts that I've installed, and they all appear exactly the same (i.e. they all look exactly alike).  

I've attempted this several times.  I created a folder, and copied all the files into it (/usr/share/truetype/personal).  ran fc-cache -f -v and rebooted.  Noticed the problem and thought well, okay, maybe there's just to many fonts in one location.  So, I split them into about 15 different folders.  ran fc-cache again, rebooted, and still have the problem.

So, any suggestions on what I need to do?

---

### Post by kerry_s on 2007-03-15
Just create a hidden folder in your home account named ".fonts" and put the fonts in there. If you put them on the system side(root side) you have to do the whole setup which means you need to make a "fonts.scale" (mkfontscale) and after that you need "fonts.dir"(mkfontdir), you might even need a "fonts.alias"(don't know how).

So if you put it on the user side you don't have to do that. :)

---

### Post by Anaximander Thales on 2007-03-15
Well, I have it going with the .fonts directory -- but I'd much prefer to have the fonts available for all users.  I understand that all I have to do is copy the fonts to the users .fonts directory again, but I'd rather not have to copy 41megs each time when I can have it one location and available to all.

Not much documentation on mkfontscale or mkfontdir.  All though I did see that mkfontscale isn't the best method.  The best method is to use mkfontscale, then manually edit the fonts.scale file for optimum performance.

I wouldn't mind doing the work, but it doesn't seem that there are a lot of documents out there that talk about how to do this.

If anyone can point me to websites where there's some good suggestions, I'd appreciate it.

If not, thanks for the help here.

---

### Post by kerry_s on 2007-03-15
It's fairly easy->

In terminal:
cd /usr/share/fonts/(your folder of fonts) <- you have to be inside the folder with the fonts
sudo mkfontscale <- has to be done first
sudo mkfontdir 
sudo dpkg-reconfigure fontconfig

add the path to xorg.conf

sudo gedit /etc/X11/xorg.conf

```
    FontPath        "/usr/share/fonts/(your folder of fonts)"
```

Now just reboot,to let the system detect the fonts.


Also you do not need to copy the fonts for each user, you can sym link to the fonts in yours.
Example:
ln -s /home/you/.fonts /home/bob/.fonts
ln -s /home/you/.fonts /home/mary/.fonts
etc...
if you need permission, just use sudo.
sudo ln -s /home/you/.fonts /home/bob/.fonts

If it were me i would just create a /home/share that every one can access and put the ".fonts" folder there so others can add fonts if they like.
If i remember correctly you change the owner to users and make sure everyone is in the users group is in there, i think you can also just add a share group and put the users in that group. Do some googling if you want to go that way.

---

### Post by Anaximander Thales on 2007-03-18
Thanks for the information and the alternatives  -- I hadn't thought about it like that.

---

