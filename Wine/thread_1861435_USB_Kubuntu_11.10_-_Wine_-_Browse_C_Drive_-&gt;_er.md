---
title: "USB Kubuntu 11.10 - Wine - Browse C Drive -&gt; error"
date: 2011-10-15
forum: Wine
---

### Post by polarbar on 2011-10-15
Hi O:),

I created a usb Kubuntu 11.10 and I am not able to browse C Drive.  

Error window -> file:///home/ubuntu/Documents/.wine/dosdevices/c: does not exist.

But in fact the folder c: exist.  I can see inside the folder:
/Program Files 
/users
/windows

:confused:


Is this related to Permissions? :???:

---

### Post by christopher.wortman on 2011-10-15
~/drive_c is the folder name, not to mention : is an erogenous tag and cannot be used in file and folder names lol

so file:///home/ubuntu/Documents/.wine/dosdevices/drive_c

---

### Post by Raynman37 on 2012-03-20
I know this is an older thread, but I had this problem today and when you google the problem, this is the first result that comes up, so I hope it's okay to resurrect this thread to post the fix.

Edit this file with your favorite editor as root:

> /usr/share/applications/wine-browsedrive.desktop

Go to the bottom of the file and find where it says:

> Exec=xdg-open *blah blah...*

And change it to:

> Exec=xdg-open $HOME/.wine/drive_c

That will give the menu entry the correct path to your Wine C drive.

---

