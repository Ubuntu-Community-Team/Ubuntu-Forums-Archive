---
title: "Trouble with File Paths in Wine"
date: 2008-10-13
forum: Wine
---

### Post by Dionikon on 2008-10-13
I'm sure this has been posted before, but I seem to be fail at forum searches today.

After recently getting mythbuntu running at home I have now decided to experiment a little with Ubuntu at work.  The theory being, if I can rid myself of Windows my life will be better.

So, what I need to do is install and run 4 applications that I need from day to day that cannot be replaced by open source alternatives.  One of which I am having issues with.  It is called "Interaction Routing Designer", it's for designing call flows for Call Centres.

Any who...

I can open the application itself and look at folders and their contents.  However when I attempt to open a 'strategy', I get an error stating: "Strategy file c:\GCTI\Interaction Routing Designer\importstr\strategy name.rbn is not accessible."

Of course this path is not valid anywhere other than windows.

I have tried putting a correct file path in the "registry", which simply changes the file path in the error message to be something like "/home/user/.wine/GCTI\importstr\strategy name.rbn".  As you can see the application is adding \importstr\strategy name.rbn to the path and is therefore failing.

Anyone have any ideas on how to fix this?

Terminal output here:
```

 wine "c:\GCTI\Interaction Routing Designer\RoutingDesigner.exe"
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
addp-trace off
(addp_xconfig) local OFF, remote OFF, trace off
addp-trace off
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common ECO_AUTOWORDSELECTION not implemented yet!
fixme:richedit:RichEditWndProc_common ECO_AUTOHSCROLL not implemented yet!
fixme:richedit:RichEditWndProc_common ECO_AUTOVSCROLL not implemented yet!
fixme:richedit:RichEditWndProc_common ECO_NOHIDESEL not implemented yet!
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common ECO_AUTOWORDSELECTION not implemented yet!
fixme:richedit:RichEditWndProc_common ECO_AUTOHSCROLL not implemented yet!
fixme:richedit:RichEditWndProc_common ECO_AUTOVSCROLL not implemented yet!
fixme:richedit:RichEditWndProc_common ECO_NOHIDESEL not implemented yet!
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common ECO_AUTOWORDSELECTION not implemented yet!
fixme:richedit:RichEditWndProc_common ECO_AUTOHSCROLL not implemented yet!
fixme:richedit:RichEditWndProc_common ECO_AUTOVSCROLL not implemented yet!
fixme:richedit:RichEditWndProc_common ECO_NOHIDESEL not implemented yet!
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common ECO_AUTOWORDSELECTION not implemented yet!
fixme:richedit:RichEditWndProc_common ECO_AUTOHSCROLL not implemented yet!
fixme:richedit:RichEditWndProc_common ECO_AUTOVSCROLL not implemented yet!
fixme:richedit:RichEditWndProc_common ECO_NOHIDESEL not implemented yet!
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common ECO_AUTOWORDSELECTION not implemented yet!
fixme:richedit:RichEditWndProc_common ECO_AUTOHSCROLL not implemented yet!
fixme:richedit:RichEditWndProc_common ECO_AUTOVSCROLL not implemented yet!
fixme:richedit:RichEditWndProc_common ECO_NOHIDESEL not implemented yet!
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common ECO_AUTOWORDSELECTION not implemented yet!
fixme:richedit:RichEditWndProc_common ECO_AUTOHSCROLL not implemented yet!
fixme:richedit:RichEditWndProc_common ECO_AUTOVSCROLL not implemented yet!
fixme:richedit:RichEditWndProc_common ECO_NOHIDESEL not implemented yet!
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common ECO_AUTOWORDSELECTION not implemented yet!
fixme:richedit:RichEditWndProc_common ECO_AUTOHSCROLL not implemented yet!
fixme:richedit:RichEditWndProc_common ECO_AUTOVSCROLL not implemented yet!
fixme:richedit:RichEditWndProc_common ECO_NOHIDESEL not implemented yet!
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common ECO_AUTOWORDSELECTION not implemented yet!
fixme:richedit:RichEditWndProc_common ECO_AUTOHSCROLL not implemented yet!
fixme:richedit:RichEditWndProc_common ECO_AUTOVSCROLL not implemented yet!
fixme:richedit:RichEditWndProc_common ECO_NOHIDESEL not implemented yet!
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common ECO_AUTOWORDSELECTION not implemented yet!
fixme:richedit:RichEditWndProc_common ECO_AUTOHSCROLL not implemented yet!
fixme:richedit:RichEditWndProc_common ECO_AUTOVSCROLL not implemented yet!
fixme:richedit:RichEditWndProc_common ECO_NOHIDESEL not implemented yet!
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common ECO_AUTOWORDSELECTION not implemented yet!
fixme:richedit:RichEditWndProc_common ECO_AUTOHSCROLL not implemented yet!
fixme:richedit:RichEditWndProc_common ECO_AUTOVSCROLL not implemented yet!
fixme:richedit:RichEditWndProc_common ECO_NOHIDESEL not implemented yet!
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common ECO_AUTOWORDSELECTION not implemented yet!
fixme:richedit:RichEditWndProc_common ECO_AUTOHSCROLL not implemented yet!
fixme:richedit:RichEditWndProc_common ECO_AUTOVSCROLL not implemented yet!
fixme:richedit:RichEditWndProc_common ECO_NOHIDESEL not implemented yet!
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common ECO_AUTOWORDSELECTION not implemented yet!
fixme:richedit:RichEditWndProc_common ECO_AUTOHSCROLL not implemented yet!
fixme:richedit:RichEditWndProc_common ECO_AUTOVSCROLL not implemented yet!
fixme:richedit:RichEditWndProc_common ECO_NOHIDESEL not implemented yet!
fixme:storage:StgCreateDocfile Transacted mode not implemented.
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
addp-trace off
(addp_xconfig) local OFF, remote OFF, trace off
addp-trace off
error: ConnNS.cpp:166 cannot resolve name 'SYDSQLDB03'
error: ConnNS.cpp:166 cannot resolve name 'melsqldb02'
error: ConnNS.cpp:166 cannot resolve name 'MEL3SQLDB01'
fixme:storage:StgCreateDocfile Transacted mode not implemented.
err:ole:CoGetClassObject class {3ff01c3d-6aa6-11d2-9ce4-0060081daaa1} not registered
err:ole:CoGetClassObject no class object {3ff01c3d-6aa6-11d2-9ce4-0060081daaa1} could be created for context 0x1
err:ole:CoGetClassObject class {3ff01c3d-6aa6-11d2-9ce4-0060081daaa1} not registered
err:ole:CoGetClassObject no class object {3ff01c3d-6aa6-11d2-9ce4-0060081daaa1} could be created for context 0x1
err:ole:CoGetClassObject class {3ff01c3d-6aa6-11d2-9ce4-0060081daaa1} not registered
err:ole:CoGetClassObject no class object {3ff01c3d-6aa6-11d2-9ce4-0060081daaa1} could be created for context 0x1
err:ole:CoGetClassObject class {3ff01c3d-6aa6-11d2-9ce4-0060081daaa1} not registered
err:ole:CoGetClassObject no class object {3ff01c3d-6aa6-11d2-9ce4-0060081daaa1} could be created for context 0x1
err:ole:CoGetClassObject class {3ff01c3d-6aa6-11d2-9ce4-0060081daaa1} not registered
err:ole:CoGetClassObject no class object {3ff01c3d-6aa6-11d2-9ce4-0060081daaa1} could be created for context 0x1

```

---

