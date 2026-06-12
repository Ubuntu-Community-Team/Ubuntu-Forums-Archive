---
title: "Amarok 2.1 does not play any local files"
date: 2009-06-06
forum: x86 64-bit Users
---

### Post by SathyaBhat on 2009-06-06
I just installed Amarok 2.1 from the repos, and while it launches (there's a redrawing problem, that's another thing), Amarok doesn't play anything. Once I populate the playlist and hit play, it skips to next song, and then after few songs, it mentions "Too many errors encountered, stopped playback".

last.fm streams work fine. I don't think codecs are the issue, as I have few flac files which don't play, plus the codecs are installed rhythmbox  can play all files fine. 

Any input would be appreciated.

I'm running on Ubuntu Jaunty, x64.

Thanks

---

### Post by ddales on 2009-06-07
I just upgraded Amarok under jaunty 64bit as well.  The only error was by the first start.  It segfaulted.  I started Amarok again, and after that, everything is fine.

Just skipping songs in a playlist sounds like a codec problem.  Re-install your "ubuntu-restricted-extras".  Or kubuntu-restricted-extras under KDE.

---

### Post by SathyaBhat on 2009-06-07
well I reinstalled ubuntu-restricted extras, no luck. launched Amarok in debug mode, I get this message
>  [Playlist::Actions] [WARNING!] Error, can not play this track. 
amarok:                                                                                                           

>  [EngineController] [WARNING!] Phonon failed to play this URL. Error:  "" 
amarok: BEGIN: void EngineSubject::stateChangedNotify(Phonon::State, Phonon::State) 
amarok: BEGIN: virtual void Context::ContextView::engineStateChanged(Phonon::State, Phonon::State) 
amarok:                                                                                                                                    

---

### Post by ddales on 2009-06-07
This is not an Amarok problem per se.  It is a compatibility issue with phonon.  Since I'm not familiar with phonon I can't help you with that.  I use the xine engine without any problems.

---

### Post by SathyaBhat on 2009-06-07
I see, correct me if I'm wrong but isn't Gstreamer the backend for Gnome ? Isn't Amarok supposed to use Gstreamer? 
Anyway I can makek Amarok use Xine ? 
In Sound System configuration dialog box, only Gstreamer is being shown in the back backend tab.

---

### Post by ddales on 2009-06-07
Yes, gstreamer is the default backend for gnome.  Amarok on the other hand is not the default music player for gnome, but rather the default for kde.  

All I can tell you is the phonon error that you received is not an amarok error, it's a phonon error.  

If you don't have xine:
# sudo apt-get install libxine1

You can try it and see if it works for you.A marok with xine, at least on my system, work perfectly together.

---

### Post by SathyaBhat on 2009-06-07
well Xine's already installed. Not sure how to proceed about next. Thanks for the help.

---

### Post by -genin- on 2009-06-07
nah...

i got the amarok error, too...

it didnt play any mp3 file...

i just drag n drop the file to amarok..
but it didnt do anything...

huhuhu..
anyone noe what is the probl..??

---

### Post by crwl on 2009-06-10
Installing libxine1-plugins (which depended on libxine1-ffmpeg) seemed to do the trick for me.

---

### Post by PunkLV on 2009-06-10
Had the same problem. 
```
sudo apt-get install libxine1-plugins
```
worked out great.

---

### Post by Yellow Pasque on 2009-06-10
You can also try installing the gstreamer backend for phonon (phonon-backend-gstreamer) and setting Phonon to use gstreamer with:
```
qtconfig
```

---

### Post by SathyaBhat on 2009-06-11
> **PunkLV said:**
> Had the same problem. 
```
sudo apt-get install libxine1-plugins
```
worked out great.
unfortunately that didn't work for me :(

why is qtconfig bringing out Qt3 config :-s

Plus I can't seem to find a place to make phonon use gstreamer

EDIT: used qtconfig-qt4 to launch, but everything's greyed out and shows not available

EDIT2: got it running by installing 
```
sudo apt-get install phonon-backend-xine
```

Thanks for the help guys!

---

### Post by pmlxuser on 2009-06-17
> **PunkLV said:**
> Had the same problem. 
```
sudo apt-get install libxine1-plugins
```
worked out great.

works!!!! thanks bro..

---

### Post by malrost on 2009-06-21
I had the same problem and configuration

This didn't work for me; I already had the latest version:

```
sudo apt-get install libxine1-plugins
```

This however, did the trick.
```

sudo apt-get install phonon-backend-xine
```

Thanks for the help!

---

### Post by PGHammer on 2009-07-01
> **-genin- said:**
> nah...

i got the amarok error, too...

it didnt play any mp3 file...

i just drag n drop the file to amarok..
but it didnt do anything...

huhuhu..
anyone noe what is the probl..??

If you moved from Amarok  to Amarok 2, you have to reinstall the plugins (including the MP3 plug-ins).  Amarok 2 uses a different plug-in format.

(You will also have to restart Amarok for the plug-in install to take effect.)

