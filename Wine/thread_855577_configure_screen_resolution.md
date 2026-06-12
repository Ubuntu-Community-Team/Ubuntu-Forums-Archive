---
title: "configure screen resolution"
date: 2008-07-10
forum: Wine
---

### Post by groeswenphil on 2008-07-10
I shouldn't fiddle.
I was trying to get WINE to give me a bigger screen area.
Now it's so big that when I try to configure it I can't get to some of the command areas........to confirm change of resolution under the GRAPHICS tab.

Help!
Phil

---

### Post by Felson on 2008-07-10
use wineconfig instead of winecfg.

---

### Post by groeswenphil on 2008-07-10
It said 'wineconfig' not found

Phil

---

### Post by Felson on 2008-07-10
My apologies. I am using Kbuntu. I didn't realize that it was a KDE thing.
Here is the ugly answer instead....
```

cd ~/.wine/
gedit user.reg

```
go to the very end and change the value of "Desktop" and then save. Be really careful not to change anything else....

---

### Post by groeswenphil on 2008-07-17
Did that. Now when I try Applications >Wine >Configure Wine, I get [this.]("http://flickr.com/photos/groeswenphil/2677692476/")
[IMG]http://flickr.com/photos/groeswenphil/2677692476/[/IMG]




Any ideas?
Phil

---

### Post by Felson on 2008-07-17
You get what? Also, post the line exact line as you changed it from the user.reg file.

---

### Post by groeswenphil on 2008-07-17
[http://flickr.com/photos/groeswenphil/2677692476/](http://flickr.com/photos/groeswenphil/2677692476/)

[Software\\Wine\\X11 Driver] 1215719024
"Desktop"="1280x1024"
"Managed"="N"

Thanks,
Phil

---

### Post by Felson on 2008-07-17
wow... Sometime I should be shot. Uncheck the "Emulate Virtual Desktop" check box, and then hit the enter key on the keyboard. After that you should be able to reload it and change it to what ever resolution you want.

---

