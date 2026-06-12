---
title: "wine + awn + picasa can't get rid of wine system tray icon"
date: 2008-05-27
forum: Wine
---

### Post by northwestuntu on 2008-05-27
when i open picasa everything works fine, but in my awn bar the wine system tray icon appears and won't close after i close picasa? 

i have to reboot the system to get rid of it?

i have tried right clicking it and closing, but nothing :mad:

---

### Post by Alex Carroll on 2008-05-27
Try using the command:

```
wineserver -k
```

---

### Post by northwestuntu on 2008-05-27
ok that seems to work.  but is this a pisaca bug?  this is gonna be a pain if i have to do this every time.

---

### Post by Alex Carroll on 2008-05-27
I think it's more of a problem with Wine; it's not guaranteed to run everything perfectly.

---

### Post by Kinst on 2008-05-28
[b]Q: What are the known issues/bugs in Picasa for Linux?

    * The system tray does not close with loss of focus. If you bring up the media detector menu, you have to either start picasa or stop the media detector to get the menu to go away.[/b]

[http://picasa.google.com/linux/faq.html](http://picasa.google.com/linux/faq.html)

---

