---
title: "Run Time '5' Error.  trying to run a program for school"
date: 2011-10-02
forum: Wine
---

### Post by tinkerist on 2011-10-02
so i'm trying to install a windows based program for school and run it in wine.  i've steadily gotten it to go a little further each step of the way, most recently i've installed winetricks and ran vbrun60 to get a .dll file i need.  now it starts to run but i get a Run Time '5' error and then it shuts down when i hit "ok".  when i run from terminal this is the output:

```
$ wine C:\\windows\\system32\\LogicCoach\ 11\\LC11_H11.exe wine
fixme:ole:OaBuildVersion Version value not known yet. Please investigate it !
fixme:ole:OleLoadPictureEx (0xbe0994,63180,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f97c), partially implemented.
fixme:ole:OleLoadPictureEx (0xbe1c54,1086,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f9cc), partially implemented.
fixme:ole:OLEPictureImpl_SaveAsFile (0x182ab0)->(0x18cd08, 0, (nil)), hacked stub.
fixme:ole:OleLoadPictureEx (0xbe31a4,76862,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f584), partially implemented.
fixme:ole:OleLoadPictureEx (0xbe31a4,75371,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f584), partially implemented.
fixme:ole:OleLoadPictureEx (0xbe31a4,0,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=32,y=32,f=0,0x1a6ad0), partially implemented.
fixme:ole:OleLoadPictureEx (0xbe31a4,0,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=32,y=32,f=0,0x1a6c48), partially implemented.
fixme:ole:OleLoadPictureEx (0xbe31a4,0,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=32,y=32,f=0,0x1a6d00), partially implemented.
fixme:ole:OleLoadPictureEx (0xbe31a4,0,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=32,y=32,f=0,0x1a6d98), partially implemented.
fixme:ole:OleLoadPictureEx (0xbe31a4,0,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=32,y=32,f=0,0x1a6e30), partially implemented.
fixme:ole:OleLoadPictureEx (0xbe31a4,0,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=32,y=32,f=0,0x1a6ea8), partially implemented.
fixme:ole:OleLoadPictureEx (0xbe31a4,0,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=32,y=32,f=0,0x1a70f0), partially implemented.
fixme:ole:OleLoadPictureEx (0xbe31a4,0,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=32,y=32,f=0,0x1a7168), partially implemented.
fixme:ole:OleLoadPictureEx (0xbe31a4,0,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=32,y=32,f=0,0x1de888), partially implemented.
fixme:ole:OleLoadPictureEx (0xbe31a4,0,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=32,y=32,f=0,0x1de900), partially implemented.
fixme:ole:OleLoadPictureEx (0xbe31a4,0,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=32,y=32,f=0,0x1de998), partially implemented.
fixme:ole:OleLoadPictureEx (0xbe31a4,0,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=32,y=32,f=0,0x1deaf8), partially implemented.
fixme:ole:OleLoadPictureEx (0xbe31a4,0,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=32,y=32,f=0,0x1deb90), partially implemented.
fixme:ole:OleLoadPictureEx (0xbe31a4,0,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=32,y=32,f=0,0x1dec28), partially implemented.
fixme:ole:OleLoadPictureEx (0xbe31a4,0,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=32,y=32,f=0,0x1ded80), partially implemented.
fixme:ole:OleLoadPictureEx (0xbe31a4,0,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=32,y=32,f=0,0x1deed8), partially implemented.
fixme:ole:OleLoadPictureEx (0xbe31a4,0,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=32,y=32,f=0,0x1def68), partially implemented.
fixme:ole:OleLoadPictureEx (0xbe31a4,0,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=32,y=32,f=0,0x1deff8), partially implemented.
fixme:ole:OleLoadPictureEx (0xbe31a4,0,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=32,y=32,f=0,0x1df088), partially implemented.
fixme:ole:OleLoadPictureEx (0xbe31a4,0,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=32,y=32,f=0,0x1df1e0), partially implemented.
fixme:ole:OLEPictureImpl_SaveAsFile (0x1a0708)->(0x1843e8, 0, (nil)), hacked stub.
fixme:ole:OLEPictureImpl_SaveAsFile (0x1e2970)->(0x184300, 0, (nil)), hacked stub.
err:ole:CoGetClassObject class {0d43fe01-f093-11cf-8940-00a0c9054228} not registered
err:ole:create_server class {0d43fe01-f093-11cf-8940-00a0c9054228} not registered
err:ole:CoGetClassObject no class object {0d43fe01-f093-11cf-8940-00a0c9054228} could be created for context 0x5
fixme:ole:OLEPictureImpl_get_hPal unimplemented for type 3. Returning 0 palette.
fixme:ole:OLEPictureImpl_get_hPal unimplemented for type 3. Returning 0 palette.
fixme:ole:OLEPictureImpl_get_hPal unimplemented for type 3. Returning 0 palette.
fixme:ole:OLEPictureImpl_get_hPal unimplemented for type 3. Returning 0 palette.
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4f92-6699-11cf-b70c-00aa0060d393}

```

---

### Post by tinkerist on 2011-10-06
nothin'?  bummer.

---

