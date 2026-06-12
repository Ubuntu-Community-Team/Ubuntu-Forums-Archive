---
title: "iTunes stuck in my laptop"
date: 2014-12-06
forum: Wine
---

### Post by IL TRIVELLA on 2014-12-06
Hi everyone,

Long time ago, due the fact that previously I was owning a MacBook, I tried to install iTunes on my laptop using Wine, then I removed it because it never worked at all, at least I thought so, but when I right click on a song and I go on "open with" iTunes is still there in the available options, and if I press it, nothing happen, I see the sign that I have to wait instead than my mouse pointer, and then nothing happen, it's very annoying to have it still on my laptop, can someone help me to remove it once for all please?

Thanks.

---

### Post by Toz on 2014-12-06
>  then I removed it because it never worked at all
How exactly did you remove it?

To remove the association that causes it to show the "open with iTunes" option, edit the file ~/.local/share/applications/mimeapps.list and remove all references to iTunes.

---

### Post by howefield on 2014-12-06
Thread moved to the *"Wine"* forum.

---

### Post by IL TRIVELLA on 2014-12-07
> **Toz said:**
> How exactly did you remove it?

To remove the association that causes it to show the "open with iTunes" option, edit the file ~/.local/share/applications/mimeapps.list and remove all references to iTunes.

sorry I'm not a very expert of Ubuntu, how I exactly do that what you told me to do? and I can't remember how I removed it...

---

### Post by Toz on 2014-12-07
Open a terminal window and type in the following commands:

1. First, lets go to the directory that contains the file we are looking for:
```
cd $HOME/.local/share/applications
```

2. Then lets backup the file just in case:
```
cp mimeapps.list mimeapps.list.BAK
```

3. Now lets open the file in a graphical editor:
```
gedit mimeapps.list
```

4. Look for any lines that contain the word iTunes and delete the whole line.

5. Save the file.

---

### Post by IL TRIVELLA on 2014-12-07
> **Toz said:**
> Open a terminal window and type in the following commands:

1. First, lets go to the directory that contains the file we are looking for:
```
cd $HOME/.local/share/applications
```

2. Then lets backup the file just in case:
```
cp mimeapps.list mimeapps.list.BAK
```

3. Now lets open the file in a graphical editor:
```
gedit mimeapps.list
```

4. Look for any lines that contain the word iTunes and delete the whole line.

5. Save the file.

I did what you told me to, and on terminal I got that:

```
alessandro@SuperAlex:~$ cd $HOME/.local/share/applicationsalessandro@SuperAlex:~/.local/share/applications$ cp mimeapps.list mimeapps.list.BAK
alessandro@SuperAlex:~/.local/share/applications$ gedit mimeapps.list

```

And instead on the gedit list I got this, but I can't find anything with iTunes... 

