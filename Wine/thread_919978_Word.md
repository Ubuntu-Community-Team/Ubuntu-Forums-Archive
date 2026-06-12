---
title: "Word"
date: 2008-09-14
forum: Wine
---

### Post by demonskier on 2008-09-14
I want to use MS word as my default word processor but I don't know how to make it be the application that starts when I click on a wordfile.  Can anyone help me...

---

### Post by pytheas22 on 2008-09-14
If you want to open .doc files with Word by default, first right-click on any .doc file and go to the "Open With" tab, then click the "Add" button.  A new window will open with an option to write a custom command for opening the file.  Click the "browse" button next to the field where you enter the command, then navigate to the location of the Word executable--it will be under a location like /home/username/.wine/drive_c/Program Files/Microsoft Office/<precise location of .exe>

Note that your .wine folder is probably hidden by default when you try to browse to it graphically, so if you can't find it inside your /home directory, right-click and select "show hidden files" and it should appear.

I'll attach a screenshot of how I would set it up on my computer, which has Office 2003 installed in wine.

I know these instructions are convoluted, but let me know if it works for you.

EDIT: my apologies, but this doesn't appear to work 100%.  The above steps will cause Microsoft Word to open whenever you click on a .doc file, but it doesn't open the .doc file that you clicked on; it just opens a blank file instead.  I'll see if I can figure out a way to fix that, although I'm not sure it's going to be possible, because Word probably won't accept command-line arguments like that.

---

### Post by demonskier on 2008-09-14
Yeah I already figured that out
... I was able to open it but it is kinda irritating that it won't open the file

---

