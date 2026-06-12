---
title: "SketchUp 2014 and OpenStudio plugin"
date: 2014-11-02
forum: Wine
---

### Post by kuliodpd on 2014-11-02
Hello, I am trying to make the OpenStudio SketchUp Plugin work under Linux (Xubuntu) with Wine. I have installed SketchUp Make 2014 for Windows with Wine (in Xubuntu) and with some tricks found on WineHQ about it I made SketchUp work. After that, I have installed the OpenStudio Suite for Windows, again with Wine, but I can't see any Plugin in SketchUp. In the OpenStudio/Ruby directory (Wine under Linux, again) there is a folder which contains the SketchUp plugin ruby files, which are supposed to work fine in a "pure Windows" OS, but here with Wine the plugin cannot be loaded. In fact I get the error "Error loading OpenStudio SketchUp Plug-in: cannot load such file -- pathname", which in the end derives from the file "Startup.rb" in the last lines:
```
UI.messagebox("Error loading OpenStudio SketchUp Plug-In:\n  #{e.message}", MB_OK)
```
The point is: does anybody get this plugin for SketchUp work with Linux (Wine)?
Thank you!

---

### Post by kuliodpd on 2014-11-02
I have followed a little bit the flow of the code:


1) wine/drive_c/users/Public/Application Data/.../SketchUp/Plugins/OpenStudio/Startup.rb
    require 'OpenStudio/OpenStudio-config.rb'


2) wine/drive_c/users/Public/Application Data/.../SketchUp/Plugins/OpenStudio/OpenStudio-config.rb
    require 'C:\Program Files (x86)\OpenStudio 1.5.0\Ruby\openstudio.rb'


3) C:\Program Files (x86)\OpenStudio 1.5.0\Ruby\openstudio.rb
    at the beginning of this file the following command won't work:
    require "pathname"


I have then went on changing all the relative paths with absolute paths for n-times until the "openssl.so" file (which can't be modified by text editing of course) gives the error: "Verify that ruby can access the OpenSSL libraries".
I think I can't really go on now...

---