```
[Default Applications]video/mp4=vlc.desktop
video/x-msvideo=vlc.desktop
audio/mpeg=vlc.desktop
video/x-matroska=vlc.desktop
audio/x-aiff=vlc.desktop
audio/flac=rhythmbox.desktop
x-scheme-handler/mailto=thunderbird.desktop
message/rfc822=thunderbird.desktop
application/x-extension-eml=thunderbird.desktop
audio/x-vorbis+ogg=vlc.desktop
audio/x-matroska=vlc.desktop
audio/webm=vlc.desktop
audio/x-mp3=vlc.desktop
audio/x-mpeg=vlc.desktop
audio/x-wav=vlc.desktop
audio/x-mpegurl=vlc.desktop
audio/x-scpls=vlc.desktop
audio/x-m4a=vlc.desktop
audio/x-ms-asf=vlc.desktop
audio/x-ms-asx=vlc.desktop
audio/x-ms-wax=vlc.desktop
audio/x-real-audio=vlc.desktop
audio/x-pn-realaudio=vlc.desktop
audio/x-flac=vlc.desktop
audio/vnd.rn-realaudio=vlc.desktop
audio/x-pn-aiff=vlc.desktop
audio/x-pn-au=vlc.desktop
audio/x-pn-wav=vlc.desktop
audio/x-pn-windows-acm=vlc.desktop
audio/x-pn-realaudio-plugin=vlc.desktop
audio/mp4=vlc.desktop
audio/amr=vlc.desktop
audio/amr-wb=vlc.desktop
video/x-ogm+ogg=vlc.desktop
video/dv=vlc.desktop
video/mpeg=vlc.desktop
video/x-mpeg=vlc.desktop
video/msvideo=vlc.desktop
video/quicktime=vlc.desktop
video/x-anim=vlc.desktop
video/x-avi=vlc.desktop
video/x-ms-asf=vlc.desktop
video/x-ms-wmv=vlc.desktop
video/x-nsv=vlc.desktop
video/x-flc=vlc.desktop
video/x-fli=vlc.desktop
video/x-flv=vlc.desktop
video/vnd.rn-realvideo=vlc.desktop
video/mp4v-es=vlc.desktop
video/mp2t=vlc.desktop
video/webm=vlc.desktop
text/html=google-chrome.desktop
x-scheme-handler/http=google-chrome.desktop
x-scheme-handler/https=google-chrome.desktop
x-scheme-handler/about=google-chrome.desktop
x-scheme-handler/unknown=google-chrome.desktop


[Added Associations]
audio/x-aiff=vlc.desktop;
audio/flac=vlc.desktop;rhythmbox.desktop;
x-scheme-handler/mailto=thunderbird.desktop;
message/rfc822=thunderbird.desktop;
application/x-extension-eml=thunderbird.desktop;
image/png=gimp.desktop;
image/jpeg=inkscape.desktop;
audio/x-matroska=vlc.desktop;
audio/webm=vlc.desktop;
audio/x-mp3=vlc.desktop;
audio/x-mpeg=vlc.desktop;
audio/x-wav=vlc.desktop;
audio/x-mpegurl=vlc.desktop;
audio/x-scpls=vlc.desktop;
audio/x-m4a=vlc.desktop;
audio/x-ms-asf=vlc.desktop;
audio/x-ms-asx=vlc.desktop;
audio/x-ms-wax=vlc.desktop;
audio/x-real-audio=vlc.desktop;
audio/x-pn-realaudio=vlc.desktop;
audio/x-flac=vlc.desktop;
audio/vnd.rn-realaudio=vlc.desktop;
audio/x-pn-aiff=vlc.desktop;
audio/x-pn-au=vlc.desktop;
audio/x-pn-wav=vlc.desktop;
audio/x-pn-windows-acm=vlc.desktop;
audio/x-pn-realaudio-plugin=vlc.desktop;
audio/mp4=vlc.desktop;
audio/amr=vlc.desktop;
audio/amr-wb=vlc.desktop;
video/dv=vlc.desktop;
video/mpeg=vlc.desktop;
video/x-mpeg=vlc.desktop;
video/msvideo=vlc.desktop;
video/quicktime=vlc.desktop;
video/x-anim=vlc.desktop;
video/x-avi=vlc.desktop;
video/x-ms-asf=vlc.desktop;
video/x-ms-wmv=vlc.desktop;
video/x-nsv=vlc.desktop;
video/x-flc=vlc.desktop;
video/x-fli=vlc.desktop;
video/x-flv=vlc.desktop;
video/vnd.rn-realvideo=vlc.desktop;
video/mp4v-es=vlc.desktop;
video/mp2t=vlc.desktop;
video/webm=vlc.desktop;
application/x-subrip=vlc.desktop;
application/octet-stream=google-chrome.desktop;
audio/aac=vlc.desktop;
application/zip=file-roller.desktop;
application/vnd.openxmlformats-officedocument.wordprocessingml.document=evince.desktop;
```

---

### Post by Toz on 2014-12-07
Hmmm. Can you try the same with the **mimeinfo.cache** file? Perhaps its in there.

---

### Post by mc4man on 2014-12-07
I haven't had wine installed for quite some time but as I remember it can create a number of .desktop files somewhere that could cause this.
Maybe in ~/.local/share/applications or somewhere nearby..

---

### Post by IL TRIVELLA on 2014-12-07
> **Toz said:**
> Hmmm. Can you try the same with the **mimeinfo.cache** file? Perhaps its in there.

I gave the comand:

```
gedit mimeinfo.cache
```

And what I obtained it was an empty file...

> **mc4man said:**
> I haven't had wine installed for quite some time but as I remember it can create a number of .desktop files somewhere that could cause this.
Maybe in ~/.local/share/applications or somewhere nearby..

How I exactly do that?

---

### Post by Toz on 2014-12-08
> **mc4man said:**
> I haven't had wine installed for quite some time but as I remember it can create a number of .desktop files somewhere that could cause this.
Maybe in ~/.local/share/applications or somewhere nearby..

I was under the impression that all associations were saved in the these files. On my test system, the itunes association was listed here.

@IL TRIVELLA, can you try searching for itunes.desktop files? Try this:
```
sudo updatedb
locate -i itunes | grep -i desktop

```

---

### Post by IL TRIVELLA on 2014-12-08
> **Toz said:**
> I was under the impression that all associations were saved in the these files. On my test system, the itunes association was listed here.

@IL TRIVELLA, can you try searching for itunes.desktop files? Try this:
```
sudo updatedb
locate -i itunes | grep -i desktop

```

```
alessandro@SuperAlex:~$ sudo updatedbalessandro@SuperAlex:~$ locate -i itunes | grep -i desktop
/home/alessandro/.local/share/applications/wine/Programs/About iTunes.desktop
/home/alessandro/.local/share/applications/wine/Programs/iTunes/About iTunes.desktop
/home/alessandro/.local/share/applications/wine/Programs/iTunes/iTunes.desktop
/home/alessandro/.local/share/desktop-directories/wine-Programs-iTunes.directory
alessandro@SuperAlex:~$ 
```

---

### Post by IL TRIVELLA on 2014-12-10
So what I should do now?

---

### Post by Toz on 2014-12-12
Delete those files and see if that removes the option.

---