All *conflicted-file-format* plug-ins are *not* installed in Amarok by default.  (This is by design, so don't blame the Amarok team for this; I actually get why they did it.)  I already knew I had to do this because the original Amarok required it.

---

### Post by cmltow on 2009-07-04
> **ddales said:**
> I just upgraded Amarok under jaunty 64bit as well.  The only error was by the first start.  It segfaulted.  I started Amarok again, and after that, everything is fine.

Just skipping songs in a playlist sounds like a codec problem.  Re-install your "ubuntu-restricted-extras".  Or kubuntu-restricted-extras under KDE.

Ah yes... restricted extras. Thanks for the reminder.

---

### Post by cybrsaylr on 2009-07-05
> **PunkLV said:**
> Had the same problem. 
```
sudo apt-get install libxine1-plugins
```
worked out great.

Thanks, had the same problem with music files not playing with Amarock version 2.0.2.Put in that plugin and all seems to play fine now.

---

### Post by tetris4 on 2009-07-06
I had the same problem for a long time, here is a post on how I fixed it:

[http://www.mygnulinux.com/?p=129]("http://www.mygnulinux.com/?p=129")

g00d luck :)

---

### Post by Quilzas on 2009-07-09
> **PunkLV said:**
> Had the same problem. 
```
sudo apt-get install libxine1-plugins
```
worked out great.

This solved my problem with Amarok as well!
Thanks!

---

### Post by PunkLV on 2009-08-17
Damn, I've re-orgonized/moved my music, and now amarok does not play, again, damn it. Instead I get this Tooltip upon launching Amarok. Can some one please tell me where did things go wrong?

Edit: And this I get when launching from terminal
```
mak@mak-desktop:~$ amarok &
[1] 26055
mak@mak-desktop:~$ amarok(26056) Phonon::KdePlatformPlugin::createBackend: using backend:  "Xine"
Object::connect: No such slot MainWindow::showStatistics() in /build/buildd/amarok-2.0.2mysql5.1.30/amarok-2.0.2/src/MainWindow.cpp:692
Object::connect:  (receiver name: 'MainWindow')
QLayout: Attempting to add QLayout "" to MainWindow "MainWindow", which already has a layout
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
QWidget::insertAction: Attempt to insert null action
QWidget::insertAction: Attempt to insert null action
QWidget::insertAction: Attempt to insert null action
QWidget::insertAction: Attempt to insert null action
QWidget::insertAction: Attempt to insert null action
QWidget::insertAction: Attempt to insert null action
QWidget::insertAction: Attempt to insert null action
amarok(26056) Plasma::Applet::save: saving to "1"
amarok(26056) Context::ContextView::setContainment: "" Line:  599
amarok(26056) Plasma::ThemePrivate::config: using theme for app "amarok"
amarok(26056) Plasma::Applet::save: saving to "2"
amarok(26056) Plasma::Applet::save: saving to "3"
amarok(26056) Plasma::Applet::save: saving to "4"
amarok(26056) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
amarok(26056) Context::ColumnContainment::insertInGrid: "" Line:  603
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
Object::connect: No such slot FileBrowser::Widget::setDir( const QString& ) in /build/buildd/amarok-2.0.2mysql5.1.30/amarok-2.0.2/src/browsers/filebrowser/FileBrowser.cpp:112
Object::connect:  (sender name:   'KBookmarkHandler')
Object::connect:  (receiver name: 'FileBrowser::Widget')
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0x5200064
amarok(26056) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
amarok(26056) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
amarok(26056) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
amarok(26056) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated

```

Update: Deleted ~/.kde/share/apps/amarok and ~/.kde/share/config/amarok* tooltip still shows at startup, yet amarok plays my music.

---

### Post by n2stc on 2009-08-21
> **PunkLV said:**
> Had the same problem. 
```
sudo apt-get install libxine1-plugins
```
worked out great.

Worked great for me too!  Thanks!

---

### Post by zirtik on 2009-09-17
> **PunkLV said:**
> Had the same problem. 
```
sudo apt-get install libxine1-plugins
```
worked out great.

thanks, this solved my problem as well.

---

### Post by dk21 on 2009-09-17
Same problem... Worked too...

---

### Post by Storm Rider on 2009-09-18
> **PunkLV said:**
> Had the same problem. 
```
sudo apt-get install libxine1-plugins
```
worked out great.

Same here :)

---

### Post by cybrsaylr on 2009-10-30
> **cybrsaylr said:**
> Thanks, had the same problem with music files not playing with Amarock version 2.0.2.Put in that plugin and all seems to play fine now.

> sudo apt-get install libxine1-plugins

Just installed 64 bit Karmic Koala and Amarok wouldn't play any music files.
Put above code in terminal and Amarok plays music files again as it did with Jaunty.

---

### Post by medya on 2009-10-31
I have the same problem I installed all the libraries u mentioned , and still dont get any music :(
EDIT 1: 
sorry I tried again and now it works :)

thanks guys

---

### Post by cybrsaylr on 2009-10-31
When Amarok didn't work I put the code in terminal to correct it, then had to close then restart Amarok and it worked fine. Same thing usually applies to flash and a couple other tweaks that had to be made.

---

### Post by lagunero on 2009-11-02
> **PunkLV said:**
> Had the same problem. 
```
sudo apt-get install libxine1-plugins
```worked out great.

Thank you a lot it works for me =D>

---

