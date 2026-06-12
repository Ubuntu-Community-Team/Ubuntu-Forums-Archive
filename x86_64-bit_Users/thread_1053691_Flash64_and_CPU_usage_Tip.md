---
title: "Flash64 and CPU usage Tip"
date: 2009-01-28
forum: x86 64-bit Users
---

### Post by Yellow Pasque on 2009-01-28
Disclaimer: The following tip is a "dirty" workaround to force Flash to use OpenGL. I've seen some reports of success using this, so I thought I would share it. DO NOT file bug reports if you use it. DO NOT attempt to use this if you run Compiz.

This tip will be particularly interesting to users with Intel graphics or users with ATI cards and open-source drivers that support hardware acceleration/DRI.

Flash can be controlled with an mms.cfg file in /etc/adobe. To create this file in Ubuntu/GNOME :
```
cd /etc
mkdir adobe
cd adobe/
gksudo gedit mms.cfg
```
Now, copy and paste the following.
```
OverrideGPUValidation=true
```
Save the file and quit the editor.

For more detailed info, see:
[http://blogs.adobe.com/penguin.swf/2008/08/secrets_of_the_mmscfg_file_1.html](http://blogs.adobe.com/penguin.swf/2008/08/secrets_of_the_mmscfg_file_1.html)

If this workaround creates problems and you wish to undo it, just delete the file you created:
```
sudo rm /etc/adobe/mms.cfg
```

---

