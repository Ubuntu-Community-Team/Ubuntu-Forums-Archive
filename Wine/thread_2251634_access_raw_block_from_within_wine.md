---
title: "access raw block from within wine?"
date: 2014-11-05
forum: Wine
---

### Post by Sandgoose on 2014-11-05
just wondering, I have / shared as drive "z"

is it possible inside wine to open for example /dev/sdc (cdrom) as a raw read only file from inside wine and have wine treat it as a regular file?

I thought it would be transparent and all handled by the filesystem but nothing even shows up in "/dev/" when browsing with a windows file manager even with all files shown

should I give up now or is what I am trying to do possible ?

---

### Post by TheFu on 2014-11-05
The only reasons I can think of for this requirement (which will remain unsaid) can be solved using other methods directly under Linux for about 95% of the situations I've come across.  Basically, use dd/ddrescue to create an image.iso and do whatever you need with that file. In that way you have complete control over the permissions.

Sharing / with WINE is a terrible thing for Linux security - just sayin'.

---

### Post by Sandgoose on 2014-11-05
"The only reasons I can think of for this requirement (which will remain unsaid) can be solved"

I wanted to edit an iso (which I created) by loading it into some old but reliable windows software (not buying a new version) just figured doing it this way would be a time saver but as said couldn't get it to work so ended up using this method just feels a little waste when it is already on the filesystem accessible in this format, just to see if it would work (it did)

thanks

---

