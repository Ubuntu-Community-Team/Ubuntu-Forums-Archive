---
title: "Making Non-linux text editor the default"
date: 2022-08-30
forum: Wine
---

### Post by LeeU on 2022-08-30
I am running Ubuntu 18.04 with WINE v7.0. I use the NoteTab Pro text editor [[https://appdb.winehq.org/objectManager.php?sClass=version&iId=28805]](https://appdb.winehq.org/objectManager.php?sClass=version&iId=28805]) as a default editor. However, the problem is, I would like to have it listed among the "Open with ..." list and then open the files I select. Is it possible?

(I would also like it to be the system default editor but that's probably not gonna happen, right?)

---

### Post by vanadium on 2022-08-31
If you create a desktop launcher that features an argument placeholder in the command used to launch the application, e.g.  %U, then, in Files, it will be included in the list in the "Properties", "Open With" tab, ready to be set a the default application.

---

### Post by LeeU on 2022-08-31
Okay. I made the desktop file as below but it never shows up on the "Open With" tab

    [Desktop Entry]
    Encoding=UTF-8
    Version=1.0
    Type=Application
    Terminal=false
    Exec=env WINEPREFIX="/home/lee/.wine" wine C:\\\\ProgramData\\\\Microsoft\\\\Windows\\\\Start\\ Menu\\\\Programs\\\\NoteTab\\ 7\\\\NoteTab\\ Pro.lnk %U
    Name=NoteTab Pro

---

### Post by LeeU on 2022-09-06
Anybody?

---

### Post by &amp;KyT$0P# on 2022-09-06
To show up in "Open With" your launcher needs a [FONT=Courier New]MimeType=[/FONT] line listing the relevant MIME type(s) in a semicolon-separated list.  For example here's the one from Vim -
```
MimeType=text/english;text/plain;text/x-makefile;text/x-c++hdr;text/x-c++src;text/x-chdr;text/x-csrc;text/x-java;text/x-moc;text/x-pascal;text/x-tcl;text/x-tex;application/x-shellscript;text/x-c;text/x-c++;
```

To make it the default editor requires setting it in [FONT=Courier New]~/.config/mimeapps.list[/FONT] .  For each MIME type for which you want your editor default, under the [FONT=Courier New][Default Applications][/FONT] header, associate the MIME type to the name of the .desktop file.  As an example associating GVim (gvim.desktop) as default for [FONT=Courier New]text/plain[/FONT] -
```
text/plain=gvim.desktop
```
But this will only apply to your user account, I don't know how to do it system-wide, sorry.

* Also make sure your .desktop file is located inside the folder [FONT=Courier New]~/.local/share/applications/[/FONT]

---

### Post by LeeU on 2022-09-09
Okay. I added the MIME type in the launcher, and moved it to "~/.local/share/applications/". I also set it in the MIME file in the "/.config/" file. 

It does recognize and run the software but it doesn't open the file. Any other suggestions?

---

### Post by &amp;KyT$0P# on 2022-09-09
First maybe double check whether NoteTab Pro wants the file to be specified like a URL (%U) or file path (%F)?

If you start NoteTab Pro and use its own File > Open (or equivalent) to open the file, does the full file path it sees match **exactly** the actual full path?  Or does Wine transform it into a Windows-like path?  (It has been too long since I've played with Wine to remember the answer, sorry)

If path is different, you might need to launch NoteTab Pro via a wrapper script that performs the path transformation before passing the argument to NoteTab Pro.

Failing all that, you might try to run the command in the [FONT=Courier New]Exec=[/FONT] line of your desktop entry in a Terminal, passing it a specific file, to see if it opens that file.  If that doesn't work, the desktop entry won't either and the problem becomes figuring out how to tell NoteTab Pro to open a specific file at the command line.

---

### Post by LeeU on 2022-09-11
I'm trying to figure this out now. I'll get back soon!

---

### Post by LeeU on 2022-09-14
I have found that when using the right-click menu it uses the wrong 'drive'. When installed, WINE 'creates' a 'drive' for the software running on it (e.g., NoteTab Pro). For instance, right now when I right-click and select ""Open with NoteTab Pro", the path used to the program is

    env WINEPREFIX="/home/lee/.wine" wine C:\\\\ProgramData\\\\Microsoft\\\\Windows\\\\Start\\ Menu\\\\Programs\\\\NoteTab\\ 7\\\\NoteTab\\ Pro.lnk

making it look for the document on the "C" 'drive' instead of the "Z" 'drive', e.g.,

"C:\home\lee\Documents\Copyright\FAIR USE NOTICE.txt" not found."

I just need it to change the "C" designation to the "Z" designation. Any ideas?

---

### Post by &amp;KyT$0P# on 2022-09-14
You could try creating a shell script at [FONT=Courier New]~/bin/notetabpro-wrapper.sh[/FONT] with this contents -
```
#!/bin/bash
export WINEPREFIX="/home/lee/.wine"

declare -a z
for f in "$@";do
  z[${#z}]="Z:$(realpath "$f" | sed -r -e 's#/#\\#g')"
done

exec wine C:\\ProgramData\\Microsoft\\Windows\\Start\ Menu\\Programs\\NoteTab\ 7\\NoteTab\ Pro.lnk "${z[@]}"
```

make it executable
```
chmod +x ~/bin/notetabpro-wrapper.sh
```

Then change the [FONT=Courier New]Exec=[/FONT] line in your desktop entry to read
```
Exec=/home/lee/bin/notetabpro-wrapper.sh %F
```

Does it work?

(* Note, the information in this post assumes that NoteTab Pro can open multiple files at once.)

---

### Post by LeeU on 2022-09-14
Unfortunately, it only repeated the error above (looking for the C drive instead of Z).

---

### Post by LeeU on 2022-09-14
I'm not familiar with Regular expressions but someone had given me this before but I couldn't get it to work. It has this at the end

    "z:$(echo $1 | tr '/' '\\')"

something like: 

    Exec=env WINEPREFIX="/home/lee/.wine" wine C:\\\\ProgramData\\\\Microsoft\\\\Windows\\\\Start\\ Menu\\\\Programs\\\\NoteTab\\ 7\\\\NoteTab\\ Pro.lnk "z:$(echo $1 | tr '/' '\\')"

Their idea was kind of like yours. I couldn't get it working though.

---

### Post by &amp;KyT$0P# on 2022-09-14
[FONT=Courier New]$1[/FONT] is shell script language, to use that command you would need to put it in a shell script instead of using it directly in the .desktop file.

---

### Post by LeeU on 2022-09-14
This is the error code I am getting now - in the attachment. It seems all I need now is to change the "C" to a "Z".

---

### Post by LeeU on 2022-09-17
Anybody?

---

