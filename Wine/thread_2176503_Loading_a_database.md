---
title: "Loading a database"
date: 2013-09-24
forum: Wine
---

### Post by warburp on 2013-09-24
I have a database of items for MH3U it is an exe that i can run fine in windows but id like to use in in ubuntu when i try to laod it with wine it tells me to install mono for net 2.0 applications so I installed mono with the following commands

```

sudo apt-get isntall mono-complete
sudo apt-get update

```
and attempt to run the application with
```

mono /media/warburp/Media_Storage/MH3U/MH3U\ Database.exe

```

and receive the following output
```

(mono:10972): GLib-GObject-WARNING **: Attempt to add property GtkSettings::gtk-button-images after class was initialised


(mono:10972): GLib-GObject-WARNING **: Attempt to add property GtkSettings::gtk-can-change-accels after class was initialised


(mono:10972): GLib-GObject-WARNING **: Attempt to add property GtkSettings::gtk-menu-popup-delay after class was initialised


(mono:10972): GLib-GObject-WARNING **: Attempt to add property GtkSettings::gtk-menu-popdown-delay after class was initialised


Unhandled Exception: System.EntryPointNotFoundException: GetPrivateProfileString
  at (wrapper managed-to-native) MH3G_Dex.Engine_IniConfig:GetPrivateProfileString (string,string,string,System.Text.StringBuilder,uint,string)
  at MH3G_Dex.Engine_IniConfig.INIGetStringValue (System.String iniFile, System.String section, System.String key, System.String defaultValue) [0x00000] in <filename unknown>:0 
  at MH3G_Dex.Engine_Language.Initial_Language () [0x00000] in <filename unknown>:0 
  at MH3G_Dex.Program.Main () [0x00000] in <filename unknown>:0 
[ERROR] FATAL UNHANDLED EXCEPTION: System.EntryPointNotFoundException: GetPrivateProfileString
  at (wrapper managed-to-native) MH3G_Dex.Engine_IniConfig:GetPrivateProfileString (string,string,string,System.Text.StringBuilder,uint,string)
  at MH3G_Dex.Engine_IniConfig.INIGetStringValue (System.String iniFile, System.String section, System.String key, System.String defaultValue) [0x00000] in <filename unknown>:0 
  at MH3G_Dex.Engine_Language.Initial_Language () [0x00000] in <filename unknown>:0 
  at MH3G_Dex.Program.Main () [0x00000] in <filename unknown>:0

```

---

### Post by ian-weisser on 2013-09-25
An .exe file is not merely a database. It's an executable that includes how you interact with the database.
And, as you have discovered, that interaction part seems to be Windows only.
Linux has great database support, all kinds of databases...if the file were actually just a database.

You have several options, including:
1) You can file a Wine bug, and help the Wine developers, to add the functionality to Wine.
2) You can run Windows in a VM
3) You can look for some way to extract or copy the database from the .exe, so you bring only the database into Ubuntu.
4) You can use a different database for your purpose. One that's cross-platform compatible.

---

### Post by warburp on 2013-09-25
Thank you ian-weisser for the information i was jsut hoping that there couldve been a way to get it to work ill look into extracted the database from the .exe it would be great if you could help me out with that its an access database if that helps at all

---

### Post by oldfred on 2013-09-25
If it is an older version of Access you may be able to partially get it to work.
 Microsoft Access in Wine - some success
[http://ubuntuforums.org/showthread.php?t=1113065](http://ubuntuforums.org/showthread.php?t=1113065)
[http://wiki.winehq.org/FAQ](http://wiki.winehq.org/FAQ)

But do not expect full functionality. And Access is more than a database. It is also a code generator, query tool, graphics screen creator and report writer. Each of those functions in Linux are usually separate applications each with its own learning curve. The closest is LibreOffice's database which will do most of the same functions.

You should be able to export data and reimport into any of the many SQL data bases Linux supports.

---

### Post by ian-weisser on 2013-09-25
Access databases work with Microsoft Access. Nothing else. Microsoft designed it that way.
You paid for that feature.
 
[oldfred beat me to the rest of it. Well done!]

---

### Post by warburp on 2013-09-25
alright thanks for the info i was just really hoping i would be able to get it open in ubuntu and not have to reboot to windows just for my monster hunter info

---

