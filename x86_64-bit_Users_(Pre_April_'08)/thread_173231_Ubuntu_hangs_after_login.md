---
title: "Ubuntu hangs after login"
date: 2006-05-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by kvaz on 2006-05-10
Greetings,

Am new to ubuntu. I recently got a copy of the "Breezy Badger" and installed it on my system which is an AMD 64 using an Asus motherboard. The installation went on well and was led to the login screen. I logged in at thr login screen; the screen changed but there was no panel. I tried the mouse buttons but still nothing happens. FInally had to reset the system. :( 

Once again I booted the system and at the login screen changed the session to 'failsafe terminal' and logged in. This time I got a terminal, but without the panel, also the terminal was without the border and so was stuck up in the lower rightend corner. I typed in 'gnome-wm&' and got the window-manager working. Next I typed 'gnome-panel&' and got the panel. One important observation was that with any command we get some warning messages on the terminal like
----
Gdk-WARNING **: locale not supported by Xlib
Gdk-WARNING **: Cannot set locale modifiers
----

Could any one of you help me in setting up my ubuntu system so that it boots normally? Thanks for all the help.

Regards,
Kev

---

### Post by louis_nichols on 2006-05-10
a very helpful thing would be if, after such a hang, you were able to post here the contents of the file

/var/log/Xorg.0.log

It's unlikely you would be able to do that from within the same system. perhaps from a liveCd or a windows installation complete with a driver for ext2/ext3. Can you do this?

---

### Post by kvaz on 2006-05-10
Dear Louis_nichols,

Thanks for your interest in the issue am facing with Ubuntu. As am not connected to the internet am unable to send you the   /var/log/Xorg.0.log   as an attachment. However here is the gist of the log and my observations.

The log begins with the header containing the version, build, etc. This is followed by the modules loaded. There are a few warnings in the log, related to 
1. fonts not present
2. ignoring request to load module GLcore
3. mode clock 162Mhz exceeds DDC max 110Mhz, and such messages followed by the info "finally use 60hz for 1280X1024".
4. Open APM failed.

I know the summary above is very inadequate. Kindly let me know if you need any specific information. Thanks again.

Regards,
Kevin.

---

### Post by louis_nichols on 2006-05-10
Your small description helps. I can't say I'm very knowledgeable in this area, but I did a google about it and found [this link]("http://gentoo-wiki.com/HOWTO_Eliminate_warning_%22(WW)_Open_APM_failed_(/dev/apm_bios)_(No_such_file_or_directory)%22") which might help you. Check the upper text on the page and see if the error described there is the one you saw in the logfile.

Please give some details about your hardware; especially what graphic card you have is important in this issue.

---

