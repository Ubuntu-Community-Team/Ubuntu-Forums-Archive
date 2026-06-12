---
title: "Help with errors"
date: 2013-11-23
forum: Wine
---

### Post by kevin.pierson on 2013-11-23
I am trying to run a program written in VB6 in Ubuntu 12.04.  When I try to run it from the terminal I get:

fixme:scrrun:filesys_QueryInterface Unsupported interface {7fd52380-4e07-101b-ae2d-08002b2ec713}
fixme:scrrun:filesys_QueryInterface Unsupported interface {37d84f60-42cb-11ce-8135-00aa004bb851}
fixme:olepicture:OleLoadPictureEx (0xc644ec,326,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f498), partially implemented.
fixme:olepicture:OLEPictureImpl_get_hPal unimplemented for type 3. Returning 0 palette.
err:ole:CoGetClassObject class {00000514-0000-0010-8000-00aa006d2ea4} not registered
err:ole:create_server class {00000514-0000-0010-8000-00aa006d2ea4} not registered
err:ole:CoGetClassObject no class object {00000514-0000-0010-8000-00aa006d2ea4} could be created for context 0x5
fixme:olepicture:OLEPictureImpl_Render Not quite correct implementation of rendering icons...


Any ideas on how to get this working????  Until today I had never messed with Linux or Wine so I am pretty lost at this point!!!!

---

### Post by ian-weisser on 2013-11-24
Looks like you are trying to access interfaces that simply don't exist in Wine.
You may get a better answer asking in the Wine forums.

Wine is not a Windows clone or emulator. It's an attempt to reproduce Windows system calls natively in Ubuntu, without access to the Windows source code. 

There are native Linux VB compilers, if that's what you are looking for.

Another option for you is to install a real copy of windows in a Virtual Machine. VMs are very easy to install on Ubuntu hosts.

---

### Post by Mark Phelps on 2013-11-24
Attached is a link to the Wine page for Visual Basic: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=94]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=94")

Notice that the recent versions are rated Garbage -- meaning, they are not going to work no matter what you do.

As ian-weisser mentioned, Wine is not a Windows emulator -- so it will not simply do what Windows does.

---

