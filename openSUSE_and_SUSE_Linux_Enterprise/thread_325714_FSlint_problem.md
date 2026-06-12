---
title: "FSlint problem"
date: 2006-12-26
forum: openSUSE and SUSE Linux Enterprise
---

### Post by Don_DiZzLe on 2006-12-26
Hello peeps,

Im tryin to compile FSlint 2.18 into a suse specific rpm as stated in the FAQ [http://fslint.googlecode.com/svn/trunk/doc/FAQ](http://fslint.googlecode.com/svn/trunk/doc/FAQ). This is the command I use

[HTML]sudo rpmbuild -ta fslint-2.18.tar.gz[/HTML]

But this is the error I get:

```
+ desktop-file-install --vendor author --dir /var/tmp/fslint-2.18-1.suse-root-root/usr/share/applications --mode 644 fslint.desktop
/var/tmp/rpm-tmp.48703: line 49: desktop-file-install: command not found
error: Bad exit status from /var/tmp/rpm-tmp.48703 (%install)


RPM build errors:
    Bad exit status from /var/tmp/rpm-tmp.48703 (%install)
```

and when running the same command -sudo in super user mode i get:

```
+ desktop-file-install --vendor author --dir /var/tmp/fslint-2.18-1.suse-root-root/usr/share/applications --mode 644 fslint.desktop
/var/tmp/fslint-2.18-1.suse-root-root/usr/share/applications/author-fslint.desktop: error: Categories values must be one of "Core", "Development", "Building", "Debugger", "IDE", "GUIDesigner", "Profiling", "RevisionControl", "Translation", "Office", "Calendar", "ContactManagement", "Database", "Dictionary", "Chart", "Email", "Finance", "FlowChart", "PDA", "ProjectManagement", "Presentation", "Spreadsheet", "WordProcessor", "Graphics", "2DGraphics", "VectorGraphics", "RasterGraphics", "3DGraphics", "Scanning", "OCR", "Photography", "Viewer", "Settings", "DesktopSettings", "HardwareSettings", "PackageManager", "Network", "Dialup", "InstantMessaging", "IRCClient", "FileTransfer", "HamRadio", "News", "P2P", "RemoteAccess", "Telephony", "WebBrowser", "WebDevelopment", "AudioVideo", "Audio", "Midi", "Mixer", "Sequencer", "Tuner", "Video", "TV", "AudioVideoEditing", "Player", "Recorder", "DiscBurning", "Game", "ActionGame", "AdventureGame", "ArcadeGame", "BoardGame", "BlocksGame", "CardGame", "KidsGame", "LogicGame", "RolePlaying", "Simulation", "SportsGame", "StrategyGame", "Education", "Art", "Construction", "Music", "Languages", "Science", "Astronomy", "Biology", "Chemistry", "Geology", "Math", "MedicalSoftware", "Physics", "Teaching", "Amusement", "Applet", "Archiving", "Electronics", "Emulator", "Engineering", "FileManager", "Shell", "ScreenSaver", "TeminalEmulator", "TrayIcon", "System", "Filesystem", "Monitor", "Security", "Utility", "Accessibility", "Calculator", "Clock", "TextEditor", "KDE", "GNOME", "GTK", "Qt", "Motif", "Java", "ConsoleOnly" (found "Application")
desktop-file-install created an invalid desktop file!
error: Bad exit status from /var/tmp/rpm-tmp.8056 (%install)


RPM build errors:
    Bad exit status from /var/tmp/rpm-tmp.8056 (%install)
```


How do I fix this?

---

