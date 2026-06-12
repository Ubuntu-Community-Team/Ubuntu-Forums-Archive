---
title: "How to change Ubuntu image from applications menu?"
date: 2009-05-11
forum: x86 64-bit Users
---

### Post by Jfedak on 2009-05-11
Hi, I'm trying to find out how to change the ubuntu logo on the applications menu to a custom image. However, I am having some trouble finding where to do this. I have seen a few ways to do this, however I have tried and none of them work.

Any tips?

-edit- 

Found problem, wasn't looking in the right folders. PEBCAK error

---

### Post by Jfedak on 2009-05-11
Wait, I think i might have just been looking into the wrong folders.  :popcorn:

---

### Post by John.Michael.Kane on 2009-05-12
You can try the below method.

```
gconftool-2 --set "/apps/panel/objects/object_0/custom_icon" --type string "Icon Location"
```

Replace Icon Location with the location and name of your "start" menu icon.

Example:
```
gconftool-2 --set "/apps/panel/objects/object_0/custom_icon" --type string "/home/xxxx/Themes/Start Button Icons/Start_Button.png"
```

Then you can run the below in you terminal:
```
killall gnome-panel
```

---

