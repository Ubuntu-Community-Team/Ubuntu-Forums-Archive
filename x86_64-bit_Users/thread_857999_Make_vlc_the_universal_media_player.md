---
title: "Make vlc the universal media player"
date: 2008-07-13
forum: x86 64-bit Users
---

### Post by vikrant_me on 2008-07-13
Rather than right-click-ing every filetype out there and specifying the open-with option is there a central location of a easier way to set filetype associations? Dare i say like windows default file type associations option.

---

### Post by akudewan on 2008-07-13
In Nautilus (the default file-manager), you can right-click on a video (or any other file type), go to properties, and choose your preferred app under "Open With"

There is also System > Preferences > Preferred Applications in the menu.

---

### Post by vikrant_me on 2008-07-13
* Suggestion #1 is exactly what i was trying to avoid, manually setting file type associations for each file type out there.

* Suggestion #2 is better but when i set vlc as default for multimedia it didnt set it for mp3 or mp4 :(

---

### Post by no1wantdthisname on 2008-07-13
Open ~/.local/share/applications/mimeapps.list.

```

[Added Associations]
video/x-msvideo=vlc.desktop;
video/x-matroska=vlc.desktop;
application/vnd.rn-realmedia=vlc.desktop;
video/mp4=vlc.desktop;
video/x-ogm+ogg=vlc.desktop;
video/x-ms-wmv=vlc.desktop;
video/mpeg=vlc.desktop;
video/quicktime=vlc.desktop;
video/x-ms-asf=vlc.desktop;

```

That should take care of video files at least.

---

### Post by mhenriday on 2008-07-13
I'd like to make the **VLC Media Player** my default audio player for music files, for the simple reason that after the latest **flashplayer** plugin update, it is the only one that is now working on my 64-bit box with a **Creative Soundblaster X-Fi** card. But when I open > ~/.local/share/applications/mimeapps.listI see the following :
```
[Added Associations]
application/x-flash-video=mplayer.desktop;
audio/x-wav=kde-amarok.desktop;rhythmbox.desktop;
application/msword=ooo-template.desktop;scribus.desktop;kde-kpdf.desktop;kde-k3b.desktop;gedit.desktop;evince.desktop;kde-kwrite.desktop;ooo-writer.desktop;
application/pdf=ooo-writer.desktop;
inode/directory=mplayer.desktop;vlc.desktop;
```

How can I edit the above to make the desired changes ?...

Henri

---

### Post by no1wantdthisname on 2008-07-13
Just add in the lines you don't have and modify the ones you do have to vlc.desktop.

---

