---
title: "ies4linux problem"
date: 2008-02-21
forum: Wine
---

### Post by skunkrecords on 2008-02-21
IDK if i'm missing something obvious but, when I install ies4linux, after the gui install, nothing happens. I requested desktop links, but that never happened either. I think the gui install process finished, but now Im stuck. any help would be appreciated!

---

### Post by jwedeking on 2008-02-22
after you run ./ies4linux do you receive


Xlib: unexpected async reply (sequence 0xf99)!
ui/pygtk/python-gtk.sh: line 6:  8162 Killed                  python "$IES4LINUX"/ui/pygtk/ies4linux-gtk.py

---

### Post by ricoris on 2008-03-29
When I installed IEs4linux I did get this message: > **jwedeking said:**
> 


Xlib: unexpected async reply (sequence 0xf99)!
ui/pygtk/python-gtk.sh: line 6:  8162 Killed                  python "$IES4LINUX"/ui/pygtk/ies4linux-gtk.py

I don't know why this happens but I know that if you choose to install Internet Explorer 5.5 instead of Internet Explorer 6 everything works just fine...Should I report this someplace? Where?

---

### Post by karnerblue on 2008-04-03
I had this problem too - looks like it's a python error. I have python version 2.5.1 (I recall update manager just doing an update within the past week or so too I think?)
Anyone found a way to fix this? I need to do ie6 testing for work asap! =(

---

### Post by brento73 on 2008-04-18
My solution to the issues I had installing ies4linux, and this will sound rediculous, was to just keep running the install script every time it crashed.

I received errors which I think were similar, but every time I ran it I would get further along the install process. Eventually it installed, and I was able to run it, and get the 'Sucess!' page the dev set as the default home page.

However... after that initial run, and that initial success, I haven't been able to get it working again. Now I just get a blank window, and have to kill the app.

*sighs*

---

### Post by siddesu on 2008-05-26
this works for me:

./ies4linux --install-corefonts --no-gui --no-color --beta-install-ie7

./ies4linux --full-help for more option goodness

---

### Post by cboldwyn on 2008-11-29
I was getting all kinds of different errors when running
```
./ies4linux
```

particularly

```

python: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int)((xcb_req) - (dpy->request)) >= 0)' failed. ui/pygtk/python-gtk.sh: line 6: 21841 Aborted python "$IES4LINUX"/ui/pygtk/ies4linuxgtk.py
```

and what finally worked for me was


```
sudo ./ies4linux --install-corefonts --no-gui --no-color --beta-install-ie7
```

---

### Post by balibaa on 2009-04-16
For IE6 I used

```
sudo ./ies4linux --install-corefonts --no-gui --no-color --install-ie6
```

It gave me a red message not to do it as root, so after it finished I changed the ownership of the directory it was put in:

```
sudo chown $myusername -R /home/$myhomedirectory/.ies4linux/ie6
```

:)

---

