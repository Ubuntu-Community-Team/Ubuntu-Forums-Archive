---
title: "Kdar does evil things in Ubuntu-64 Gnome"
date: 2006-02-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by John Jason Jordan on 2006-02-14
I have been desperately searching for a decent backup utility. Yes, I know there are a gazillion of them for Linux, but they are almost all for huge organizations with thousands of clients over a massive network. In contrast, I have a standalone laptop and I'm th sole user of it. I just wanted something simple to back up to my 60 GB USB pocket drive.

I thought I had found it when someone told me about Kdar. It is listed in Snaptic, so I installed it. I should add that I have previously added a lot of other KDE programs, including Scribus and the whole KOffice suite, in spite of the fact that I prefer my Gnome desktop.

It took a while to get Kdar configured (not overly intuitive), but once I did it is working great. Just the kind of nice, simple backup utility I was looking for. The problem is, it locks up Linux tighter than a drum about one out of four backups. I mean, the only solution is to hit the power button. And once it just suddenly shelled to the command line (like doing Ctrl-Alt-F1) and then came back to the Ubuntu login screen.

I asked on a KDE forum, but no responses. Is anyone here using Kdar under Gnome? Any problems? Does anyone have any idea what might be wrong? A missing KDE file or something?

---

### Post by rplantz on 2006-02-15
[QUOTE=John Jason Jordan]I have been desperately searching for a decent backup utility. Yes, I know there are a gazillion of them for Linux, but they are almost all for huge organizations with thousands of clients over a massive network. In contrast, I have a standalone laptop and I'm th sole user of it. I just wanted something simple to back up to my 60 GB USB pocket drive.
[/QUOTE]

I'm not using Kdar, but I have used simplebackup. I have to confess that I used it only once, but it was a lifesaver. I made a stupid mistake and deleted my entire home directory. Fortunately, simplebackup worked perfectly for the restore.

I have turned my attention to rsync for backups. I've written a shell script for using it with my Mac OSX. It seems to be working, so I'm going to modify the script for my Ubuntu box. They are both desktop machines, which I will backup to a usb external disk.

---

### Post by John Jason Jordan on 2006-02-15
[QUOTE=rplantz]I'm not using Kdar, but I have used simplebackup. I have to confess that I used it only once, but it was a lifesaver. I made a stupid mistake and deleted my entire home directory. Fortunately, simplebackup worked perfectly for the restore.

I have turned my attention to rsync for backups. I've written a shell script for using it with my Mac OSX. It seems to be working, so I'm going to modify the script for my Ubuntu box. They are both desktop machines, which I will backup to a usb external disk.[/QUOTE]
Simple Backup was one of the first things I tried. Unfortunately it does not work. I set it up to make a backup and it appears to do so, except no backup is made. Nothing. Nada. I think the problem is that it is set up only to make backups to its default location and if you try to tell it a different location it probably doesn't work. I ran into other bugs with it also. Not ready for prime time.

As for rsync, a lot of people have suggested that, but I know zero about programming. I'm the dude who turns the light switch on and has no interest in knowing how the light comes on. I looked at web pages about rsync and I couldn't even figure out what the purpose of the program was. Writing a script, or even altering a script supplied by someone else, would take me hundreds of hours of study in order to learn the programming skills. When they assembled my brain I think I got shortchanged in the logic module. :(

I really like Kdar. It's just what I need, albeit a little unintuitive. But I have it configured now, so I'm satisfied. I just need to figure out why it's locking up my computer. I can make a backup and it runs perfectly, then turn around and make exactly the same backup half an hour later, and it will lock up the computer somewhere at random while making the backup. The lockups always happen during the backup, and always at a different point. In other words, it's not a GUI interface problem, and it is not just one file that is triggering it. Since it happens during the backup I'm assuming it has something to do with file copy/write, or perhaps the USB connection. The laptop and the pocket drive are both 60 GB and both are formatted ext3.

I'm just hoping someone has experienced the same problem and knows how to fix it. Even just knowing that it happens to someone else would be useful. At least then I'd know it's not just me.

---

